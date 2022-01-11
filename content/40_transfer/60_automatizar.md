---
draft: false
title: 'OPCIONAL: 6. Automatizar el encendido y apagado del servidor SFTP'
weight: 60
---
Automatizar el encendido y apagado de su servidor SFTP en el horario de su elección puede ser algo muy conveniente desde el punto de vista de costos. Esto puede ser de gran utilidad en un proceso de migración en el cual solamente se migran datos durante una ventana de tiempo predeterminada. Esta automatización se puede lograr mediante el uso de funciones [AWS Lambda](https://aws.amazon.com/lambda/), reglas de [Amazon EventBridge](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/WhatIsCloudWatchEvents.html), y el [AWS SDK para Python (Boto3)](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html).

Para habilitar esta automatización en su ambiente, ejecute los pasos descritos a continuación.

#### 1. Despliegue de plantilla de CloudFormation

Esta plantilla desplegará dos funciones AWS Lambda escritas en Python 3.8 y el rol necesario para su correcta ejecución:

* **StartTransferSFTPServer** - función para encendido.
* **StopTransferSFTPServer** - función para apagado.

1. Haga clic en **Services** y después en **CloudFormation** que se encuentra bajo la categoría de **Management & Governance** (también puede teclear CloudFormation en el campo de búsqueda).
2. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.
3. En el campo de **Amazon S3 URL** ingrese la siguiente URL: 

```
http://taller-migracion-dev.s3.amazonaws.com/40_transfer/StartStopTransferSFTPServer.yaml
```

4. Haga clic en **Next**.
5. En el campo de **Stack name** escriba **auto-on-off-lambda**.
6. En el campo de **server** ingrese el **Server ID** de su servidor SFTP.
7. Haga clic en **Next**.
8. En la siguiente pantalla haga clic de nuevo en **Next**.
9. Seleccione la casilla de **"I acknowledge that AWS CloudFormation might create IAM resources"**.
10. Haga clic en **Create stack**.

Después de un minuto, el status de la plantilla cambiará a **<span style="color\:green">✔ CREATE_COMPLETE</span>**, indicando que esta se ha desplegado satisfactoriamente.

#### 2. Configuración de la regla en Amazon EventBridge

A continuación, usted configurará una regla en el servicio de Amazon EventBridge que le permitirá calendarizar la ejecución de las funciones AWS Lambda que encenderán y apagarán su servidor SFTP en el horario de su conveniencia.

11. Haga clic en **Services** y posteriormente seleccione el servicio de **Amazon EventBridge**.
12. Ingrese **IniciarServidorSFTP** en el campo de **Name**.
13. En el recuadro de **Define pattern** seleccione **Schedule** y posteriormente seleccione **Cron expression**.
14. En el campo de **Cron expression** ingrese lo siguiente:

```
0 21 * * ? *
```

16. En el recuadro de **Select Targets** seleccione **Lambda function** bajo la opción de **Target**.
17. En el menú desplegable de **Function** seleccione la función con el nombre **auto-on-off-lambda-StartTransferSFTPServer**.
18. Haga clic en **Create rule**.


Lo anterior habrá creado una regla para ejecutar la función AWS Lambda que encenderá su servidor SFTP todos los días a las 21:00 (UTC).

22. Repita los pasos para crear la regla, pero esta vez seleccione la función **auto-on-off-lambda-StopTransferSFTPServer** como **Target** e ingrese lo siguiente en el campo de **Cron expression**:

```
0 08 * * ? *
```

Esta regla ejecutará la función AWS Lambda que apagará su servidor SFTP todos los días a las 08:00 (UTC). Para más información acerca de como programar expresiones para reglas , consulte la [documentación disponible](https://docs.aws.amazon.com/es_es/AmazonCloudWatch/latest/events/ScheduledEvents.html).