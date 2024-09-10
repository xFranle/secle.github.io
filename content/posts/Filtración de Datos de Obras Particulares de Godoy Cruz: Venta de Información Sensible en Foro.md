+++
title = 'Filtración de Datos de Obras Particulares de Godoy Cruz: Venta de Información Sensible en Foro'
date = 2024-09-09
draft = false
author = 'Franle'
tags = ['Godoy Cruz', 'argentina', 'hackeo']
+++

---

## Índice
1. 🔍 [Descripción del Incidente](#-descripci%C3%B3n-del-incidente)
2. 🛡️ [Información Comprometida](#-informaci%C3%B3n-comprometida)
3. 🛑 [Detalles del Anuncio](#-detalles-del-anuncio)
4. 🕵️‍♂️ [Análisis del Ataque](#-an%C3%A1lisis-del-ataque)
5. ⚠️ [Impacto y Riesgos Potenciales](#-impacto-y-riesgos-potenciales)
6. 🕵️‍♂️ [Hipótesis del Ataque](#-hip%C3%B3tesis-del-ataque)
7. ✅ [Medidas Preventivas y Recomendaciones](#-medidas-preventivas-y-recomendaciones)

---

## 🔍 Descripción del Incidente

Un actor malicioso ha puesto a la venta un **dump de datos** proveniente de **Obras Particulares de Godoy Cruz**, una plataforma gubernamental especializada en arquitectura, construcción y prevención de incendios en Argentina. La información filtrada incluye planos detallados de construcciones privadas, junto con respuestas de la **API** que contienen correos electrónicos y detalles de los usuarios de la plataforma. El actor asegura tener más documentos internos que pueden ser negociados de manera privada.

El hacker, además, acusa a la Municipalidad de Godoy Cruz de ignorar la seguridad de sus ciudadanos y no haber tomado medidas tras el ataque, lo que ha motivado la publicación de esta información en un foro clandestino.

---

## 🛡️ Información Comprometida

El dump de datos en venta incluye la siguiente información clave:

- **Planos arquitectónicos y de prevención de incendios** de múltiples edificios privados.
- Detalles técnicos de **instalaciones eléctricas** en construcciones.
- Respuestas de la **API** que contienen **correos electrónicos** y **detalles de los usuarios** de la plataforma.
- Documentación adicional interna de la plataforma, disponible bajo negociación privada.

El actor malicioso ha puesto estos datos a la venta por **5 créditos** en un foro de hackers, lo que sugiere un acceso amplio a información sensible de la plataforma.

---

## 🛑 Detalles del Anuncio

El anuncio en el foro de hackers fue realizado por un usuario que se especializa en la venta de datos de plataformas gubernamentales. En el anuncio se detallan los siguientes puntos clave:

- _"Hello. Today we bring you a server dump for Obras Particulares Godoy Cruz in Argentina, specialized in Architecture, Construction, Fire Prevention."_
- _"The dump contains multiple plans from different private buildings with electrical, fire prevention and architectural details, as well as JSON API responses containing emails and user details."_
- _"We have more information including internal files and more documents which can be negotiated via PM (we do not answer to new users)."_

El lote de datos, según el anuncio, tiene un precio de **5 créditos** en el foro, lo que sugiere que está siendo ofrecido a un precio relativamente bajo en comparación con otros dumps similares, pero que contiene información sensible de alta relevancia.

![godoy-cruz2024](https://i.ibb.co/1zZxND4/godoy-cruz.png)

---

## 🕵️‍♂️ Análisis del Ataque

Basándonos en la información proporcionada en el foro y en el análisis del ataque, es probable que los atacantes hayan aprovechado una vulnerabilidad en la **API** de Obras Particulares de Godoy Cruz para obtener acceso no autorizado a los planos y detalles de los usuarios. A continuación, algunos elementos clave del ataque:

1. **Explotación de la API**: El hecho de que los datos obtenidos incluyan respuestas de la API sugiere que los atacantes pudieron haber realizado un ataque de **API scraping** o haber accedido directamente a los endpoints no protegidos. Esto les habría permitido extraer grandes cantidades de información sin que se detectaran actividades anómalas.

2. **Acceso a planos privados**: Los planos de los edificios, junto con detalles técnicos de instalaciones eléctricas y de prevención de incendios, sugieren un acceso profundo a la base de datos interna de la plataforma. Esto podría haberse realizado mediante inyecciones SQL o la explotación de credenciales robadas.

3. **Acceso a datos personales**: La venta de correos electrónicos y datos de usuarios sugiere que los atacantes pudieron acceder a datos sensibles de individuos y empresas que interactúan con la plataforma, poniendo en riesgo su privacidad y seguridad.

---

## ⚠️ Impacto y Riesgos Potenciales

La venta de este dump de datos tiene serias implicaciones para la seguridad de los ciudadanos y empresas cuyas construcciones privadas han sido comprometidas. A continuación, algunos de los riesgos más graves:

1. **Explotación de datos sensibles**: Los planos de edificios privados podrían ser utilizados para fines maliciosos, como robos planificados o actividades ilícitas dentro de las propiedades afectadas.
   
2. **Riesgos de privacidad**: La exposición de los datos personales y correos electrónicos de los usuarios podría dar lugar a campañas de **phishing** y otros ataques dirigidos.

3. **Inseguridad física**: La publicación de detalles técnicos sobre prevención de incendios y sistemas eléctricos podría comprometer la seguridad física de los edificios involucrados.

4. **Daño reputacional**: La plataforma gubernamental queda expuesta a una pérdida de confianza pública, ya que la falta de acción tras el ataque podría ser vista como una negligencia en la protección de los datos de los ciudadanos.

## 🕵️‍♂️ Hipótesis del Ataque

A partir de la información recopilada, se pueden formular las siguientes hipótesis sobre cómo se produjo el ataque:

1. **Vulnerabilidad en la API**: Es probable que los atacantes hayan explotado una vulnerabilidad en la API de Obras Particulares de Godoy Cruz, lo que les permitió acceder a datos sensibles como planos y detalles de usuarios.

2. **Credenciales Robadas**: Los atacantes podrían haber utilizado credenciales robadas o haber accedido a cuentas privilegiadas de empleados de la plataforma, lo que les permitió extraer información de la base de datos interna.

3. **Inseguridad en el manejo de archivos**: La posibilidad de que los planos y documentos internos hayan estado almacenados sin una adecuada protección sugiere que los atacantes podrían haber accedido directamente a los archivos, sin necesidad de explotar vulnerabilidades más complejas.

4. **Explotación de permisos mal configurados**: Si la plataforma no tenía correctamente configurados los permisos de acceso a los datos, los atacantes podrían haber obtenido acceso de manera sencilla, sin requerir técnicas avanzadas.

---

## ✅ Medidas Preventivas y Recomendaciones

Para prevenir futuros ataques y mitigar los riesgos actuales, se recomienda a Obras Particulares de Godoy Cruz que implemente las siguientes medidas de seguridad:

1. **Revisión exhaustiva de la API**: Es crucial que se realice una auditoría completa de la API utilizada por la plataforma, identificando y cerrando cualquier vulnerabilidad que pueda estar exponiendo datos sensibles.

2. **Implementación de autenticación reforzada**: Se debe reforzar la autenticación en la plataforma, implementando mecanismos como autenticación multifactor (MFA) para evitar accesos no autorizados a cuentas privilegiadas.

3. **Cifrado de datos sensibles**: Los datos sensibles, incluidos los planos arquitectónicos y los detalles de usuarios, deben ser almacenados y transmitidos utilizando cifrado de extremo a extremo para evitar su exposición en caso de una brecha de seguridad.

4. **Monitoreo constante de la actividad de la plataforma**: Implementar sistemas de monitoreo en tiempo real que alerten sobre cualquier actividad sospechosa, especialmente en endpoints de la API.

5. **Capacitación en ciberseguridad para empleados**: El personal que gestiona la plataforma debe recibir formación continua en ciberseguridad, para asegurar que manejan los datos sensibles de manera segura y conocen los procedimientos adecuados ante un ataque.

Estas medidas ayudarán a mitigar los efectos del ataque y a proteger mejor la información sensible almacenada en la plataforma, evitando futuros incidentes similares.

---

## Disclaimer

La información presentada en este artículo tiene fines puramente informativos y educativos. No se han divulgado datos personales ni información sensible de manera que pueda identificar a individuos específicos. Todos los detalles sensibles han sido debidamente anonimizados para proteger la privacidad de los afectados.

Este blog no promueve ni respalda ninguna actividad ilegal, y se esfuerza por concienciar sobre la importancia de la ciberseguridad y la protección de datos personales. Cualquier uso indebido de la información aquí compartida es responsabilidad exclusiva del individuo que lo lleve a cabo.

---
