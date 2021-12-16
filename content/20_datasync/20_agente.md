---
draft: false
pre: <b style="color:#fff;">2. </b>
title: Creación del agente
weight: 20
---
En este módulo, usted desplegará el agente de AWS DataSync en una instancia de Amazon EC2.

1. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **CloudShell**.
2. Ejecute el siguiente comando, sustituyendo el valor de **$region** por la región en la que está trabajando:

```
aws ssm get-parameter --name /aws/service/datasync/ami --region $region
```
::alert[Si usted se encuentra trabajando en la región de N. Virginia, el comando se ejecutaría así:]{type="info"}

```
aws ssm get-parameter --name /aws/service/datasync/ami --region us-east-1
```

::alert[La ejecución de este comando le permite conocer la versión más reciente de la AMI de AWS DataSync (ami-id).]{type="info"}

3. Copie el resultado de la ejecución del comando anterior y guárdelo en un archivo de texto.
4. Copie la siguiente URL y sustituya los valores de **source-file-systemregion** por la región en la que va a desplegar su agente y el valor de **ami-id** por el valor de **value** resultado de la ejecución del comando del paso anterior:

```
https://console.aws.amazon.com/ec2/v2/home?region=source-file-systemregion#LaunchInstanceWizard\:ami=ami-id
```

::alert[Si usted se encuentra trabajando en la región de N. Virginia, la URL quedaría así:]{type="info"}

```
https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard\:ami=ami-057d036cc57e1af91
```

5. Una vez que haya sustituido los valores, copie la URL y péguela en su navegador web. Esta URL lo llevará a desplegar el agente de AWS DataSync como una instancia de Amazon EC2.
6. Seleccione **m5.2xlarge** como tipo de instancia.
7. Haga clic en **Next: Configure instance details**.
8. En Network, seleccione la VPC **Migracion-datos-VPC**.
9. Haga clic en **Next: Add storage**.
10. En la pantalla de **Add Storage** mantenga los valores predeterminados, no es necesario agregar almacenamiento adicional.
11. Haga clic en **Next: Add tags**.
12. Agregue la etiqueta **Name** con el valor **Agente AWS DataSync**.
13. Haga clic en **Next: Configure Security Group**.
14. Habilite el acceso al puerto TCP 80 (HTTP) desde su dirección IP y deshabilite el acceso al puerto 22 (SSH) ya que este acceso no es necesario.

![Puerto TCP 80 - HTTP](/static/images/ds/puerto80.png)

15. Haga clic en **Review and Launch**.
16. Haga clic en **Launch**.
17. Seleccione el key pair que creó anteriormente y haga clic en **Launch Instances**.
18. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **EC2**.
19. Asegúrese de que la instancia de su agente indique **<span style="color\:green">✔ Running**</span> bajo el apartado de **Instance State** y **<span style="color\:green">✔ 2/2 checks passed**</span> bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/ds/statuscheck.png)

20. Seleccione la casilla del agente de AWS DataSync, copie las direcciones IP pública y privada, y guárdelas en un archivo de texto.
21. Seleccione la casilla de la instancia **Servidor NFS** y modifique el grupo de seguridad para permitir el acceso por el puerto TCP 2049 (NFS) desde la dirección IP privada del agente de AWS DataSync.

![Habilitar puerto 2049](/static/images/ds/puerto2049.png)

21. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **DataSync**.
22. Haga clic en **Agents** en el menú lateral izquierdo.
23. Haga clic en el botón de **Create agent**.
24. En el campo de **Agent adress** ingrese la dirección IP pública del agente de AWS DataSync.
25. Haga clic en **Get key**.
26. Ingrese **Agente AWS DataSync** en el campo de **Agent name**.
27. Haga clic en **Create agent**.
28. Haga clic en **Agents** en el menú lateral izquierdo y compruebe que su agente se encuentra activo (**Status = Online**).


![Agente en línea](/static/images/ds/agenteenlinea.png)

29. Proceda al siguiente módulo.