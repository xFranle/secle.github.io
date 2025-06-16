+++
title = 'Nueva filtración de "aero": más de 31.000 registros de UPCNBA expuestos'
date = 2025-06-16
draft = false
author = 'Franle'
tags = ['argentina', 'upcnba', 'datos filtrados', 'venta de datos', 'darkweb', 'aero']
+++

---

![Filtración UPCNBA](https://i.gyazo.com/18179defa1ac16dd786204fe53dc212a.png)

## Índice
- [Resumen del incidente](#resumen-del-incidente)
- [¿Qué es UPCNBA?](#qué-es-upcnba)
- [¿Qué información fue comprometida?](#qué-información-fue-comprometida)
- [¿Cómo fue publicada?](#cómo-fue-publicada)
- [Riesgos asociados](#riesgos-asociados)
- [Relación con otras filtraciones](#relación-con-otras-filtraciones)
- [Conclusión](#conclusión)
- [FAQ](#faq)
- [Disclaimer](#disclaimer)

---

## Resumen del incidente

El actor de amenazas **“aero”**, que ya ha sido vinculado con múltiples filtraciones de alto perfil en Argentina, publicó un nuevo volcado de datos que afecta a **UPCNBA** (Unión del Personal Civil de la Nación, Buenos Aires).  

La base expuesta contiene información de **más de 31.000 personas**, con datos personales y financieros extraídos presuntamente desde el portal **tu.upcnba.org**.

El dump incluye archivos `.json` y `.tar` junto con una **API Flask de prueba** para consultar localmente la información.

---

## ¿Qué es UPCNBA?

La UPCNBA es una de las seccionales más relevantes del sindicato nacional de empleados públicos de Argentina. Su plataforma gestiona información de afiliados, sus grupos familiares, datos de contacto y servicios sociales.

---

## ¿Qué información fue comprometida?

De acuerdo con la publicación y las vistas previas compartidas por el atacante, los archivos contienen:

- Nombres completos  
- Correos electrónicos  
- Teléfonos  
- Direcciones personales  
- Fechas de nacimiento  
- Documentos de identidad  
- Información bancaria  
- Relación de familiares por afiliado

Todo esto empaquetado junto a un README y una **interfaz local Flask** para navegar los datos.

---

## ¿Cómo fue publicada?

La base fue subida a servicios de almacenamiento anónimo (`Gofile`) y promocionada en foros de la dark web y canales de Telegram asociados a “aero”. El actor describe el acceso como logrado a través de vulnerabilidades en el dominio **tu.upcnba.org**, aunque no se brindan pruebas técnicas detalladas.

---

## Riesgos asociados

La exposición de información sindical y personal de miles de afiliados plantea riesgos como:

- **Spear phishing dirigido a empleados públicos**  
- **Uso de datos bancarios y personales para fraude financiero**  
- **Exposición de vínculos familiares** que puede facilitar extorsión o chantaje  
- **Impacto reputacional** para la UPCNBA y potencial investigación administrativa

Además, el uso de una API Flask para navegación sugiere la intención de facilitar consultas masivas por parte de terceros malintencionados.

---

## Relación con otras filtraciones

Este nuevo dump refuerza la seguidilla de filtraciones recientes publicadas por “aero”, incluyendo:

- Infraestructura del SPB (Servicio Penitenciario Bonaerense)  
- Base completa de OSSE San Juan  
- Supuesta base con 19 millones de registros vinculados al BCRA

El patrón muestra foco en **entidades estatales, sindicales y servicios públicos**, dejando en evidencia brechas de seguridad comunes y falta de controles básicos.

---

## Conclusión

La filtración de UPCNBA no solo compromete datos individuales: afecta la privacidad de empleados públicos y sus grupos familiares, amplificando riesgos de estafas y ataques dirigidos.

Es imprescindible que entidades sindicales y gubernamentales **refuercen sus prácticas de ciberseguridad**, incluyan auditorías periódicas y eduquen a sus afiliados sobre posibles fraudes.

---

## FAQ

**¿Qué es UPCNBA?**  
Es la Unión del Personal Civil de la Nación, seccional Buenos Aires.

**¿Qué datos contiene esta filtración?**  
Datos personales, bancarios, direcciones y estructura familiar de más de 31.000 afiliados.

**¿Cómo se obtuvo la base?**  
Según el atacante, mediante acceso a **tu.upcnba.org**. No hay confirmación oficial.

**¿Está verificada la autenticidad?**  
La estructura coincide con información verificada en dumps previos de “aero”, pero no hay confirmación institucional.

---

## Disclaimer

Este artículo tiene fines exclusivamente informativos y educativos. No promueve ni distribuye enlaces directos al material expuesto. La información se presenta para concientizar sobre la importancia de fortalecer la ciberseguridad en el ámbito sindical y estatal.
