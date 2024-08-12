+++
title = 'Filtración de Datos: "Viaje de Egresados Argentina 2023" Expone Información Sensible de Estudiantes y Padres'
date = 2024-08-12
draft = false
author = 'Franle'
tags = ['filtracion', 'argentina', 'hackeo']
+++

---

## 📋 Índice
- 🔍 [Descripción del Incidente](#🔍-descripción-del-incidente)
- 🛡️ [Información Comprometida](#🛡️-información-comprometida)
- 🛑 [Detalles del Anuncio](#🛑-detalles-del-anuncio)
- 🕵️‍♂️ [Análisis de la Filtración](#🕵️‍♂️-análisis-de-la-filtración)
- ⚠️ [Impacto y Riesgos Potenciales](#⚠️-impacto-y-riesgos-potenciales)
- ✅ [Medidas Preventivas y Recomendaciones](#✅-medidas-preventivas-y-recomendaciones)

---

## 🔍 Descripción del Incidente

Recientemente, un actor de amenazas conocido como **"netcut"** compartió una base de datos titulada **"Viaje de Egresados Argentina 2023"**. Esta filtración incluye **10,800 entradas** con información sensible de estudiantes y sus padres. La base de datos contiene datos como **correos electrónicos, hashes de contraseñas**, y detalles sobre **instituciones educativas y niveles académicos**.

Es importante señalar que la información filtrada no especifica a qué empresa de viajes de egresados pertenece ni si se trata de los viajes ofrecidos gratuitamente por el Estado.

---

## 🛡️ Información Comprometida

La información filtrada se divide en dos archivos CSV que contienen una amplia gama de datos personales. Entre los más relevantes se incluyen:

### Archivo 1:
- **Nombre y Apellido del Estudiante**
- **DNI**
- **CUIL/CUIT**
- **Fecha de Nacimiento**
- **Estado de Inscripción**
- **Información del Familiar a Cargo** (nombre, apellido, celular, documento)

### Archivo 2:
- **DNI del Estudiante**
- **Hash de Contraseña**
- **Correo Electrónico**
- **Número de Celular**
- **Género**
- **Institución Educativa**

---

## 🛑 Detalles del Anuncio

El actor de amenazas "netcut" publicó lo siguiente en relación a la filtración:

_"This data has been leaked by me. 2 csv files that contain data from 'viaje de egresados 2023' (argentinian) students."_

Este mensaje confirma la responsabilidad del ataque y la filtración de datos, los cuales están relacionados con estudiantes argentinos que participaron en el viaje de egresados del año 2023.

![egresados-2023](https://i.ibb.co/9Gmtmxr/Argentina-Egresados.png)

---

## 🕵️‍♂️ Análisis de la Filtración

Aunque no se han revelado detalles específicos sobre cómo ocurrió la filtración, podemos hacer algunas hipótesis basadas en el tipo de datos comprometidos y los métodos de ataque comunes en estos casos:

1. **Vulnerabilidad en la Aplicación Web o Base de Datos**: Dado que la base de datos incluye información detallada y estructurada, es posible que los atacantes hayan explotado una vulnerabilidad en una aplicación web o un sistema de gestión de bases de datos. Un ataque de **SQL Injection** podría haber permitido a los ciberdelincuentes extraer la información directamente desde la base de datos.

2. **Acceso No Autorizado a través de Credenciales Robadas**: Si los atacantes obtuvieron credenciales de acceso (quizás a través de phishing o de un ataque de fuerza bruta), podrían haber accedido directamente a los sistemas internos para descargar los archivos CSV.

3. **Compromiso Interno o Error Humano**: En algunos casos, las filtraciones de datos ocurren debido a errores humanos o a la acción maliciosa de un empleado interno. Es posible que alguien con acceso legítimo haya compartido estos archivos intencionalmente o por descuido.

4. **Falta de Cifrado y Protección de Datos**: La ausencia de cifrado en los datos almacenados podría haber facilitado la extracción de la información en texto plano, exponiendo datos sensibles como hashes de contraseñas y números de identificación.

---

## ⚠️ Impacto y Riesgos Potenciales

La filtración de esta base de datos tiene varias implicaciones graves:

- **Fraude de Identidad**: Los datos personales expuestos pueden ser utilizados para crear identidades falsas o acceder a cuentas bancarias.
- **Phishing**: Con los correos electrónicos y otros datos personales, los ciberdelincuentes pueden diseñar ataques de phishing altamente personalizados.
- **Extorsión**: La información sobre familiares a cargo podría ser explotada para amenazas o intentos de extorsión.

---

## ✅ Medidas Preventivas y Recomendaciones

Para evitar futuras filtraciones de datos como la del "Viaje de Egresados Argentina 2023", es crucial que las instituciones educativas y organizaciones relacionadas implementen fuertes medidas de seguridad. A continuación, se detallan algunas recomendaciones clave:

- **Cifrado de Datos Sensibles**: Asegurarse de que toda la información personal esté cifrada, tanto en reposo como en tránsito.
- **Auditorías de Seguridad**: Realizar auditorías periódicas para identificar y corregir vulnerabilidades en las bases de datos y sistemas.
- **Autenticación Multifactor (MFA)**: Implementar autenticación multifactor para acceder a sistemas críticos, reduciendo significativamente el riesgo de acceso no autorizado.
- **Capacitación en Ciberseguridad**: Educar constantemente al personal sobre las mejores prácticas en ciberseguridad, incluyendo cómo detectar intentos de phishing y proteger sus contraseñas.
- **Protección contra Vulnerabilidades Conocidas**: Mantener los sistemas actualizados y aplicar parches de seguridad rápidamente para evitar que se exploten vulnerabilidades conocidas.

Estas medidas resaltan la importancia de adoptar un enfoque proactivo en la ciberseguridad, protegiendo tanto a las instituciones como a los datos personales de los individuos.

---

## Disclaimer

La información presentada en este artículo tiene fines puramente informativos y educativos. No se han divulgado datos personales ni información sensible de manera que pueda identificar a individuos específicos. Todos los detalles sensibles han sido debidamente anonimizados para proteger la privacidad de los afectados.

Este blog no promueve ni respalda ninguna actividad ilegal, y se esfuerza por concienciar sobre la importancia de la ciberseguridad y la protección de datos personales. Cualquier uso indebido de la información aquí compartida es responsabilidad exclusiva del individuo que lo lleve a cabo.

---
