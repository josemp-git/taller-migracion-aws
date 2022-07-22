---
chapter: true
pre: <b>2. </b>
title: Migración de servidores con AWS Application Migration Service
weight: 15
---
**AWS Application Migration Service (AWS MGN)** es una solución de migración basada en agentes que simplifica, agiliza y reduce el costo de la migración a la nube al ofrecer una solución “lift-and-shift” altamente automatizada.

En este laboratorio usted aprenderá a utilizar la herramienta de AWS MGN y llevará cabo todas las tareas necesarias para migrar un servidor hacia el entorno de nube de AWS. Las tareas que usted ejecutará en este laboratorio incluyen:

- Crear un usuario IAM con la política adecuada para generar las credenciales necesarias.
- Crear la plantilla de configuración de replicación
- Instalar el agente de AWS MGN en el servidor que migrará.
- Configurar la plantilla de Amazon EC2 con los parámetros necesarios para poder lanzar su servidor en su nueva ubicación.
- Probar su servidor como instancia Amazon EC2 previo a la migración final.

Para efectos de este laboratorio, usted desplegará una instancia Linux con Apache ubicada en la región de N. Virgina que simulará ser un servidor que se encuentra en su centro de datos.
Dentro de esta instancia usted instalará el agente de AWS MGN para llevar a cabo la migración hacia otra VPC dentro de la misma región.

![Architecture Diagram](/static/images/ce/diagrama-mgn.png)

::video{id="KVV5Hd70Uc8"}