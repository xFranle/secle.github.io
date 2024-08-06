+++
title = 'Seguridad en Riesgo: Análisis del Ataque a Bittensor y la Recompensa por Justicia'
date = 2024-07-08T01:55:19-03:00
draft = false
author = 'Franle'
tags = ['criptomonedas', 'blockchain', 'hackeo']
+++

---
-   🧠 ¿Qué es Bittensor (TAO) y cómo funciona?
-   📋 [Resumen](#-resumen)
-   🕵️‍♂️ [Detalles del Ataque]
-   ⏳ [Cronología](#-cronología-del-incidente)
-   🧬 [Código Malicioso](#-código-malicioso)
-   🔍 [Análisis del Comportamiento Anómalo](#-análisis-del-comportamiento-anómalo)
    -   ⚠️ [Indicadores de Compromiso](#-indicadores-de-compromiso)
-   🛡️ [Medidas de Mitigación Adoptadas](#-medidas-de-mitigación-adoptadas)
    -   🗝️ [Puntos Clave](#-puntos-clave)
    -   🚨 [Importancia de estas Medidas](#-importancia-de-estas-medidas)
-   📚 [Lecciones Aprendidas](#-lecciones-aprendidas)
-   🕵️‍♂️ [Recompensa por Incidente de Seguridad de Bittensor](#-recompensa-por-incidente-de-seguridad-de-bittensor)
-   📝 [Conclusión](#-conclusión)
---
Nota: Esto es una investigación completamente independiente.

## 🧠 ¿Qué es Bittensor (TAO) y cómo funciona? [Click Aquí](https://www.binance.com/es/square/post/6727389891649)

## 📋 Resumen

El 3 de julio de 2024, Opentensor publicó una entrada en su blog sobre un incidente de seguridad significativo relacionado con la versión 6.12.2 del paquete "bittensor" en PyPI. Este incidente involucró la inclusión de una función maliciosa en el paquete, diseñada para enviar claves de billetera a un servidor controlado por el atacante. Pareciera ser que esto se deba a una clave API de PyPI comprometida.

### 🕵️‍♂️ Detalles del Ataque

El paquete malicioso fue publicado en PyPI el 22 de mayo de 2024 y permaneció disponible hasta el 2 de julio de 2024, un periodo de aproximadamente 41 días. Durante este tiempo, el código malicioso, disfrazado como una actualización legítima de "bittensor", robaba detalles de las claves frías no cifradas de los usuarios y las enviaba a un servidor remoto controlado por el atacante.

### ⏳ Cronología del Incidente

**22 de Mayo:**

-   **19:14 UTC**: El paquete malicioso fue publicado en PyPI.
-   **21:25 UTC**: La versión 6.12.2 fue publicada en GitHub por "gus-opentensor".
-   **21:25 UTC**: La imagen 6.12.2 fue publicada en [hub.docker.com](http://hub.docker.com) por "gopentensor".

**2 de Julio:**

-   **19:06 UTC**: El atacante comenzó a transferir fondos a su propia billetera.
-   **19:25 UTC**: Opentensor identificó el comportamiento anómalo y abrió una war room.
-   **19:41 UTC**: Se colocaron los validadores de cadena detrás de un firewall para evitar conexiones, deteniendo el procesamiento de transacciones para permitir el análisis.

### 🧬 Código Malicioso

Para determinar la causa raíz, se compararon las versiones del paquete "bittensor" de PyPI y GitHub. Se descubrió que la versión de PyPI contenía una función de validación adicional en el archivo `wallet.py` que no estaba presente en la versión de GitHub. Esta función enviaba las claves robadas a un servidor remoto usando una conexión HTTP simple.

### 🔍 Análisis del Comportamiento Anómalo

El análisis reveló que los tiempos de carga del paquete eran inusualmente variables, lo que sugiere que el atacante cargó el paquete en PyPI manualmente. La diferencia de más de dos horas entre la publicación en PyPI y las publicaciones en GitHub y Dockerhub indica un intento de ocultar rastros.

### ⚠️ Indicadores de Compromiso

El atacante utilizó conexiones HTTP para enviar datos a `api.opentensor.io/v1`. El análisis DNS mostró que este dominio ya no estaba activo en el momento de la investigación.

### **🛡️ Medidas de Mitigación Adoptadas**

-   **Eliminación del Paquete Malicioso**: Bittensor 6.12.2 ha sido eliminado.
-   **Auditoría de Código**: Revisión completa de los paquetes históricos y actuales de Bittensor/Subtensor.
-   **Cumplimiento de Normas ISO en PyPI**: Los paquetes deben cumplir con los estándares ISO, incluyendo la rotación automática de claves y la verificación de suma de verificación del paquete.
-   **Publicación de Claves Secundarias**.
-   **Separación de `wallet.py`**: Mayor dificultad de ataques de fuerza bruta y mayor complejidad y entropía de la contraseña predeterminada.
-   **Subsunción de Subpaquetes**: Para evitar ataques a subpaquetes.
-   **Soporte Nativo para Multifirma**: Creación de billeteras con multifirma y soporte para autenticación de dos factores en la billetera y extensión de iOS.
-   **Integración de Firma y Envío vía Archivo y QR**: Funciones avanzadas de seguridad en btwallet.

### **🗝️ Puntos Clave**

-   **Recuperación de Fondos**: Se estima que ~10.000 TAO de los 32.000 robados podrían recuperarse.
-   **Intercambio de Clave Fría**: Nueva función para proteger las billeteras en riesgo.
-   **Retraso de 72 Horas**: En los canjes para mayor seguridad.
-   **Proceso de Arbitraje**: Para intentos de intercambio conflictivos.

### **🚨 Importancia de estas Medidas**

-   **Protección contra Futuros Ataques**
-   **Fortalecimiento de la Seguridad de $TAO**
-   **Compromiso con la Seguridad del Usuario**

### 📚 Lecciones Aprendidas

Este incidente subraya varias lecciones importantes para la comunidad de desarrolladores y administradores de sistemas:

-   **Importancia de la Vigilancia Continua**: La supervisión constante de los paquetes publicados puede ayudar a detectar comportamientos anómalos antes de que se produzcan daños significativos.
-   **Automatización de la Seguridad**: Implementar flujos de trabajo automatizados para la revisión de código y la gestión de claves API puede reducir significativamente el riesgo de compromisos.
-   **Mejora Continua**: Las estrategias de seguridad deben evolucionar constantemente para mantenerse al día con las nuevas amenazas y vulnerabilidades.

### 🕵️‍♂️ Recompensa por Incidente de Seguridad de Bittensor

En respuesta al incidente de seguridad con el paquete malicioso "bittensor" versión 6.12.2, un usuario en Twitter ha ofrecido una recompensa significativa para identificar a los responsables de este ataque.

**Objetivo**: Identificar a las personas responsables de cargar el paquete PyPI malicioso "bittensor" versión 6.12.2.

**Recompensa**: Inicialmente, la recompensa fue de 50,000 USDT, pero ha aumentado a 202,000 USDT.

### Información Clave

-   **Dirección IP utilizada**: 192.42.116.196
    -   Nota: Se sospecha que la carga se realizó usando TOR y VPN.
-   **Carteras de hackers**:
    -   **Cartera Bittensor**: 5FbWTraF7jfBe5EvCmSThum85htcrEsCzwuFjG3PukTUQYot
    -   **Dirección de depósito MEXC**: 5DiKRbWtTtyanmgffRZvK3YQd2cdj4aTbJk1s7xXxJXUcBup
    -   **Dirección de depósito de Kucoin**: 5EaWsLaY8mwqEmLabtLmb7zECKCkHALCtgVqpXeH2prdbj
    -   **Dirección de depósito WTAO**: 5EhGYBakgin8TzUmNT5htx7QXoMMJbngf9wyZUWSNctNfRdo
    -   **Dirección ETH**: 0xa9f1b0ac7e4e6016a8027ec3b2b5e168b6e7639b

### Requisitos de la Recompensa

Para calificar para la recompensa, los participantes deben:

1.  **Proporcionar pruebas concluyentes** que identifiquen a las personas responsables de cargar el paquete malicioso.
2.  **Presentar un informe detallado** que describa el proceso de investigación, los hallazgos y las pruebas de respaldo.
3.  **Cumplir con todas las leyes aplicables** durante la investigación.

Para más detalles, puedes consultar el tweet original [aquí](https://x.com/fish_datura/status/1809342757204578323).

(actualizacion de monto a +200k usdt [aquí](https://x.com/fish_datura/status/1809653833359847792)).

### 📝 Conclusión

Este incidente resalta la necesidad de reforzar las prácticas de seguridad en la gestión de claves API y la publicación de paquetes. Es fundamental que las organizaciones implementen flujos de trabajo automatizados y revisiones de código robustas para minimizar el riesgo de compromisos. Además, el análisis proactivo y continuo de las distribuciones publicadas puede detectar anomalías antes de que causen daños significativos. Este ataque, aunque sofisticado, subraya la importancia de la vigilancia constante y la mejora continua en las estrategias de seguridad de la cadena de suministro de software.
