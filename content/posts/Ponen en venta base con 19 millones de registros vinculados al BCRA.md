+++
title = 'Ponen en venta base con 19 millones de registros vinculados al BCRA'
date = 2025-06-04
draft = false
author = 'Franle'
tags = ['argentina', 'bcra', 'datos filtrados', 'venta de datos', 'darkweb', 'base de datos']
+++

---

![filtracion BCRA](https://i.gyazo.com/e542a2558b83956d5026562b798c2fd9.png)

## Índice
- [Resumen del incidente](#resumen-del-incidente)
- [¿Qué contiene la base puesta en venta?](#qué-contiene-la-base-puesta-en-venta)
- [¿Es realmente del BCRA?](#es-realmente-del-bcra)
- [Análisis del esquema de la tabla](#análisis-del-esquema-de-la-tabla)
- [Riesgos asociados a la venta de este tipo de bases](#riesgos-asociados-a-la-venta-de-este-tipo-de-bases)
- [Comparativa con filtraciones anteriores](#comparativa-con-filtraciones-anteriores)
- [Conclusión](#conclusión)
- [FAQ](#faq)
- [Disclaimer](#disclaimer)

---

## Resumen del incidente

En foros de compraventa de datos en la dark web, apareció una publicación que ofrece una supuesta base de datos con **más de 19 millones de registros vinculados al BCRA (Banco Central de la República Argentina)**.

La publicación asegura contener información de carácter personal y financiero asociada a ciudadanos argentinos, con detalles como **CUIL completo, historial crediticio, deudas y préstamos**, todo vinculado a registros del sistema financiero nacional.

Aunque la información ofrecida parece estar compuesta **mayormente por datos públicos o semipúblicos**, el volumen, la estructura y el contexto podrían representar un **riesgo significativo de reidentificación y uso malicioso**.

---

## ¿Qué contiene la base puesta en venta?

Según el vendedor, la base incluye para cada registro:

- Apellido y nombre  
- Tipo y número de documento  
- CUIL completo  
- Fecha de nacimiento  
- Dirección (calle y número)  
- Ciudad y código postal  
- Teléfono  
- Número único de cliente  

Además, el vendedor afirma que cada registro está vinculado a:

- **Informes de deuda**  
- **Préstamos y créditos registrados**  
- **Antecedentes financieros reportados al BCRA**

El total anunciado es de **19.000.680 registros**, lo que implicaría un volumen considerable respecto a la población económicamente activa del país.

---

## ¿Es realmente del BCRA?

No hay forma de confirmar con certeza que la base provenga directamente de los sistemas del Banco Central. Sin embargo, el tipo de información listada coincide con bases de datos que utilizan:

- **Bancos y entidades financieras reguladas**  
- **Sistemas de scoring crediticio**  
- **Prestadoras de informes como Veraz o Nosis**  
- **Registros centralizados que reportan al BCRA (como la Central de Deudores)**

La estructura también coincide con formatos que suelen ser utilizados en sistemas legacy o migraciones internas.

---

## Análisis del esquema de la tabla

El vendedor comparte un esquema SQL que corresponde a una tabla llamada `clientes`, estructurada con campos como: nombre, apellido, documento, CUIL, dirección, localidad, teléfono, código postal y número de cliente.  

La estructura presentada utiliza tecnología **MyISAM y charset latin1**, típica de sistemas heredados y poco modernos, lo que refuerza la idea de que pudo haberse tratado de una migración o backup antiguo.

---

## Riesgos asociados a la venta de este tipo de bases

Aunque muchos de los datos sean técnicamente públicos o se puedan obtener por otras vías, su **combinación masiva y estructura relacional** potencia enormemente los riesgos:

- **Spear phishing altamente dirigido**  
- **Simulación de identidad (fraude)**  
- **Enriquecimiento de campañas de ingeniería social**  
- **Reidentificación cruzada con otras filtraciones previas**

Además, el posible vínculo con información crediticia lo convierte en material atractivo para **estafadores, prestamistas ilegales y grupos que ejecutan extorsiones digitales**.

---

## Comparativa con filtraciones anteriores

Esta no es la primera vez que se intenta comercializar una base de este estilo. Durante el 2024, circularon dos versiones previas:

- Una con 9.000 registros  
- Otra con 49.000 registros  

Ambas contenían parte del mismo tipo de información, pero el salto a **19 millones de registros** marcaría una escalada significativa si se confirma su autenticidad.

---

## Conclusión

La aparición de esta base masiva, supuestamente vinculada al BCRA, refuerza la necesidad urgente de:

- Implementar mayores controles sobre la distribución y almacenamiento de datos financieros  
- Adoptar mecanismos de pseudonimización, hashing y acceso segmentado en entidades públicas y privadas  
- **Investigar y confirmar el origen** de este dump para evitar la propagación de información descontextualizada o manipulada

La venta de este tipo de datasets es una amenaza directa a la privacidad financiera de millones de argentinos y pone en evidencia lo frágiles que son aún algunos canales institucionales.

---

## FAQ

**¿Es oficial que la base fue robada del BCRA?**  
No hay confirmación oficial. El vendedor afirma su origen, pero no hay pruebas concluyentes.

**¿Qué tipo de datos contiene?**  
Información personal completa, más posibles vínculos con historial financiero.

**¿Es ilegal acceder o descargar esta base?**  
Sí. Cualquier descarga o comercialización de esta información constituye una infracción a la Ley de Protección de Datos Personales (Ley 25.326).

**¿Qué deberían hacer las personas si su información está incluida?**  
Estar alerta ante intentos de estafas personalizadas y revisar sus perfiles en centrales de riesgo.

---

## Disclaimer

Este artículo tiene fines exclusivamente informativos y busca alertar sobre el uso indebido de bases de datos con información personal. No se promueve ni se enlaza al contenido original, ni se avala ningún tipo de actividad ilegal. El análisis se realiza con base en publicaciones abiertas en foros de discusión y se enmarca dentro del ejercicio ético del periodismo de ciberseguridad.
