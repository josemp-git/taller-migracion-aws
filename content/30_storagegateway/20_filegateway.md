---
draft: false
pre: <b style="color:#fff;">2. </b>
title: Creación de File Gateway
weight: 20
---
En este módulo usted creará un File Gateway utilizando una de las instancias que fueron creadas cuando lanzó la plantilla de [**AWS CloudFormation**](https://console.aws.amazon.com/cloudformation). Este gateway le permitirá acceder a los archivos contenidos en su bucket de [**Amazon S3**](https://s3.console.aws.amazon.com/s3/) desde su instancia local.

1. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **CloudShell**.
2. Ejecute el siguiente comando, sustituyendo el valor de **$region** por la región en la que está trabajando:

```
aws ssm get-parameter --name /aws/service/storagegateway/ami/FILE_S3/latest --region $region
```
::alert[Si usted se encuentra trabajando en la región de N. Virginia, el comando se ejecutaría así:]{type="info"}

```
aws ssm get-parameter --name /aws/service/storagegateway/ami/FILE_S3/latest --region us-east-1
```

::alert[La ejecución de este comando le permite conocer la versión más reciente de la AMI de AWS de AWS Storage Gateway (ami-id).]{type="info"}

3. Copie el resultado de la ejecución del comando anterior y guárdelo en un archivo de texto.
4. Copie la siguiente URL y sustituya los valores de **source-file-systemregion** por la región en la que va a desplegar su agente y el valor de **ami-id** por el valor de **value** resultado de la ejecución del comando del paso anterior:

```
https://console.aws.amazon.com/ec2/v2/home?region=source-file-systemregion#LaunchInstanceWizard\:ami=ami-id
```

::alert[Si usted se encuentra trabajando en la región de N. Virginia, la URL quedaría así:]{type="info"}

```
https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard\:ami=ami-056f71af0f2ca2daa
```

5. Una vez que haya sustituido los valores, copie la URL y péguela en su navegador web. Esta URL lo llevará a desplegar File Gateway como una instancia de Amazon EC2.
6. Seleccione **m5.xlarge** como tipo de instancia.
7. Haga clic en **Next: Configure instance details**.
8. En Network, seleccione la VPC **Migracion-datos-VPC**.
9. Haga clic en **Next: Add storage**.
10. En la pantalla de **Add Storage**  haga clic en **Add new volume** y agregue un volumen EBS adicional con las siguientes características:

- Size (GiB) = **150**
- Volume Type = **Magnetic (standard)**
- Delete on termination = ✅ 

![Agregar volúmen](/static/images/sg/agregarvolumen.png)

11. Haga clic en **Next: Add tags**.
12. Agregue la etiqueta **Name** con el valor **File Gateway**.
13. Haga clic en **Next: Configure Security Group**.
14. Habilite el acceso al puerto TCP 80 (HTTP) desde su dirección IP y al puerto TCP 2049 desde la dirección IP privada de la instancia cliente.

![Agregar volúmen](/static/images/sg/sg.png)

15. Haga clic en **Review and Launch**.
16. Haga clic en **Launch**.
17. Seleccione el key pair que creó anteriormente y haga clic en **Launch Instances**.
18. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **EC2**.
19. Asegúrese de que la instancia de su agente indique **<span style="color\:green">✔ Running</span>** bajo el apartado de **Instance State** y **<span style="color\:green">2/2 checks passed</span>** bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/sg/statuscheck.png)

20. Seleccione la casilla de **File Gateway**, copie la dirección IP pública, y guárdela en un archivo de texto.
21. Haga clic en **Services** y después en **Storage Gateway**.
22. Haga clic en **Get Started** o **Create Gateway** según sea el caso.
23. En **Select gateway type** seleccione **Amazon S3 File Gateway** y haga clic en **Next**.
24. En **Select host platform** seleccione **Amazon EC2** y haga clic en **Next**.
25. En **Service endpoint** seleccione **Public** y haga clic en **Next**.
26. En **Connect to gateway** ingrese la IP de **StorageGatewayPublicIp** en el campo de **IP address** y haga clic en **Next**.
27. En **Activate Gateway** seleccione la zona horaria de su localidad en el menú desplegable de **Gateway time zone**.
28. Ingrese un nombre para su Gateway en el campo de **Gateway name** (ejemplo: **File Gateway Lab**) .
29. Haga clic en **Activate Gateway**.
30. Haga clic en **Exit**.
31. Haga clic en **Gateways** en el menú lateral izquierdo.
32. Seleccione la casilla del **Gateway** que acaba de crear y asegúrese que el status de su Gateway sea **<span style="color\:red">! Running</span>**.
33. Haga clic en el menú desplegable de **Actions** y después en **Edit local disks** (para ejecutar este paso probablemente tenga que esperar unos minutos a que el gateway termine de crearse por completo).
34. Seleccione **Cache** del menú desplegable de **Allocated to**.
35. Haga clic en **Save**.
36. Corrobore que el status del gateway ahora sea **<span style="color\:green">✔ Running**</span>.
37. Proceda al siguiente módulo.