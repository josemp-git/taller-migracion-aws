---
draft: false
title: 2. Creación de File Gateway
weight: 20
---
En este módulo usted creará un File Gateway utilizando una de las instancias que fueron creadas cuando lanzó la plantilla de [**AWS CloudFormation**](https://console.aws.amazon.com/cloudformation). Este gateway le permitirá acceder a los archivos contenidos en su bucket de [**Amazon S3**](https://s3.console.aws.amazon.com/s3/) desde su instancia local.

1. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **CloudShell**.
2. Ejecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
aws ssm get-parameter --name /aws/service/storagegateway/ami/FILE_S3/latest --region us-east-1
:::

::alert[La ejecución de este comando le permite conocer la versión más reciente de la AMI de AWS Storage Gateway (ami-id).]{type="info"}

3. Copie el resultado de la ejecución del comando anterior y guárdelo en un archivo de texto.
4. Copie la siguiente URL y sustituya el valor de **ami-id** por el valor de **value** resultado de la ejecución del comando del paso anterior:

:::code{showCopyAction=true showLineNumbers=false language=java}
https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstances:ami=**ami-id**
:::

5. Una vez que haya sustituido los valores, copie la URL y péguela en su navegador web. Esta URL lo llevará a desplegar File Gateway como una instancia de Amazon EC2.
6. Ingrese **File Storage Gateway** en el campo de **Name**.
7. Seleccione **m5.xlarge** como tipo de instancia.

![Tipo de instancia](/static/images/sg/instancetypesg.png)

8. Del menú desplegable de **Key pair**, elija **Proceed without a key pair**.

![Proceed without a key pair](/static/images/sg/nokeypair.png)

9. Haga clic en **Edit** en el apartado de **Network settings**.
10. En **VPC**, seleccione la VPC **Lab-Migracion-datos-VPC**.

![VPC](/static/images/sg/requiredvpc.png)

11. Bajo el apartado de **Auto-assign public IP** elija **Enable**.

![Auto-assign public IP - Enable](/static/images/sg/auto-assign-publicip.png)

12. En el apartado de **Firewall (security groups)** seleccione la opción de **Create security group** e ingrese un nombre en el campo de **Security group name** (**storage-gateway-sg**).

![Security group](/static/images/sg/sg.png)

13. Bajo el apartado de **Inbound security groups rules**, elimine la regla que permite el acceso al puerto 22 (SSH) y agregue dos reglas nuevas que habilite el acceso al puerto TCP 80 (HTTP) desde su dirección IP y al acceso al puerto TCP 2049 (NFS) desde la dirección IP privada de la instancia cliente:

* Regla 1:
* Type = **HTTP**
* Source type = **My IP**

*Regla 2:
* Type = **NFS**
* Source type = **IP privada de instancia cliente**

![Security group](/static/images/sg/sg2.png)

14. Bajo el apartado de **Configure storage** haga clic en **Add new volume** y agregue un volumen con las siguientes caraceterísticas:

- Capacidad (GiB) = **150**
- Tipo de volumen  EBS = **Magnetic (standard)**

![Volumen adicional](/static/images/sg/storage.png)

15. Haga clic en **Launch**.
16. Haga clic en **View all instances**.

![View instances](/static/images/sg/viewinstances.png)

17. De regreso en la consola de EC2, asegúrese de que la instancia de su agente indique **✔ Running** bajo el apartado de **Instance State** y **✔ 2/2 checks passed** bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/sg/statuscheck.png)

18. Seleccione la casilla de **File Storage Gateway**, copie la dirección **IP PÚBLICA**, y guárdela en un archivo de texto.

![IP pública](/static/images/sg/ippublica.png)

19. Haga clic en **Services** y después en **Storage Gateway**.
20. Haga clic en **Get Started** o **Create Gateway** según sea el caso.
21. En el campo de **Gateway name** ingrese **File storage gateway lab**.
22. Seleccione su zona horaria bajo el menu desplegable de **Gateway time zone**.
23. Seleccione **Amazon S3 File Gateway** bajo **Gateway type**.
24. Selccione **Amazon EC2** bajo **Host platform**.

![Create gateway](/static/images/sg/creategateway.png)

25. Al final de la página seleccione la opción de **I completed all the steps above and launched the EC2 instance**.
26. Haga clic en **Next**.

![Confirm set up gateway](/static/images/sg/confirm.png)

27. Bajo el apartado de **Service endpoint** seleccione **Publicly accesible**.
28. Bajo el apartado de **Connection options** seleccione IP address.
29. En el campo de **IP address** ingrese la dirección **IP PÚBLICA** que guardó anteriormente.
30. Haga clic en **Next**.

![Endpoint options](/static/images/sg/endpointoptions.png)

31. En la pantalla de **Review and activate** haga clic en **Next**.
32. En la siguiente pantalla seleccione **Cache** en el menú desplegable de **Allocated to** bajo el apartado de **Configure cache storage**.

![Configure gateway](/static/images/sg/configuregateway.png)

::alert[Este apartado puede tardar unos minutos en habilitarse.]{type="info"}

33. Haga clic en **Configure**.
34. Proceda al siguiente módulo.