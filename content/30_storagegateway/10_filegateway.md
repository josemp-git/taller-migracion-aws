---
draft: false
title: 1. Creación de S3 File Gateway
weight: 10
---
En este módulo usted creará un Amazon S3 File Gateway. Amazon S3 File Gateway le permitirá acceder a los archivos contenidos en su bucket de [**Amazon S3**](https://s3.console.aws.amazon.com/s3/) desde su instancia **Cliente NFS** por medio del protocolo NFS.

1. Haga clic en **Services** y después en **EC2**.
2. Haga clic en **Key pairs** bajo el apartado de **Network & Security** en el menú lateral izquierdo.
3. Haga clic en **Create key pair** en la esquina superior derecha.
4. Ingrese :code[s3filegateway]{showCopyAction=true} en el campo de **Name**.
5. Seleccione los siguientes valores:
* Key pair type = **RSA**
* Private key file format = **.pem**
6. Haga clic en **Create key pair**.

![Create key pair](/static/images/sg/keypair.png)

7. Haga clic en **Services** y después en **Storage Gateway**.
8. Haga clic en **Create Gateway**.
9. Ingrese :code[S3 File gateway]{showCopyAction=true} en el campo de **Gateway name**.
10. Seleccione su zona horaria bajo el menu desplegable de **Gateway time zone**.
11. Seleccione **Amazon S3 File Gateway** bajo **Gateway type**.

![Settings](/static/images/sg/sgsettings1.png)

12. Bajo el apartado de **Platform options** seleccione las siguientes opciones:

* Host platform = **Amazon EC2**
* Launch EC2 instance = **Use default settings**
* Virtual private cloud (VPC) network = **MigrationLabVPC**
* VPC subnet = **Source Subnet**
* Key pair = **s3filegateway**

![Settings](/static/images/sg/sgsettings2.png)

13. Haga clic en **Launch instance**.

::alert[Este proceso tomará aproximadamente dos minutos en completarse.]{type="info"}

14. Haga clic en **Close** una vez que la instancia haya sido lanzada exitosamente (**The instance was launched successfully**).
15. Haga clic en **Next**.

![Confirm set up gateway](/static/images/sg/confirm.png)

16. Bajo el apartado de **Connection options** seleccione **IP address** (La dirección IP de la instancia ya se habrá agregado automáticamente).
17. Bajo el apartado de **Service endpoint** seleccione **Publicly accesible**.

![Endpoint options](/static/images/sg/endpointoptions.png)

18. Haga clic en **Next**.
19. Haga clic en **Activate gateway**.

20. En la siguiente pantalla seleccione **Cache** en el menú desplegable de **Allocated to** bajo el apartado de **Configure cache storage**.

::alert[Este apartado puede tardar unos minutos en habilitarse.]{type="info"}

![Configure gateway](/static/images/sg/configuregateway.png)

21. Haga clic en **Configure**.
22. Proceda al siguiente módulo.