+++
title = 'Ransomware QILIN ataca a DACAS Argentina y amenaza con filtrar 190GB de datos'
date = 2025-03-10
draft = false
author = 'Franle'
tags = ['ransomware', 'argentina', 'DACAS', 'QILIN']
+++

## Índice

1. [Introducción: Resumen del ataque](#introducción-resumen-del-ataque)
2. [Perfil de DACAS Argentina](#perfil-de-dacas-argentina)
3. [¿Quiénes son los atacantes? El grupo QILIN y su conexión con Corea del Norte](#quienes-son-los-atacantes-el-grupo-qilin-y-su-conexión-con-corea-del-norte)
4. [Detalles del ataque: ¿Qué se ha filtrado hasta ahora?](#detalles-del-ataque-qué-se-ha-filtrado-hasta-ahora)
5. [Consecuencias y riesgos potenciales](#consecuencias-y-riesgos-potenciales)
6. [Medidas de seguridad y lecciones aprendidas](#medidas-de-seguridad-y-lecciones-aprendidas)
7. [Conclusión](#conclusión)
8. [FAQ](#faq)
9. [Disclaimer](#disclaimer)

---

![DACAS-2025](https://i.ibb.co/hJ5C1X5H/Screenshot-2025-03-10-111102.png)

## Introducción: Resumen del ataque

El grupo de ransomware **QILIN** ha reivindicado un **ciberataque contra DACAS Argentina**, un mayorista tecnológico de valor agregado con presencia en varios países de América Latina.

Según información publicada en su **sitio en la dark web**, los atacantes aseguran haber exfiltrado **190GB de datos confidenciales**, incluyendo documentos financieros y datos personales. Han fijado el **17 de marzo de 2025** como la fecha límite antes de publicar la información robada si no se paga un rescate.

Este ataque pone en evidencia la vulnerabilidad de las empresas tecnológicas frente a amenazas avanzadas como **el ransomware de doble extorsión**, una táctica cada vez más común en el panorama del cibercrimen.

---

## Perfil de DACAS Argentina

**DACAS** es una empresa fundada en **1993**, con presencia en **más de 12 países** y más de **3,720 socios comerciales** en América Latina. Se especializa en la distribución de **soluciones tecnológicas de valor agregado**, abarcando áreas como **ciberseguridad, infraestructura y networking**.

Al ser un mayorista tecnológico, **DACAS maneja información sensible** tanto de sus clientes como de sus proveedores, lo que la convierte en un objetivo atractivo para ataques cibernéticos.

---

## ¿Quiénes son los atacantes? El grupo QILIN y su conexión con Corea del Norte

QILIN es un **grupo de ransomware de habla rusa**, también conocido como **Agenda**, que opera bajo un modelo de **Ransomware-as-a-Service (RaaS)**.

Sin embargo, recientemente **Microsoft identificó que piratas informáticos norcoreanos han comenzado a usar QILIN en ataques dirigidos**. Un grupo de **APT vinculado a Corea del Norte**, conocido como **Moonstone Sleet**, ha implementado este ransomware en ataques limitados desde **febrero de 2025**.

Moonstone Sleet ha sido previamente identificado usando:

- **Malware troyanizado**
- **Juegos fraudulentos para distribuir ransomware**
- **Falsas ofertas de empleo en LinkedIn y Telegram para engañar a víctimas**
- **Ataques de doble extorsión en organismos gubernamentales**

QILIN ha estado **activo desde 2022**, pero ganó notoriedad en **junio de 2024** al atacar a **Synnovis**, un proveedor de servicios médicos del Reino Unido.

---

## Detalles del ataque: ¿Qué se ha filtrado hasta ahora?

El grupo QILIN publicó en su **sitio de filtraciones en la dark web** una muestra de los datos robados a DACAS, que incluyen:

📂 **Documentos financieros** de la empresa  
📂 **Información personal** de empleados y clientes  
📂 **Datos internos confidenciales** sobre operaciones comerciales  

En sus declaraciones, QILIN amenaza con publicar la totalidad de la información el **17 de marzo de 2025** si DACAS no cumple con sus demandas.

---

## Consecuencias y riesgos potenciales

- 🔴 **Filtración de datos críticos**: Si la información se hace pública, podría comprometer las relaciones comerciales de DACAS y afectar su reputación en la industria.
- 🔴 **Uso de credenciales robadas**: Si los atacantes obtuvieron accesos privilegiados, podrían revender las credenciales en mercados clandestinos o usarlas en futuros ataques.
- 🔴 **Ataques en cadena**: Proveedores, socios y clientes de DACAS también podrían verse afectados, ya que los datos filtrados podrían ser utilizados en ataques dirigidos (spear phishing, BEC, etc.).

---

## Medidas de seguridad y lecciones aprendidas

Para mitigar el impacto y evitar futuros ataques, las organizaciones deben adoptar un enfoque **proactivo** en ciberseguridad:

✅ **Habilitar autenticación multifactor (MFA)** en todos los accesos críticos  
✅ **Monitorear accesos no autorizados** en redes y servidores  
✅ **Implementar segmentación de red** para evitar movimientos laterales  
✅ **Realizar copias de seguridad cifradas** con almacenamiento fuera de línea  
✅ **Entrenar a empleados y socios en buenas prácticas de seguridad**  

---

## Conclusión

El ataque a DACAS demuestra que los grupos de ransomware siguen evolucionando y estableciendo nuevas alianzas con actores avanzados, como **APT norcoreanos**.

Este incidente subraya la importancia de que empresas tecnológicas y de infraestructura crítica **refuercen sus medidas de seguridad y adopten estrategias de ciberdefensa adaptativas**.

Con **190GB de datos en riesgo de ser filtrados**, DACAS enfrenta un desafío importante para contener el daño y evitar mayores repercusiones.

---

## FAQ

### 📌 1. ¿Qué es el ransomware de doble extorsión?
Es un tipo de ataque en el que los criminales **cifran los archivos** de la víctima y, además, **roban datos confidenciales**, amenazando con publicarlos si no se paga un rescate.

### 📌 2. ¿Cómo se propagó el ransomware en este caso?
Aunque no se ha confirmado el vector exacto, ataques previos de QILIN han aprovechado:
- **Credenciales comprometidas en VPN sin MFA**
- **Correos de phishing con archivos maliciosos**
- **Accesos remotos inseguros en servidores expuestos**

### 📌 3. ¿Cuál es la relación de QILIN con Corea del Norte?
Investigadores de Microsoft han detectado que un **grupo APT norcoreano llamado Moonstone Sleet** ha utilizado QILIN en ataques recientes.

### 📌 4. ¿Cómo pueden protegerse las empresas contra ataques de ransomware?
- **Implementando MFA en todos los accesos**
- **Realizando backups seguros**
- **Monitoreando actividad sospechosa en la red**
- **Educando a empleados sobre riesgos de phishing y ataques de ingeniería social**

---

## Disclaimer

*Este artículo se basa en información obtenida de fuentes públicas y no se hace responsable por la veracidad de los datos filtrados por terceros. Se recomienda a las partes afectadas tomar medidas de ciberseguridad y consultar con expertos en la materia (como Secle Solutions 😉).*
