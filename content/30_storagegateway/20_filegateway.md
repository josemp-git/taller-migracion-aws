---
draft: false
title: 2. Creación de File Gateway
weight: 20
---
En este módulo usted creará un File Gateway. Este gateway le permitirá acceder a los archivos contenidos en su bucket de [**Amazon S3**](https://s3.console.aws.amazon.com/s3/) desde su **Instancia cliente**.

1. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
2. Haga click en **Running instances**.
2. Seleccione la casilla que se encuentra a lado de la **Instancia cliente**.
4. Haga click en **Connect**.
5. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect** para tener acceso a su instancia vía SSH por medio del navegador web.

![Connect (browser-based SSH connection)](/static/images/sg/conectarec2.png)

6. Ejecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
aws ssm get-parameter --name /aws/service/storagegateway/ami/FILE_S3/latest --region us-east-1
:::

::alert[La ejecución de este comando le permite conocer la versión más reciente de la AMI de AWS Storage Gateway (ami-id).]{type="info"}

7. Copie el el valor del parámetro **Value** (sin las comillas) y guárdelo en un archivo de texto.

![File Gateway AMI id](/static/images/sg/ami-id.png)

8. Copie la siguiente URL y sustituya **ami-id** por el valor de **value** que guardó en el archivo de texto (**ami-0123456789XXXXXX**).

:::code{showCopyAction=true showLineNumbers=false language=java}
https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard:ami=ami-id
:::

::alert[Ejemplo de la URL anterior: https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstances:ami=ami-05257a1f7eff27687]{type="info"}

9. Una vez que haya sustituido los valores, copie la URL y péguela en su navegador web. Esta URL lo llevará a desplegar File Gateway como una instancia de Amazon EC2.
10. Ingrese **File Storage Gateway** en el campo de **Name**.
11. Seleccione **m5.xlarge** como tipo de instancia.

![Tipo de instancia](/static/images/sg/instancetypesg.png)

12. Del menú desplegable de **Key pair**, elija **Proceed without a key pair**.

![Proceed without a key pair](/static/images/sg/nokeypair.png)

13. Haga clic en **Edit** en el apartado de **Network settings**.
14. En **VPC**, seleccione la VPC **Lab-Migracion-datos-VPC**.

![VPC](/static/images/sg/requiredvpc.png)

15. Bajo el apartado de **Auto-assign public IP** elija **Enable**.

![Auto-assign public IP - Enable](/static/images/sg/auto-assign-publicip.png)

16. En el apartado de **Firewall (security groups)** seleccione la opción de **Create security group** e ingrese un nombre en el campo de **Security group name** (**storage-gateway-sg**).

![Security group](/static/images/sg/sg.png)

17. Bajo el apartado de **Inbound security groups rules**, elimine la regla que permite el acceso al puerto 22 (SSH) y agregue dos reglas nuevas que habiliten el acceso al puerto TCP 80 (HTTP) desde su dirección IP y el acceso al puerto TCP 2049 (NFS) desde la dirección **IP privada** de la **instancia cliente**:

* Regla 1:
* Type = **HTTP**
* Source type = **My IP**

*Regla 2:
* Type = **NFS**
* Source type = **IP privada de instancia cliente**

![Security group](/static/images/sg/sg2.png)

18. Bajo el apartado de **Configure storage** haga clic en **Add new volume** y agregue un volumen con las siguientes caraceterísticas:

- Capacidad (GiB) = **150**
- Tipo de volumen  EBS = **Magnetic (standard)**

![Volumen adicional](/static/images/sg/storage.png)

19. Haga clic en **Launch instance**.
20. Haga clic en **View all instances**.

![View instances](/static/images/sg/viewinstances.png)

21. De regreso en la consola de EC2, asegúrese de que la instancia de su agente indique **✔ Running** bajo el apartado de **Instance State** y **✔ 2/2 checks passed** bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/sg/statuscheck.png)

22. Seleccione la casilla de **File Storage Gateway**, copie la dirección **IP PÚBLICA**, y guárdela en un archivo de texto.

![IP pública](/static/images/sg/ippublica.png)

23. Haga clic en **Services** y después en **Storage Gateway**.
24. Haga clic en **Get Started** o **Create Gateway** según sea el caso.
25. En el campo de **Gateway name** ingrese **File storage gateway lab**.
26. Seleccione su zona horaria bajo el menu desplegable de **Gateway time zone**.

![Settings](/static/images/sg/sgsettings1.png)

27. Seleccione **Amazon S3 File Gateway** bajo **Gateway type**.

![Settings](/static/images/sg/sgsettings2.png)

28. Selccione **Amazon EC2** bajo **Host platform**.
29. Selecciones **Customize your settings** bajo **Launc EC2 instance**.

![Settings](/static/images/sg/sgsettings3.png)

30. Al final de la página seleccione la opción de **I completed all the steps above and launched the EC2 instance**.
31. Haga clic en **Next**.

![Confirm set up gateway](/static/images/sg/confirm.png)

32. Bajo el apartado de **Service endpoint** seleccione **Publicly accesible**.
33. Bajo el apartado de **Connection options** seleccione IP address.
34. En el campo de **IP address** ingrese la dirección **IP PÚBLICA** que guardó anteriormente.
35 Haga clic en **Next**.

![Endpoint options](/static/images/sg/endpointoptions.png)

36. En la pantalla de **Review and activate** haga clic en **Next**.
37. En la siguiente pantalla seleccione **Cache** en el menú desplegable de **Allocated to** bajo el apartado de **Configure cache storage**.

::alert[Este apartado puede tardar unos minutos en habilitarse.]{type="info"}

![Configure gateway](/static/images/sg/configuregateway.png)

38. Haga clic en **Configure**.
39. Proceda al siguiente módulo.