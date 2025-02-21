+++
title = 'Bybit y el mayor hackeo de la historia cripto: así rompió Lazarus la seguridad multisig con ingeniería social'
date = 2025-02-21
draft = false
author = 'Franle'
tags = ['crypto', 'bybit', 'hackeo', 'lazarus', 'ETH', 'Criptomonedas']
+++

---

## Índice

1. [Contexto y Antecedentes](#contexto-y-antecedentes)
2. [Perfil del Atacante: El Grupo Lazarus](#perfil-del-atacante-el-grupo-lazarus)
3. [Anatomía del Ataque](#anatomía-del-ataque)
   - [Línea de Tiempo del Incidente](#línea-de-tiempo-del-incidente)
   - [Desglose Técnico del Ataque](#desglose-técnico-del-ataque)
4. [Respuesta de Bybit y Manejo de la Crisis](#respuesta-de-bybit-y-manejo-de-la-crisis)
   - [Magnitud del Daño](#magnitud-del-daño)
   - [Gestión de Retiros y Transparencia](#gestión-de-retiros-y-transparencia)
   - [Estrategia de Comunicación](#estrategia-de-comunicación)
5. [Implicaciones para la Industria Cripto](#implicaciones-para-la-industria-cripto)
6. [Conclusiones y Perspectivas](#conclusiones-y-perspectivas)
7. [Advertencia](#advertencia)

---
![Billetera](https://pbs.twimg.com/media/GkVNpQJWMAEcINl?format=jpg&name=medium)

## 1. Contexto y Antecedentes

Bybit, uno de los exchanges más importantes del mundo, fue víctima de un ciberataque sin precedentes que resultó en la sustracción de **más de 1.46 mil millones de dólares** en ETH y stETH desde su billetera fría. Este incidente, que supera a hackeos tan conocidos como el de Ronin Bridge (~600M) o el ataque al puente de Harmony (~100M), redefine los estándares de seguridad en el ecosistema cripto.

El ataque no se basó en una falla de los contratos inteligentes, sino que explotó la **manipulación de la interfaz de usuario** (UI) y la vulnerabilidad humana. Esto demuestra que, pese a contar con sólidas medidas criptográficas y configuraciones multisig, la “cadena humana” sigue siendo el eslabón más débil.

![Lazarus](https://tecnetone.com/hubfs/Grupo%20de%20Hackers%20Lazarus%20Amenazas%20Cibern%C3%A9ticas%20Norcoreanas.png)

---

## 2. Perfil del Atacante: El Grupo Lazarus

El **Grupo Lazarus** –también conocido como APT38 y vinculado a Corea del Norte– posee un historial de operaciones de alto perfil contra instituciones financieras y plataformas de criptomonedas. Entre sus ataques se destacan:

- **Bangladesh Bank Heist (2016):** Robo de 81 millones de dólares mediante la manipulación del sistema SWIFT.  
- **WannaCry (2017):** Propagación global de ransomware que afectó a múltiples sectores.  
- **Ataques a Exchanges Cripto:** Incidentes en plataformas como Phemex, KuCoin y otros protocolos DeFi.

Expertos como **ZachXBT** y equipos de análisis forense han identificado patrones y técnicas operativas (fragmentación de fondos, test transactions y sincronización de actividades) que vinculan este ataque con métodos previamente utilizados por Lazarus.

---

## 3. Anatomía del Ataque

### Línea de Tiempo del Incidente

- **T-0: Compromiso Inicial**  
  Los atacantes identificaron a los firmantes clave de la multisig a través de OSINT y phishing dirigido. Se presume que infectaron sus dispositivos mediante malware (keyloggers o inyectores de scripts) que alteró el flujo de datos antes de la firma.

- **T+1: Manipulación de la Interfaz y Autorización**  
  El malware modificó la visualización en la interfaz de **Safe** (anteriormente Gnosis Safe), mostrando una transacción legítima a la warm wallet de Bybit. Sin embargo, en realidad se aprobó una modificación maliciosa en la lógica del smart contract, cediendo el control total de la billetera fría al atacante.

- **T+2: Ejecución y Exfiltración de Fondos**  
  Tras obtener las firmas, se ejecutó la transacción en la red Ethereum. Los fondos se dispersaron en **53 direcciones** y se realizaron intercambios en DEXs (como Curve y Uniswap), convirtiendo aproximadamente $200M en stETH a ETH y dividiendo lotes de 10K ETH para dificultar el rastreo.

- **T+3: Atribución y Análisis Forense**  
  La sincronización de transacciones y la reutilización de patrones permitieron atribuir el ataque al Grupo Lazarus, alineándolo con técnicas utilizadas en ataques previos, como el hackeo a Phemex.

![arkhm](https://pbs.twimg.com/media/GkU8D6xWkAAw24l?format=jpg&name=4096x4096)

### Desglose Técnico del Ataque

**a) Identificación y Compromiso de Firmantes**  
- **Técnicas:** Recolección de información vía OSINT y phishing dirigido.  
- **Método:** Infección de dispositivos con malware que interceptó y alteró datos en el momento de la firma.

**b) UI Spoofing y Secuestro de Firmas**  
- **Proceso:** El malware alteró la visualización local en la interfaz de Safe, presentando una transacción “legítima”.  
- **Resultado:** Los firmantes autorizaron sin saber que la lógica subyacente había sido modificada.

**c) Alteración del Smart Contract**  
- **Modificación:** La transacción maliciosa insertó una función de backdoor en el contrato multisig, permitiendo retirar fondos sin requerir futuras autorizaciones.

**d) Dispersión y Lavado de Activos**  
- **Fragmentación:** Los activos fueron dispersados en 53 direcciones y divididos en lotes de 10K ETH.  
- **Estrategia:** Se optó por intercambios en DEXs y movimientos hacia OTCs en Asia, evitando el uso de mezcladores y dificultando la trazabilidad.

---

## 4. Respuesta de Bybit y Manejo de la Crisis

![Bybit](https://pbs.twimg.com/media/GkVovhzWYAAYq4K?format=png&name=900x900)

### Magnitud del Daño

- **Robo Histórico:** Además de la cifra global (~1.46 mil millones de dólares), se confirmó que fueron sustraídos **401K ETH** de la billetera fría comprometida.  
- **No se detuvieron retiros:** Bybit continúa operando normalmente, garantizando que solo una billetera fría fue comprometida y que los fondos de clientes están respaldados 1:1.

### Gestión de Retiros y Transparencia

- **4,000 Retiros Pendientes:** Bybit afirmó que se procesarían en pocas horas, priorizando a clientes minoristas sobre instituciones.  
- **Grandes Retiros:** Pasan por controles de seguridad estándar y no han sido pausados.  
- **Colaboración con la Industria:** Market makers, socios y hasta exchanges competidores han ofrecido apoyo a Bybit, reforzando la credibilidad y la confianza en su solvencia.

### Estrategia de Comunicación

- **Admisión del Punto de Brecha:** Bybit señaló que la interfaz de Gnosis Safe fue “muskeada” y que no se trató de una negligencia, sino de un ataque de ingeniería social muy sofisticado.  
- **Diálogo con los Hackers:** Asumiendo que podrían estar observando, Bybit enfatizó lo difícil que sería para los atacantes liquidar los fondos robados e invitó a una posible negociación.  
- **Promesa de Post-Mortem:** Bybit se comprometió a publicar un informe detallado del incidente para compartir aprendizajes con la comunidad.

---

## 5. Implicaciones para la Industria Cripto

### Replanteamiento de la Seguridad Multisig y del Almacenamiento en Frío

- **Limitaciones del Multisig:** Si todos los firmantes son comprometidos, la seguridad de un esquema M-of-N colapsa.  
- **Revisión de Interfaces:** La manipulación de la UI pone de relieve la necesidad de utilizar hardware wallets con verificación en pantalla y dispositivos aislados del entorno web.

### Enfoque en el Factor Humano

- **Ingeniería Social 2.0:** La confianza depositada en interfaces legítimas fue explotada, subrayando la importancia de la formación continua y la verificación en múltiples canales.  
- **Posible Fuga de Información:** El hecho de que los atacantes supieran exactamente a quién debían apuntar sugiere un trabajo de inteligencia previo (inside job, espionaje de correos, etc.).

### Desafíos Forenses y Colaboración Internacional

- **Rastreo de Fondos:** La fragmentación y dispersión de activos complica el análisis forense, aunque herramientas on-chain han permitido atribuir el ataque a Lazarus.  
- **Regulación y Sanciones:** Se espera que este incidente impulse la coordinación entre agencias internacionales y exchanges para congelar fondos sospechosos y reforzar la seguridad del ecosistema.

---

## 6. Conclusiones y Perspectivas

El hackeo a Bybit marca un antes y un después en la seguridad de las criptomonedas. La sofisticación del ataque –que combina precisión quirúrgica en la manipulación de la interfaz con técnicas avanzadas de ingeniería social– demuestra que la seguridad no depende únicamente de la robustez del código, sino también de la protección integral de la cadena humana.

Este incidente expone las limitaciones de las soluciones multisig y el almacenamiento en frío, e insta a la industria a adoptar métodos de verificación más rigurosos, integrando controles técnicos avanzados con una capacitación continua y una mentalidad de “zero trust”.

> **“El mayor desafío no es el código, sino asegurar que la persona detrás de la firma nunca sea el eslabón débil.”**

---

## 7. Disclaimer

Esta noticia se basa en información pública, análisis on-chain y comunicados oficiales. No constituye asesoría financiera ni legal. Se recomienda a las instituciones y usuarios consultar a expertos en ciberseguridad para fortalecer sus protocolos de protección.

---
