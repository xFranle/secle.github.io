+++
title = 'Expuesta la base de datos de OSSE San Juan: 30 archivos SQL con datos sensibles'
date = 2025-05-27
draft = false
author = 'Franle'
tags = ['argentina', 'filtración', 'datos personales', 'aero', 'osse', 'san juan', 'sql']
+++

---

![OSSE filtración](https://i.gyazo.com/d14066f047df24a42bd6691a3bfd615c.png)

## Índice
- [Resumen del incidente](#resumen-del-incidente)
- [¿Qué es OSSE San Juan?](#qué-es-osse-san-juan)
- [¿Qué información fue comprometida?](#qué-información-fue-comprometida)
- [¿Quién está detrás de la filtración?](#quién-está-detrás-de-la-filtración)
- [Riesgos y posibles impactos](#riesgos-y-posibles-impactos)
- [Buenas prácticas recomendadas](#buenas-prácticas-recomendadas)
- [Conclusión](#conclusión)
- [FAQ](#faq)
- [Disclaimer](#disclaimer)

---

## Resumen del incidente

El actor de amenazas **“aero”**, identificado recientemente por la filtración de la infraestructura del Servicio Penitenciario Bonaerense, ha vuelto a atacar. Esta vez, se ha publicado un **volcado completo de la base de datos interna de Obras Sanitarias Sociedad del Estado (OSSE) de San Juan**, Argentina.

El dump contiene más de **30 archivos SQL exportados desde phpMyAdmin**, con información sensible que va desde **datos personales de empleados y contratistas**, hasta **registros de pagos e infraestructura crítica**.

---

## ¿Qué es OSSE San Juan?

OSSE (Obras Sanitarias Sociedad del Estado) es la empresa estatal encargada de **proveer servicios de agua potable y saneamiento** en la provincia de San Juan. Su infraestructura incluye redes hidráulicas, plantas de tratamiento, documentación técnica, contratistas externos y recursos humanos públicos.

---

## ¿Qué información fue comprometida?

El dump incluye más de 30 archivos `.sql`, cada uno correspondiente a una tabla. Entre ellos:

- `personas_cv.sql`: con datos completos de empleados y postulantes (nombres, DNI, direcciones, correos, estudios, teléfonos).
- `emails.sql`: registros internos de correos electrónicos.
- `pagos.sql`, `contratistas.sql`: información financiera y comercial.
- `documentos_archivos.sql`: posiblemente archivos o referencias a infraestructura técnica y documentos escaneados.
- Otras tablas referidas a concursos, licitaciones, departamentos, instalaciones y características técnicas de obras.

> El dump fue subido a plataformas públicas de almacenamiento y acompañado por capturas como prueba, todo desde el perfil del actor “aero” en foros de la dark web.

---

## ¿Quién está detrás de la filtración?

El actor **“aero”**, que ya había sido identificado por la filtración al SPB días atrás, continúa con una seguidilla de publicaciones dirigidas a instituciones gubernamentales argentinas. Su actividad indica un patrón de ataque orientado a **exponer debilidades estructurales** en sistemas públicos, sin evidencia concreta (por ahora) de motivaciones financieras directas como ransomware.

Se desconoce si el actor obtuvo esta información mediante acceso remoto, colaboración interna o ingeniería social, pero el uso de `phpMyAdmin` sugiere un acceso web mal asegurado.

---

## Riesgos y posibles impactos

1. **Exposición masiva de datos personales**: puede derivar en robo de identidad, campañas de phishing o doxing.
2. **Riesgos reputacionales e institucionales**: la falta de resguardo daña la imagen de OSSE ante la ciudadanía.
3. **Información sobre contratistas y pagos**: podría ser usada para fraudes administrativos o extorsiones.
4. **Planos y datos técnicos de infraestructura**: representan una amenaza directa a la seguridad de servicios públicos esenciales.

---

## Buenas prácticas recomendadas

- **Evitar acceso público a phpMyAdmin** y restringirlo por VPN.
- **Implementar WAFs y sistemas de detección de intrusos (IDS/IPS)**.
- **Auditorías periódicas de acceso, configuraciones y endpoints expuestos.**
- **Segmentación y cifrado de bases de datos sensibles.**
- **Resguardo de archivos en buckets privados (S3, Azure Blob) y no en servidores públicos.**

---

## Conclusión

Esta filtración no es solo un incidente técnico: es una nueva señal de alarma sobre el **estado de la ciberseguridad en entidades públicas argentinas**. El hecho de que en menos de una semana el mismo actor haya expuesto a **dos organismos críticos** revela un patrón de negligencia estructural que debe ser atendido con urgencia.

La protección de datos ciudadanos, información interna y operativa no es una opción: es una responsabilidad legal y ética.

---

## FAQ

**¿Qué es OSSE?**  
Obras Sanitarias Sociedad del Estado, responsable del agua y saneamiento en San Juan.

**¿Qué datos contiene el dump?**  
Información personal, correos, pagos, contratistas y archivos de infraestructura.

**¿Fue ransomware?**  
No. Hasta el momento no se ha exigido rescate. Es una exposición pública con fines aún no declarados.

**¿Qué medidas deberían tomar otras instituciones ahora mismo?**  
Revisar accesos a paneles web (phpMyAdmin, cPanel, etc.), proteger bases de datos, y segmentar datos sensibles.

---

## Disclaimer

Esta publicación tiene fines informativos y educativos. No promovemos ni avalamos la publicación o distribución de información obtenida sin autorización. El análisis presentado se basa en fuentes públicas con el objetivo de mejorar las prácticas de ciberseguridad y concientización dentro del sector público argentino.
