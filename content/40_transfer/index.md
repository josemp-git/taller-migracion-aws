---
chapter: true
pre: <b>4. </b>
title: Acceso SFTP con AWS Transfer
weight: 40
---
**AWS Transfer** es un servicio totalmente administrado para transferencias de archivos directamente hacia y desde Amazon S3 o Amazon EFS. 

AWS Transfer soporta protocolos estándar tales como

* File Transfer Protocol (SFTP). 
* File Transfer Protocol over SSL (FTPS).
* File Transfer Protocol (FTP).

Con AWS Transfer usted no tiene que comprar y ejecutar sus propios servidores y almacenamiento SFTP, FTPS o FTP para intercambiar datos de forma segura con sus socios y clientes. AWS Transfer administra la infraestructura de archivos por usted y la escala automáticamente. Una vez que sus datos se encuentran en Amazon S3 o Amazon EFS, usted puede procesarlos con los servicios de cómputo, análisis y machine learning de AWS.

![Diagrama](/static/images/tr/diagrama.png)

::video{id="wYaL06kAIxs"}

#### Costos asociados

Este taller genera un costo aproximado de $0.30 USD por cada hora de ejecución una vez que todos los recursos necesarios han sido creados.

No olvide eliminar los recursos creados una vez que haya terminado el laboratorio siguiendo las instrucciones del [módulo 6](/40_transfer/60_eliminar).