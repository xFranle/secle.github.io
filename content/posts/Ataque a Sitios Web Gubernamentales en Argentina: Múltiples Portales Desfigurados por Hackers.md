+++
title = 'Ataque a Sitios Web Gubernamentales en Argentina: Múltiples Portales Desfigurados por Hackers'
date = 2024-09-05
draft = false
author = 'Franle'
tags = ['defacement', 'argentina', 'hackeo']
+++

---

## Índice
1. 🔍 [Descripción del Incidente](#-descripci%C3%B3n-del-incidente)
2. 🛡️ [Sitios Web Comprometidos](#sitios-web-comprometidos)
3. 🛑 [Detalles del Anuncio](#detalles-del-anuncio)
4. 🕵️‍♂️ [Análisis del Ataque](#análisis-del-ataque)
5. ⚠️ [Impacto y Riesgos Potenciales](#impacto-y-riesgos-potenciales)
6. 🕵️‍♂️ [Hipótesis del Ataque](#hipótesis-del-ataque)
7. ✅ [Medidas Preventivas y Recomendaciones](#medidas-preventivas-y-recomendaciones)

---

## 🔍 Descripción del Incidente

Diversos sitios web gubernamentales en Argentina han sido atacados y desfigurados por un grupo de hackers. Entre los portales afectados se encuentran los de la **Policía de Santiago del Estero**, el **Municipio de Paraná**, el **Municipio de Ezeiza**, y el **Concejo Deliberante de Cerrito**. En todos estos casos, los hackers dejaron mensajes de burla y amenazas, además de modificar completamente la página de inicio de los sitios.

---

## 🛡️ Sitios Web Comprometidos

Los siguientes portales han sido identificados entre los sitios web gubernamentales comprometidos:

- **Policía de Santiago del Estero**
- **Municipio de Paraná**
- **Municipio de Ezeiza**
- **Concejo Deliberante de Cerrito**

Los atacantes han aprovechado vulnerabilidades en la seguridad de estos sitios para modificar su contenido y dejar mensajes en los que se arrogan la responsabilidad del ataque, burlándose de la seguridad cibernética de los portales oficiales.

---

## 🛑 Detalles del Anuncio

En los sitios desfigurados, los atacantes dejaron mensajes claros y burlones sobre la vulnerabilidad de estos portales. Dado que los sistemas estaban utilizando versiones obsoletas de WordPress y Apache, es probable que los hackers hayan aprovechado vulnerabilidades conocidas en estas tecnologías para llevar a cabo los ataques.

Un ejemplo destacado es el sitio de la **Policía de Santiago del Estero**, donde los hackers incluyeron el mensaje: _"otro site de policia pra conta, é nois que tá"_, haciendo alusión a otros ataques previos a sitios policiales.

Además, en el sitio del **Municipio de Paraná**, los atacantes escribieron: _"Your website has been hacked, don’t panique, laugh before we laugh"_ junto con referencias a un grupo autodenominado "Hacktivist Army of Indonesia".

---

## 🕵️‍♂️ Análisis del Ataque

Este tipo de desfiguración de sitios web suele ser un ataque de bajo nivel técnico, pero altamente visible y dañino en términos de reputación y confianza en las instituciones públicas. Los hackers buscan exponer la falta de medidas adecuadas de seguridad en los sitios web gubernamentales, afectando la imagen pública de los organismos involucrados.

Aunque estos ataques no suelen tener como objetivo la extracción de datos sensibles, la capacidad de vulnerar la seguridad de portales oficiales deja la puerta abierta para ataques más graves en el futuro.

---

## ⚠️ Impacto y Riesgos Potenciales

Este tipo de ataques puede tener varios impactos negativos:

1. **Pérdida de confianza pública**: La desfiguración de sitios gubernamentales genera desconfianza en la capacidad del gobierno para proteger su infraestructura digital.
2. **Daño reputacional**: La exposición mediática de estos ataques afecta la imagen de las entidades afectadas, tanto a nivel nacional como internacional.
3. **Riesgos futuros**: Aunque en esta ocasión los ataques se enfocaron en desfigurar páginas, la misma vulnerabilidad podría ser aprovechada para acceder a datos sensibles en el futuro.

---

## 🕵️‍♂️ Hipótesis del Ataque

A partir de la información recopilada sobre las tecnologías y versiones de software utilizadas en los sitios web afectados, se pueden plantear varias hipótesis sobre las posibles causas de las vulnerabilidades explotadas por los atacantes:

1. **Versiones de WordPress Desactualizadas**: Todos los sitios hackeados utilizan **WordPress 6.0.9**, una versión que ya no es la más reciente (la última estable es la 6.6.1). WordPress es uno de los gestores de contenido más utilizados, pero también uno de los más atacados debido a su popularidad. La falta de actualizaciones puede exponer los sitios a vulnerabilidades conocidas, ya que las versiones anteriores pueden contener fallos de seguridad que los atacantes podrían haber explotado para acceder a los sistemas.

2. **Apache HTTP Server 2.4.29 en Ubuntu**: El servidor web Apache utilizado en los sitios está en la versión **2.4.29**, la cual también está desactualizada (la versión estable actual es 2.4.62). Las versiones antiguas de Apache son conocidas por tener vulnerabilidades, como **CVE-2018-1312** y **CVE-2021-41773**, que permiten a los atacantes realizar **path traversal** o incluso ejecutar código malicioso si no se han aplicado los parches correspondientes.

3. **Librerías JavaScript y Plugins de WordPress**: Las librerías **jQuery 3.5.1** y **jQuery Migrate 3.3.2** utilizadas en los sitios también están obsoletas. jQuery es una de las librerías más populares, y versiones antiguas son un objetivo recurrente de ataques XSS (cross-site scripting). Además, el plugin **Contact Form 7 (v5.6.3)**, ampliamente usado en WordPress, ha sufrido vulnerabilidades críticas en el pasado que permiten la ejecución de código malicioso en el servidor. Si no se ha actualizado a su versión más reciente, esta puede haber sido una de las principales vías de entrada para los hackers.

4. **Uso de GSAP 1.19.1 y Otros Frameworks Obsoletos**: El framework **GSAP (1.19.1)** también está desactualizado, lo que podría haber permitido a los atacantes explotar alguna vulnerabilidad no parcheada en la ejecución de código dinámico en el sitio.

5. **Configuraciones de Seguridad Relajadas en Apache y PHP**: La configuración por defecto de Apache y PHP a menudo no es lo suficientemente segura si no se ajustan adecuadamente. La falta de endurecimiento de estos servidores, como no deshabilitar funciones inseguras en PHP o no configurar permisos de archivos y directorios adecuadamente, podría haber permitido el acceso de los atacantes.

6. **Falta de Actualización de Plugins y Componentes**: La presencia de múltiples plugins de WordPress, como **MetaSlider** y **PhotoSwipe**, puede ser otro vector de ataque. Si alguno de estos no ha sido actualizado o contiene una vulnerabilidad, los hackers pudieron haber utilizado estos elementos como puerta de entrada al sistema.

En conclusión, es muy probable que los atacantes hayan explotado una combinación de vulnerabilidades en WordPress y sus plugins, así como en versiones desactualizadas del servidor Apache y librerías JavaScript. Este tipo de ataques pone en evidencia la importancia de mantener actualizado el software y las configuraciones de seguridad de los servidores.

---

## ✅ Medidas Preventivas y Recomendaciones

Ante este escenario, es crucial que las instituciones públicas tomen medidas inmediatas para fortalecer la seguridad de sus portales web. A continuación, se proponen algunas acciones:

1. **Actualización Inmediata de CMS y Plugins**: Es fundamental que todos los sitios actualicen a la última versión de **WordPress**, junto con todos los plugins instalados como **Contact Form 7** y **MetaSlider**. Las versiones desactualizadas contienen vulnerabilidades conocidas que pueden ser explotadas por atacantes.

2. **Aplicación de Parches de Seguridad para Apache**: Se recomienda actualizar el servidor **Apache HTTP Server** a la última versión disponible (actualmente la 2.4.57) para mitigar cualquier vulnerabilidad conocida.

3. **Revisión de Configuraciones de Seguridad en PHP**: Se deben ajustar las configuraciones de PHP, deshabilitando funciones inseguras y limitando el acceso a archivos del servidor a través de permisos estrictos.

4. **Revisión y Actualización de Librerías JavaScript**: Librerías como **jQuery**, **GSAP**, y otros frameworks utilizados en el sitio deben ser revisados y actualizados a sus versiones más recientes, para evitar ataques de inyección de código o cross-site scripting (XSS).

---

## Disclaimer

La información presentada en este artículo tiene fines puramente informativos y educativos. No se han divulgado datos personales ni información sensible de manera que pueda identificar a individuos específicos. Todos los detalles sensibles han sido debidamente anonimizados para proteger la privacidad de los afectados.

Este blog no promueve ni respalda ninguna actividad ilegal, y se esfuerza por concienciar sobre la importancia de la ciberseguridad y la protección de datos personales. Cualquier uso indebido de la información aquí compartida es responsabilidad exclusiva del individuo que lo lleve a cabo.

---
