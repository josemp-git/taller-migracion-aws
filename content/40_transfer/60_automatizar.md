---
draft: false
title: '6. Automatizar el encendido y apagado del servidor SFTP (OPCIONAL)'
weight: 60
---
Automatizar el encendido y apagado de su servidor SFTP en el horario de su elección puede ser algo muy conveniente desde el punto de vista de costos. Esto puede ser de gran utilidad en un proceso de migración en el cual solamente se migran datos durante una ventana de tiempo predeterminada. Esta automatización se puede lograr mediante el uso de funciones [AWS Lambda](https://aws.amazon.com/lambda/), reglas de [Amazon EventBridge](https://docs.aws.amazon.com/AmazonCloudWatch/latest/events/WhatIsCloudWatchEvents.html), y el [AWS SDK para Python (Boto3)](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html).

Para habilitar esta automatización en su ambiente, ejecute los pasos descritos a continuación.

#### 1. Despliegue de plantilla de CloudFormation

Esta plantilla desplegará dos funciones AWS Lambda escritas en Python 3.8 y el rol necesario para su correcta ejecución:

* **StartTransferSFTPServer** - función para encendido.
* **StopTransferSFTPServer** - función para apagado.

1. Descargue esta :link[plantilla de CloudFormation]{href="/static/40_transfer/StartStopTransferSFTPServer.yaml" action=download}.
2. Haga clic en **Services** y después en **CloudFormation**.
3. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.

![CloudFormation](/static/images/tr/cloudformation2.png)

4. Seleccione **Upload a template file** y cargue la plantilla de CloudFormation que descargó anteriormente.

![CloudFormation](/static/images/tr/cloudformation3.png)

5. Haga clic en **Next**.
6. En el campo de **Stack name** escriba **auto-on-off-lambda**.
7. En el campo de **server** ingrese el **Server ID** de su servidor SFTP.
9. Haga clic en **Next**.
9. En la siguiente pantalla haga clic de nuevo en **Next**.
10. Seleccione la casilla de **"I acknowledge that AWS CloudFormation might create IAM resources"**.
11. Haga clic en **Create stack**.

Después de un minuto, el status de la plantilla cambiará a **✔ CREATE_COMPLETE**, indicando que esta se ha desplegado satisfactoriamente.

#### 2. Configuración de la regla en Amazon EventBridge

A continuación, usted configurará una regla en el servicio de Amazon EventBridge que le permitirá calendarizar la ejecución de las funciones AWS Lambda que encenderán y apagarán su servidor SFTP en el horario de su conveniencia.

12. Haga clic en **Services** y posteriormente seleccione el servicio de **Amazon EventBridge**.
13. Haga clic en **Create rule**.
14. Ingrese **IniciarServidorSFTP** en el campo de **Name**.
15. En **Rule type** seleccione **Schedule** y haga clic en **Next**.

![Rule detail](/static/images/tr/ruledetail.png)

16. En el campo de **Cron expression** ingrese los siguientes valores:

:::code{showCopyAction=true showLineNumbers=false language=java}
0 21 * * ? *
:::

![Schedule pattern](/static/images/tr/schedule.png)



17. Haga clic en **Next**.
18. En **Target types** seleccione **AWS service**.
19. En el menú desplegable de **Select a target** seleccione **Lambda function**.
20. En el menú desplegable de **Function** seleccione la función con el nombre **auto-on-off-lambda-StartTransferSFTPServer**.

![Select target](/static/images/tr/target1.png)

21. Haga clic en **Next**.
22. Haga clic de nuevo en **Next**.
23. Haga clic en **Create rule**.

::alert[Lo anterior habrá creado una regla para ejecutar la función AWS Lambda que encenderá su servidor SFTP todos los días a las 21:00 UTC.)]{type="info"}

24. Repita los pasos anteriores para crear otra regla, pero esta vez seleccione la función **auto-on-off-lambda-StopTransferSFTPServer** como **Target** e ingrese lo siguiente en el campo de **Cron expression**:

:::code{showCopyAction=true showLineNumbers=false language=java}
0 08 * * ? *
:::

Esta regla ejecutará la función AWS Lambda que apagará su servidor SFTP todos los días a las 08:00 (UTC). Para más información acerca de como programar expresiones para reglas , consulte la [documentación disponible](https://docs.aws.amazon.com/es_es/AmazonCloudWatch/latest/events/ScheduledEvents.html).