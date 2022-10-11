---
chapter: true
pre: <b>3. </b>
title: Migración de datos con AWS DataSync
weight: 20
---
**AWS DataSync**, un servicio de transferencia de datos en línea que simplifica, automatiza y acelera la copia de datos hacia y desde los servicios de almacenamiento de AWS. AWS DataSync es un servicio que permite hacer transferencias de datos rápidas ya que utiliza compresión en línea, transferencias paralelas y otras optimizaciones para transferir sus datos de forma eficiente. AWS DataSync es un servicio totalmente administrado que le permite mover los datos desde su centro de datos hacia la región de AWS de su preferencia. Con AWS DataSync usted puede tomar los datos que se encuentren en recursos compartidos con protocolos estándar como NFS y SMB, y moverlos a buckets de Amazon S3 y sistemas de archivos de Amazon EFS y Amazon FSx.

Con un solo servicio usted podrá: migrar los datos de sus aplicaciones a la nube, archivar sus datos fríos y respaldos históricos, habilitar una ubicación de recuperación de sus datos en la nube y mover los datos que se generan en sitio para procesarlos apalancando la amplia oferta de servicios de cómputo, analíticos y machine learning de AWS. Adicionalmente, usted puede combinar este servicio con **AWS Storage Gateway** para tener acceso local a los datos que ya migró a la nube y así aprovechar las ventajas de tener un almacenamiento híbrido en su centro de datos. AWS DataSync representa una opción segura, confiable, rentable y totalmente administrada que le permitirá cumplir con sus objetivos de migración de datos a gran escala y liberar almacenamiento de sus sistemas locales. 

En este laboratorio usted aprenderá como migrar los datos que se encuentran dentro un recurso de compartido por medio de NFS a un bucket de Amazon S3. Este recurso compartido estará montado dentro de una instancia EC2 que fungirá como la ubicación origen de los datos y el bucket de Amazon S3 será la ubicación destino. La información que se migrará es un conjunto de datos históricos en formato CSV con estadísticas de baseball. Al finalizar este laboratorio usted habrá aprendido a:

- Desplegar el Agente de AWS DataSync como una instancia de Amazon EC2.
- Configurar una tarea con sus ubicaciones de origen y destino, y parámetros adicionales.
- Iniciar el proceso de transferencia de datos y conocer los mecanismos de monitoreo disponibles en el servicio.

![Diagrama](/static/images/ds/diagrama.png)

::video{id="jPRquig6Nrw"}

#### Costos asociados

Este taller tiene un costo aproximado de $7.62 USD por cada hora de ejecución una vez que todos los recursos necesarios han sido creados.

No olvide eliminar los recursos creados una vez que haya terminado el laboratorio siguiendo las instrucciones del [módulo 5](/20_datasync/50_eliminar).