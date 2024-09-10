+++
title = 'Hacker Vende Datos de Alcance Planes: 264,000 Números de Teléfono Expuestos'
date = 2024-09-10
draft = false
author = 'Franle'
tags = ['Venta de datos', 'argentina', 'hackeo', 'Datos personales']
+++

---

## Índice
1. 🔍 [Descripción del Incidente](#-descripci%C3%B3n-del-incidente)
2. 🛡️ [Sitios Web Comprometidos](#-informaci%C3%B3n-comprometida)
3. 🛑 [Detalles del Anuncio](#-detalles-del-anuncio)
4. 🕵️‍♂️ [Análisis del Ataque](#-an%C3%A1lisis-del-ataque)
5. ⚠️ [Impacto y Riesgos Potenciales](#-impacto-y-riesgos-potenciales)
6. 🕵️‍♂️ [Hipótesis del Ataque](#-hip%C3%B3tesis-del-ataque)
7. ✅ [Medidas Preventivas y Recomendaciones](#-medidas-preventivas-y-recomendaciones)

---

## 🔍 Descripción del Incidente

Un actor malicioso ha puesto a la venta un listado de clientes de la empresa Alcance Planes, una plataforma de servicios y productos en Argentina. Este listado incluye 264,000 registros que contienen nombres completos, números de teléfono y ciudades de residencia de los clientes. Los datos han sido extraídos en formato CSV y están disponibles en un foro clandestino por solo 2 créditos.

El actor malicioso, identificado como 108111118101, está ofreciendo este conjunto de datos a un precio bajo, lo que sugiere una intención de rápida distribución o un ataque dirigido a una gran cantidad de usuarios.

---

## 🛡️ Información Comprometida

El dump de datos a la venta incluye los siguientes elementos clave:

- **Nombres completos** de los clientes.
- **Números de teléfono** celulares de los individuos.
- **Ciudades de residencia** de los afectados, organizadas por provincias o localidades.
- **264,000 entradas** en total, obtenidas del sitio web **alcanceplanes.com.ar**.

El formato del archivo es CSV, facilitando su manejo para realizar ataques dirigidos, como campañas de phishing o fraudes telefónicos.

---

## 🛑 Detalles del Anuncio

El anuncio fue realizado por el actor malicioso **108111118101** en un foro de hackers, donde se detallan las siguientes características del dump de datos:

- _"Alcanceplanes.com.ar clients.csv ~264K lines name, phone, location"_
- El archivo contiene aproximadamente **264,000 registros**, y está siendo vendido por **2 créditos** en el foro.

La publicación también incluye una muestra de los datos filtrados, en la cual se pueden observar nombres de personas, números de teléfono y localidades específicas.

![alcance-planes2024](https://i.ibb.co/3Fd0YZ5/alcance-planes.png)

---

## 🕵️‍♂️ Análisis del Ataque

Dado que no hay demasiada información técnica disponible, se puede inferir que el ataque pudo haber involucrado una filtración desde la base de datos de la plataforma alcanceplanes.com.ar. A continuación, algunos posibles vectores de ataque:

1. **Explotación de la base de datos**: Es probable que el actor malicioso haya accedido a la base de datos de clientes, posiblemente a través de una vulnerabilidad en la seguridad del sitio o utilizando credenciales robadas. El hecho de que los datos estén organizados en un archivo CSV sugiere que fueron extraídos directamente desde la base de datos de clientes de la empresa.

2. **Explotación de una API mal configurada**: Si la plataforma de Alcance Planes cuenta con una API para gestionar los datos de sus clientes, los atacantes podrían haber explotado alguna vulnerabilidad en dicha API, permitiendo el acceso a una gran cantidad de registros.

3. **Fuga de datos interna**: Otra posibilidad es que la filtración haya sido el resultado de un insider o un empleado que tuvo acceso legítimo a los datos y decidió extraerlos para su venta en el foro de hackers.

---

## ⚠️ Impacto y Riesgos Potenciales

El impacto de esta filtración puede ser significativo para los clientes de Alcance Planes, ya que la información filtrada incluye detalles personales y de contacto que pueden ser utilizados para diversos tipos de ataques:

1. **Ataques de phishing y fraudes telefónicos**: Los atacantes pueden utilizar la información de contacto para llevar a cabo campañas de phishing o intentos de fraude telefónico, utilizando los nombres completos y las localidades para personalizar sus ataques.
2. **Robo de identidad**: Con nombres y números de teléfono, los atacantes podrían intentar obtener información adicional sobre las víctimas para llevar a cabo robos de identidad.
3. **Daño reputacional para Alcance Planes**: La filtración de una base de datos tan grande puede tener un impacto severo en la reputación de la empresa, ya que los clientes pueden perder la confianza en su capacidad para proteger sus datos personales.

---

## 🕵️‍♂️ Hipótesis del Ataque

A partir de la información disponible, se pueden formular las siguientes hipótesis sobre cómo se produjo el ataque:

1. **Acceso no autorizado a la base de datos**: El actor malicioso podría haber obtenido acceso a la base de datos de clientes a través de una vulnerabilidad en el sistema de seguridad de la plataforma, lo que le permitió extraer la información en formato CSV.

2. **Explotación de vulnerabilidad en la API**: Otra posible vía de ataque es que se haya utilizado una vulnerabilidad en la API de Alcance Planes para extraer masivamente los datos de los clientes.

3. **Fuga interna**: Existe la posibilidad de que la filtración haya sido facilitada por alguien dentro de la organización con acceso legítimo a los datos, lo que explicaría cómo los registros fueron obtenidos con tal nivel de detalle.

---

## ✅ Medidas Preventivas y Recomendaciones

Para prevenir futuros ataques y mitigar los riesgos actuales, se recomienda a Alcance Planes que implemente las siguientes medidas de seguridad:

1. **Revisión y Auditoría de la Base de Datos**: Se debe realizar una auditoría exhaustiva de la base de datos para identificar cualquier acceso no autorizado y determinar cómo se pudo haber extraído la información.

2. **Endurecimiento de la Seguridad en la API**: Si la plataforma utiliza una API para gestionar los datos de clientes, es fundamental realizar una revisión exhaustiva de los permisos y configuraciones para asegurarse de que no haya endpoints vulnerables.

3. **Monitoreo y Registro de Accesos**: Implementar monitoreo constante de los accesos a la base de datos y la API, y revisar los registros para detectar cualquier actividad sospechosa en tiempo real.

4. **Notificación a los Afectados**: Es importante que Alcance Planes notifique a los clientes sobre la filtración de sus datos y proporcione recomendaciones para protegerse de posibles ataques de phishing o fraudes telefónicos.

5. **Capacitación Interna en Seguridad**: El personal de la empresa debe recibir capacitación continua en buenas prácticas de ciberseguridad para garantizar que los datos de los clientes sean tratados de manera segura y responsable.

---

## Disclaimer

La información presentada en este artículo tiene fines puramente informativos y educativos. No se han divulgado datos personales ni información sensible de manera que pueda identificar a individuos específicos. Todos los detalles sensibles han sido debidamente anonimizados para proteger la privacidad de los afectados.

Este blog no promueve ni respalda ninguna actividad ilegal, y se esfuerza por concienciar sobre la importancia de la ciberseguridad y la protección de datos personales. Cualquier uso indebido de la información aquí compartida es responsabilidad exclusiva del individuo que lo lleve a cabo.

---
