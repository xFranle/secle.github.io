+++
title = "Bittensor's Silent Accounting Flaw: How a No-Op Function Has Been Inflating Token Supply Since dTAO Launch"
date = 2026-03-12
draft = false
author = "Franle"
tags = ["bittensor", "blockchain", "security", "defi", "audit"]
+++

---

## Index

1. [Background: The dTAO Emission Model](#background-the-dtao-emission-model)
2. [The Bug: burn_subnet_alpha as a Silent No-Op](#the-bug-burn_subnet_alpha-as-a-silent-no-op)
3. [Why Most Subnets Are Affected by Default](#why-most-subnets-are-affected-by-default)
4. [How the Emission Cycle Exposes the Flaw](#how-the-emission-cycle-exposes-the-flaw)
5. [On-Chain Evidence of Accounting Drift](#on-chain-evidence-of-accounting-drift)
6. [Impact on Price Formation and AMM Integrity](#impact-on-price-formation-and-amm-integrity)
7. [Severity Assessment](#severity-assessment)
8. [Current Status: Open Issue, Closed PR, No Fix Deployed](#current-status-open-issue-closed-pr-no-fix-deployed)
9. [Conclusion](#conclusion)
10. [Disclaimer](#disclaimer)

---

## Background: The dTAO Emission Model

Bittensor's Dynamic TAO (dTAO) upgrade introduced a significant shift in how value flows through the network. Under this model, each subnet operates with its own token — Alpha — and subnet owners are given a configuration choice for how their share of emissions is handled: they can either **recycle** tokens back into the AMM liquidity pool, or **burn** them to reduce circulating supply.

This configuration is stored in a parameter called `RecycleOrBurn`. The burn option was designed to be deflationary — a mechanism for subnet owners to reduce their token supply intentionally, creating scarcity.

What was not designed, however, is a function that actually does the burning.

---

## The Bug: burn_subnet_alpha as a Silent No-Op

Located in `pallets/subtensor/src/staking/helpers.rs` at line 416, the function `burn_subnet_alpha` is defined as follows:

```rust
pub fn burn_subnet_alpha(_netuid: NetUid, _amount: AlphaCurrency) {
    // Do nothing;
    // TODO: record burned alpha in a tracker
}
```

This is a complete no-op. The function accepts two parameters — a subnet identifier and an amount of Alpha to destroy — but the body performs zero state mutations. Nothing is decremented. No supply counter is updated. No tokens are destroyed.

The underscore prefix on `_netuid` and `_amount` is a Rust convention that explicitly signals to the compiler that these arguments are intentionally unused. Combined with the `// TODO` comment, this confirms the function was left as a placeholder that was never completed — and was shipped to production anyway.

For contrast, the `recycle_subnet_alpha` function on the same codebase works correctly. It performs actual state changes, returning Alpha to the AMM pool by updating `SubnetAlphaIn` and adjusting pool reserves. The burn path has no equivalent implementation. The asymmetry is the root of the bug.

---

## Why Most Subnets Are Affected by Default

The problem compounds because of how Substrate handles storage defaults. The `RecycleOrBurn` parameter uses the `ValueQuery` pattern, which means that if a subnet owner never explicitly sets this value, the system returns the default — and the default is `Burn`:

```rust
pub fn DefaultRecycleOrBurn<T: Config>() -> RecycleOrBurnEnum {
    RecycleOrBurnEnum::Burn // default to burn
}
```

Most subnet owners have never explicitly configured this parameter. That means most subnets are operating under `Burn` mode by default — which routes directly to the no-op function every epoch.

In practical terms: the majority of the 70+ active subnets on the network are continuously triggering a burn that never happens.

---

## How the Emission Cycle Exposes the Flaw

Inside `run_coinbase.rs`, the function `distribute_dividends_and_incentives` runs every epoch. When the recipient hotkey belongs to a subnet owner (an immune key), the following logic executes:

```rust
if owner_hotkeys.contains(&hotkey) {
    match RecycleOrBurn::<T>::try_get(netuid) {
        Ok(RecycleOrBurnEnum::Recycle) => {
            Self::recycle_subnet_alpha(netuid, incentive);
        }
        Ok(RecycleOrBurnEnum::Burn) | Err(_) => {
            Self::burn_subnet_alpha(netuid, incentive); // does nothing
        }
    }
    continue; // skips crediting the hotkey
}
```

The `continue` statement correctly prevents the Alpha from being credited to the owner's account. But `burn_subnet_alpha` does not remove the Alpha from supply tracking. The result is tokens that:

- Were emitted by the coinbase mechanism (counted in `SubnetAlphaOut`)
- Were not assigned to any account
- Were not destroyed from the supply
- Exist as a permanent discrepancy between actual user-owned Alpha and the protocol's supply counters

Every epoch. Every affected subnet. Continuously since dTAO launch.

---

## On-Chain Evidence of Accounting Drift

In December 2025, Opentensor contributor `bdmason` opened Issue [#2274](https://github.com/opentensor/subtensor/issues/2274), titled *"Total issuance and burn accounting are broken"*, providing on-chain evidence of the accounting drift at block **6,874,108**:

| Subnet | Negative Drift (Equivalent Units) |
|--------|----------------------------------|
| Root (0) | **-561,931** |
| Subnet 17 | -5,409 |
| Subnet 32 | -3,529 |
| Subnet 55 | -2,585 |
| Subnet 53 | -312 |
| Subnet 20 | -216 |

The drift on the Root subnet alone exceeds half a million units in TAO equivalent. This issue remains **open as of March 2026**.

The fundamental protocol invariant — that the sum of all user balances for a subnet must equal the recorded emitted supply — is continuously violated.

---

## Impact on Price Formation and AMM Integrity

The Alpha token price in dTAO is determined by an AMM based on pool reserves. Those reserves are derived from accounting variables that include `SubnetAlphaOut`. When `SubnetAlphaOut` diverges from the true circulating supply, the AMM computes incorrect prices.

When the protocol records tokens as burned (implying reduced supply and higher unit value) but the burn never executes, prices reflect a scarcity that does not exist in the actual ledger state. This creates several downstream risks:

**Staking and unstaking on distorted prices.** Every participant entering or exiting a subnet operates on price data that does not reflect the real supply. Users may be buying Alpha at a price inflated by phantom scarcity.

**TotalIssuance corruption.** The global token counter accumulates tokens the protocol considers burned but that still weigh on the accounting books. Any analysis of the network's real inflation rate or circulating supply is unreliable.

**Consensus weight distortion.** Bittensor's Yuma Consensus mechanism relies on stake-weighted voting. If the accounting of Alpha balances in affected subnets is distorted, the relative influence of validators in the Root network may be skewed — undermining the resistance to collusion that the protocol is designed to provide.

---

## Severity Assessment

**Severity: HIGH**

Three factors elevate the severity:

1. **Persistence.** The bug has been active since dTAO launch and remains unresolved as of March 2026, despite being formally identified in December 2025.

2. **Scope.** It affects the majority of active subnets due to the default configuration behavior.

3. **Remediation complexity.** A fix is not just a matter of implementing the function body. It requires a storage migration to reconcile months of accumulated drift across 70+ subnets — a high-risk operation with potential for consensus disruption if not handled carefully.

---

## Current Status: Open Issue, Closed PR, No Fix Deployed

**Issue #2274** — opened December 10, 2025 by `bdmason` — remains open.

**PR #2297** — an attempted fix opened December 16, 2025 — was closed without being merged on December 31, 2025. Reviewer `bdmason` noted during the review: the root cause is almost certainly in `run_coinbase.rs`, pointing to the exact location identified here.

**PR #2329** — a newer attempt by the same author (`Dairus01`) — is currently open and targets the same issue. It implements changes to make `burn_subnet_alpha` actually decrement `SubnetAlphaOut` using `saturating_sub`. As of March 2026, it is awaiting review and has not been merged or deployed.

No fix is live on the network. The accounting drift continues to accumulate with every block.

---

## Conclusion

`burn_subnet_alpha` is a function that was never finished. It was deployed to production as a placeholder, it became the default behavior for the majority of subnets in the network, and it has been silently corrupting Bittensor's supply accounting since dTAO launched.

The Opentensor team is aware. A fix attempt was made and rolled back. A second attempt is pending. The issue remains open.

For anyone operating in the Bittensor ecosystem — whether staking, running a subnet, or building on top of the protocol — this is worth tracking. The integrity of price signals, stake weights, and supply metrics all depend on this being resolved correctly.

Monitor Issue #2274 and PR #2329 for updates.

---

## Disclaimer

This post is based on publicly available code in the [opentensor/subtensor](https://github.com/opentensor/subtensor) repository and the referenced GitHub issues and pull requests. All technical findings are derived from on-chain data and public developer discussions. This is not financial advice. The intent is purely informational and oriented toward protocol transparency.
