+++
title = '🚨 Venta de Base de Datos del Hospital Evita Pueblo de Berazategui'
date = 2024-08-09
draft = false
author = 'Franle'
tags = ['Ciberseguridad', 'filtracion', 'hackeo', 'argentina']
+++

---

## 📋 Índice
- 🔍 [Descripción del Incidente](#🔍-descripción-del-incidente)
- 🛡️ [Información Comprometida](#🛡️-información-comprometida)
- 🛑 [Detalles del Anuncio](#🛑-detalles-del-anuncio)
- 🕵️‍♂️ [Cómo Ocurrió la Filtración](#🕵️‍♂️-cómo-ocurrió-la-filtración)
- ⚠️ [Impacto y Riesgos Potenciales](#⚠️-impacto-y-riesgos-potenciales)
- ✅ [Medidas Preventivas y Recomendaciones](#✅-medidas-preventivas-y-recomendaciones)

---

## 🔍 Descripción del Incidente

Recientemente, se ha reportado la venta de una base de datos perteneciente al **Hospital Evita Pueblo de Berazategui**. Esta base de datos, que contiene más de **40.000 registros** con información sensible de pacientes, ha sido puesta en venta por un actor de amenazas bajo el seudónimo **"MimiChan"**.

## 🛡️ Información Comprometida

La base de datos expuesta incluye información altamente sensible de los pacientes del hospital, tales como:

- **DNI**
- **Correo Electrónico**
- **Contraseñas**
- **Números de Celular**
- **Información sobre la Obra Social**

## 🛑 Detalles del Anuncio

El actor de amenazas, MimiChan, publicó el anuncio en inglés en un foro de ciberseguridad, ofreciendo un archivo de descarga con una muestra de **5.000 líneas** de datos. Según sus palabras:

_"Lines: it has 5k lines but the complete database contains more than 40k lines Cool important: the download file only contains 5 thousand lines, for the user who wants the complete database of patients (+40k lines) below I leave the sql error for you to exploit it, I didn't do it because of time issues."_

Además, MimiChan proporcionó un enlace para acceder al archivo y mencionó que, para aquellos interesados en la base de datos completa, también dejó a disposición el error SQL que permitió la filtración:

_"For those who want the whole database I leave the sql error here and I also leave the link."_

## 🕵️‍♂️ Cómo Ocurrió la Filtración

El anuncio de MimiChan sugiere que la base de datos fue comprometida mediante la explotación de una vulnerabilidad de **SQL Injection**. Este tipo de ataque ocurre cuando un atacante inserta o "inyecta" una consulta SQL maliciosa en los datos de entrada de una aplicación, permitiendo el acceso no autorizado a la base de datos.

## ⚠️ Impacto y Riesgos Potenciales

La filtración de esta base de datos no solo representa un riesgo grave para la privacidad de los pacientes, sino que también expone al hospital a posibles acciones legales y daños a su reputación. Los datos comprometidos podrían ser utilizados para fraudes de identidad, extorsión, o incluso para la venta en mercados clandestinos.

## ✅ Medidas Preventivas y Recomendaciones

Para mitigar este tipo de incidentes en el futuro, es crucial que las instituciones de salud implementen prácticas de seguridad cibernética más robustas. Algunas recomendaciones incluyen:

- **Auditorías de Seguridad Periódicas**: Evaluar regularmente las vulnerabilidades en las aplicaciones web y bases de datos.
- **Parcheo de Vulnerabilidades**: Aplicar rápidamente los parches de seguridad para corregir vulnerabilidades conocidas.
- **Capacitación del Personal**: Asegurar que el personal esté capacitado en las mejores prácticas de seguridad, incluyendo la identificación y reporte de posibles amenazas.

---
