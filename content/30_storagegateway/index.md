---
chapter: true
pre: <b>4. </b>
title: Acceso local a los datos con AWS Storage Gateway
weight: 30
---
**AWS Storage Gateway** es un servicio de almacenamiento híbrido que permite que las aplicaciones que se encuentran en sitio puedan utilizar almacenamiento prácticamente ilimitado de la nube de AWS, de manera transparente y sin contratiempos. AWS Storage Gateway no requiere cambios en sus aplicaciones y se integra fácilmente ya que utiliza protocolos de comunicación y almacenamiento estándar como HTTPS (HTTP sobre SSL/TLS) para comunicación con la nube, así como SMB (Server Message Block) y NFS (Network File System) para el acceso a los datos almacenados. Mediante AWS Storage Gateway, usted puede ampliar su capacidad local de almacenamiento mientras reduce y simplifica la infraestructura de su centro de datos o de sus oficinas remotas.

Nuestros clientes alrededor del mundo utilizan AWS Storage Gateway para ampliar sus capacidades de respaldo y archivado, así como para reemplazar sistemas de almacenamiento en sitio por almacenamiento localizado en la nube. Muchos clientes también utilizan Storage Gateway para colocar sus datos en la nube y poder analizarlos y transformarlos aprovechando los servicios de Analítica de Datos disponibles en AWS.

En este laboratorio usted aprender como desplegar AWS Storage Gateway en su modalidad de **File Gateway** dentro de un ambiente de AWS que simulará ser su Centro de Datos. Al final de este laboratorio usted habrá aprendido a:

- Desplegar y configurar un File Gateway como instancia Amazon EC2.
- Crear un recurso compartido en la consola de AWS Storage Gateway utilizando un bucket de Amazon S3 como almacenamiento.
- Montar un recurso compartido gestionado por AWS Storage Gateway en una instancia Linux.

![Diagrama](/static/images/sg/diagrama.png)

::video{id="DPyc0q4MYsM"}

#### Costos asociados

Este taller genera un costo aproximado de $14.50 USD por cada hora de ejecución una vez que todos los recursos necesarios han sido creados.

No olvide eliminar los recursos creados una vez que haya terminado el laboratorio siguiendo las instrucciones del [módulo 5](/30_storagegateway/50_eliminar).