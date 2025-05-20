+++
title = 'Filtración de Infraestructura Interna del Servicio Penitenciario Bonaerense (SPB)'
date = 2025-05-20
draft = false
author = 'Franle'
tags = ['argentina', 'filtración', 'infraestructura', 'fortinet', 'spb', 'ciberseguridad']
+++

---

![Infraestructura expuesta del SPB](https://i.gyazo.com/de9ca953bdc17d5ae731f89a35b6b26c.png)

## Índice
- [Resumen del incidente](#resumen-del-incidente)
- [¿Qué información fue filtrada?](#qué-información-fue-filtrada)
- [¿Qué se puede inferir del equipamiento expuesto?](#qué-se-puede-inferir-del-equipamiento-expuesto)
- [¿Quién es el actor “aero”?](#quién-es-el-actor-aero)
- [Implicancias y riesgos de esta exposición](#implicancias-y-riesgos-de-esta-exposición)
- [Recomendaciones técnicas para entornos gubernamentales](#recomendaciones-técnicas-para-entornos-gubernamentales)
- [Conclusión](#conclusión)
- [FAQ](#faq)
- [Disclaimer](#disclaimer)

---

## Resumen del incidente

Una nueva filtración de alto impacto compromete la seguridad del **Servicio Penitenciario Bonaerense (SPB)**, una institución crítica del sistema de justicia argentino. El actor de amenazas conocido como **“aero”** ha publicado un set de imágenes internas que revelan con alto nivel de detalle la infraestructura tecnológica utilizada por el organismo.

Las imágenes muestran **equipos Fortinet**, **modems**, **repetidores**, **racks completos**, **PCs** y resultados de **pruebas de velocidad realizadas desde dentro de la red oficial**, además de **etiquetas con claves, seriales y datos técnicos** de varios dispositivos.

---

## ¿Qué información fue filtrada?

Las imágenes publicadas exponen:

- Equipamiento Fortinet (FortiGate, FortiCloud, FortiAP).
- Routers Cisco 920 y Cisco 1800.
- Módems Huawei y equipos de conectividad TP-Link.
- Racks de servidores con cableado estructurado.
- Etiquetas con **números de serie, credenciales, MACs y configuración visible**.
- Capturas de pantalla con **resultados de tests de velocidad** desde distintas unidades.
- Actas internas vinculadas al mantenimiento o control de los sistemas.

---

## ¿Qué se puede inferir del equipamiento expuesto?

El nivel de exposición permite a cualquier actor malicioso realizar un **mapeo detallado de la red interna del SPB**, incluyendo:

- Información sensible que podría facilitar ataques de **reconocimiento activo** y posterior intrusión.
- Evidencia de **configuraciones potencialmente inseguras o desactualizadas**.
- Falta de controles sobre **filtración física y digital** del entorno operativo.

> Este tipo de exposición no solo viola principios básicos de seguridad como *Confidencialidad e Integridad*, sino que también compromete el **principio de Seguridad Física y Operativa**, fundamental en infraestructuras críticas.

---

## ¿Quién es el actor “aero”?

“Aero” es un actor relativamente nuevo en la escena de filtraciones vinculadas a entidades gubernamentales argentinas. Si bien aún no se conocen detalles técnicos sobre su método de obtención, el nivel de acceso sugiere:

- **Acceso físico temporal o prolongado** a instalaciones.
- **Ingeniería social** o colaboración interna.
- Ausencia de control de dispositivos de almacenamiento removibles y cámaras.

---

## Implicancias y riesgos de esta exposición

1. **Riesgo operativo:** Si los dispositivos mostrados siguen en uso, podrían ser objetivos de explotación por parte de terceros.
2. **Filtración de claves o configuraciones:** Seriales y configuraciones visibles pueden ser aprovechadas para ataques dirigidos.
3. **Desprestigio institucional:** Afecta la confianza en la capacidad del SPB de proteger sistemas críticos.
4. **Evidencia de falta de políticas de control de activos físicos y documentación digital.**

Además, si estas imágenes fueron obtenidas con facilidad, plantea una **alarmante falta de controles de acceso y monitoreo**.

---

## Recomendaciones técnicas para entornos gubernamentales

- **Rotación inmediata de claves y revisión de configuraciones expuestas.**
- **Segmentación de red y aislamiento de equipos de misión crítica.**
- **Instalación de sistemas de control de acceso físico y cámaras.**
- **Capacitación interna para prevención de filtraciones físicas y digitales.**
- **Clasificación y manejo seguro de información operativa y visual.**

---

## Conclusión

La filtración de la infraestructura tecnológica del Servicio Penitenciario Bonaerense no es solo una exposición de fotos: es una alerta crítica sobre las **vulnerabilidades físicas, procedimentales y culturales** que aún existen en entornos gubernamentales argentinos. La modernización tecnológica no puede estar desvinculada de una cultura de seguridad rigurosa. Esta brecha debe atenderse con prioridad para evitar impactos aún más graves.

---

## FAQ

**¿Se accedió a datos digitales o bases internas del SPB?**  
No se han divulgado archivos digitales o bases; solo imágenes que, sin embargo, contienen información sensible.

**¿Es una amenaza activa o ya neutralizada?**  
No se puede determinar. Si el equipamiento sigue en uso, los riesgos son altos.

**¿Esto compromete directamente a las cárceles?**  
Compromete la infraestructura digital que podría tener implicancia en vigilancia, comunicación y administración de unidades penitenciarias.

---

## Disclaimer

La información contenida en esta publicación tiene fines informativos y de análisis en el marco de la ciberseguridad. No promovemos ni legitimamos filtraciones ni accesos no autorizados. Las imágenes analizadas fueron obtenidas de fuentes públicas y su interpretación está destinada a promover mejoras en la protección de infraestructura crítica.
