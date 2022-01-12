---
chapter: true
pre: <b>1. </b>
title: Migración de servidores con AWS CloudEndure
weight: 10
---
**CloudEndure** es una solución de migración basada en agentes que simplifica agiliza y reduce el costo de la migración a la nube al ofrecer una solución “lift-and-shift” altamente automatizada.

En este laboratorio usted aprenderá a utilizar la herramienta de CloudEndure y llevará cabo todas las tareas necesarias para migrar un servidor hacia el entorno de nube de AWS. Las tares que usted ejecutará en este laboratorio incluyen:

- Crear un usuario IAM con la política adecuada para que el servicio de CloudEndure pueda interactuar con la consola de AWS.
- Crear proyectos de migración dentro de la consola de CloudEndure.
- Instalar el agente de CloudEndure en el servidor que migrará.
- Configurar el blueprint con los parámetros necesarios para poder lanzar su servidor en su nueva ubicación.

Usted también obtendrá su cuenta de CloudEndure con 100,000 licencias de migración sin costo, que podrá seguir utilizando una vez que concluya este laboratorio.

Para efectos de este laboratorio, usted desplegará una instancia Linux con Apache ubicada en la región de N. Virgina que simulará ser un servidor que se encuentra en su centro de datos.
Dentro de esta instancia usted instalará el agente de CloudEndure para llevar a cabo la migración hacia otra VPC dentro de la misma región.

![Architecture Diagram](/static/images/ce/diagrama.png)

::video{id=Joce88i_1Ts}

#### Costos asociados

Este taller genera un costo aproximado de $1.64 USD por cada hora de ejecución una vez que todos los recursos necesarios han sido creados.

No olvide eliminar los recursos creados una vez que haya terminado el laboratorio siguiendo las instrucciones del [módulo 9](/10_cloudendure/90_eliminar).