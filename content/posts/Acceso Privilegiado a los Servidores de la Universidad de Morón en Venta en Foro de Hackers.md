+++
title = 'Acceso Privilegiado a los Servidores de la Universidad de Morón en Venta en Foro de Hackers'
date = 2024-09-06
draft = false
author = 'Franle'
tags = ['WebShell', 'argentina', 'hackeo', 'universidad', 'moron']
+++

---

## Índice
1. 🔍 [Descripción del Incidente](#descripción-del-incidente)
2. 🛡️ [Información Comprometida](#información-comprometida)
3. 🛑 [Detalles del Anuncio](#detalles-del-anuncio)
4. 🕵️‍♂️ [Análisis del Ataque](#análisis-del-ataque)
5. ⚠️ [Impacto y Riesgos Potenciales](#impacto-y-riesgos-potenciales)
6. 🕵️‍♂️ [Hipótesis del Ataque](#hipótesis-del-ataque)
7. ✅ [Medidas Preventivas y Recomendaciones](#medidas-preventivas-y-recomendaciones)

---

## 🔍 Descripción del Incidente

Un actor malicioso ha puesto a la venta acceso privilegiado a los servidores de la **Universidad de Morón**, una importante institución educativa en Argentina. Este acceso incluye un **WebShell** instalado en el servidor comprometido, y se encuentra disponible en un conocido **foro de venta de datos**, donde los ciberdelincuentes suelen comercializar accesos no autorizados a infraestructuras comprometidas. El atacante ofrece pruebas de acceso y está dispuesto a negociar el precio, que comienza en **260 dólares** pagados en criptomonedas.

---

## 🛡️ Información Comprometida

Según la publicación en este foro de venta de datos, el atacante tiene acceso a un servidor de la Universidad de Morón con el siguiente perfil técnico:

- **Sistema Operativo**: Microsoft Windows
- **Ingresos reportados**: 25 millones de dólares (USD)
- **Tipo de acceso**: WebShell
- **Pago aceptado**: Bitcoin, Monero, Litecoin
- **Fecha de modificación del servidor**: 6 de septiembre, donde se cambió el título del sitio a _"Site Hacked by Schutzstaffel"_.

Además, el atacante advierte que solo venderá este acceso a usuarios de confianza en el foro, para evitar que investigadores de seguridad o agentes federales lo adquieran.

---

## 🛑 Detalles del Anuncio

El anuncio en el foro de venta de datos fue realizado por un usuario bajo el nombre **@Schutzstaffel**, quien afirma tener acceso completo a los servidores de la Universidad de Morón. En el anuncio se pueden leer los siguientes detalles:

- _"Hello, today I'm selling University of Moron webshell access"_
- _"price: 260$ - Negotiable"_ 
- _"Payment method: BTC, Monero, LTC ONLY!"_

El anuncio también incluye una advertencia sobre la venta solo a usuarios reputados, y se ofrece a realizar la transacción a través de un sistema de custodia del foro para mayor seguridad.

![universidad-moron](https://i.ibb.co/0cMgG6F/universidadmoron.png)

---

## 🕵️‍♂️ Análisis del Ataque

Basándonos en la información de **OSINT** recopilada, es posible que los atacantes hayan utilizado herramientas como **Censys** para rastrear la infraestructura de la universidad y descubrir vulnerabilidades explotables. Los datos técnicos recolectados indican que:

1. El servidor de la Universidad de Morón está ejecutando **Apache HTTPD 2.4.58** junto con **PHP 8.2.12**, lo que indica que el servidor está relativamente actualizado, aunque algunas vulnerabilidades podrían seguir presentes si no se han implementado configuraciones de seguridad adecuadas.

2. El 6 de septiembre se realizó un cambio en el título del sitio, que pasó a mostrar _"Site Hacked by Schutzstaffel"_. Antes de este cambio, el servidor exponía un directorio abierto (OpenDir) al público, lo que podría haber facilitado el acceso no autorizado.

3. Se identificó un servicio **AnyDesk** expuesto en el servidor el 16 de agosto, lo que sugiere la posibilidad de que se haya utilizado para controlar remotamente el servidor de manera no autorizada.

---

## ⚠️ Impacto y Riesgos Potenciales

El acceso privilegiado a los servidores de la Universidad de Morón presenta una serie de riesgos significativos:

1. **Explotación de datos internos**: Con el acceso a un WebShell, los atacantes pueden extraer datos sensibles, como información de estudiantes, personal, documentos administrativos, y otros archivos importantes de la universidad.
2. **Escalamiento de privilegios**: Los atacantes pueden intentar escalar sus privilegios en el servidor para obtener acceso completo a otros sistemas dentro de la red de la universidad.
3. **Uso malicioso del servidor**: Los atacantes podrían utilizar el servidor comprometido para lanzar ataques adicionales, alojar contenido malicioso o participar en actividades ilegales desde la infraestructura comprometida.

---

## 🕵️‍♂️ Hipótesis del Ataque

A partir de la información técnica y el análisis de OSINT, se pueden formular las siguientes hipótesis sobre cómo se produjo el ataque:

1. **Exposición del Directorio Abierto (OpenDir)**: El **4 de septiembre**, el servidor estaba configurado con un directorio abierto, lo que podría haber permitido a los atacantes acceder y plantar un WebShell sin mayor dificultad.
   
2. **Exposición de AnyDesk**: La exposición de **AnyDesk**, detectada el **16 de agosto**, es un vector importante. Si el servicio no estaba configurado correctamente, pudo haber facilitado el acceso remoto a los atacantes sin requerir credenciales adicionales.

3. **Vulnerabilidad en Apache o PHP**: Aunque las versiones de **Apache** y **PHP** están actualizadas, no se puede descartar la existencia de configuraciones inseguras o la falta de parches de seguridad en componentes adicionales que podrían haber sido explotados por los atacantes.

4. **Explotación a través de WebShell**: La instalación de un WebShell sugiere que los atacantes lograron explotar una vulnerabilidad no documentada o que utilizaron credenciales robadas, permitiéndoles obtener acceso privilegiado al servidor.

---

## ✅ Medidas Preventivas y Recomendaciones

Para prevenir futuros ataques y mitigar los riesgos actuales, se recomienda a la Universidad de Morón que implemente las siguientes medidas de seguridad:

1. **Revisión de los Logs de Acceso**: Es crucial revisar todos los registros de acceso al servidor, especialmente durante las fechas en que se detectaron los cambios (16 de agosto y 6 de septiembre), para identificar posibles entradas no autorizadas.

2. **Cierre de Servicios Expuestos**: El servicio **AnyDesk** debe ser cerrado o configurado adecuadamente, limitando el acceso únicamente a direcciones IP confiables y mediante autenticación multifactor.

3. **Eliminación de WebShells y Auditoría Completa**: Se debe realizar una auditoría completa del servidor para detectar cualquier WebShell u otros archivos maliciosos instalados por los atacantes. Asimismo, es importante auditar los permisos de archivos y directorios.

4. **Fortalecimiento de la Seguridad en Apache y PHP**: A pesar de estar actualizados, es recomendable endurecer las configuraciones de seguridad de **Apache** y **PHP**, asegurándose de que las configuraciones predeterminadas no sean explotables.

5. **Implementación de Monitoreo Continuo**: Se deben establecer sistemas de monitoreo continuo que puedan alertar al personal de IT sobre cualquier actividad sospechosa o intentos de intrusión en tiempo real.

Estas medidas permitirán reducir el riesgo de que la infraestructura de la Universidad de Morón siga comprometida y evitarán futuros ataques similares.

---

## Disclaimer

La información presentada en este artículo tiene fines puramente informativos y educativos. No se han divulgado datos personales ni información sensible de manera que pueda identificar a individuos específicos. Todos los detalles sensibles han sido debidamente anonimizados para proteger la privacidad de los afectados.

Este blog no promueve ni respalda ninguna actividad ilegal, y se esfuerza por concienciar sobre la importancia de la ciberseguridad y la protección de datos personales. Cualquier uso indebido de la información aquí compartida es responsabilidad exclusiva del individuo que lo lleve a cabo.

---
