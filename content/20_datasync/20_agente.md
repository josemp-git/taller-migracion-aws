---
draft: false
title: 2. Creación del agente
weight: 20
---
En este módulo, usted desplegará el agente de AWS DataSync en una instancia de Amazon EC2.

1. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **CloudShell**.
2. Ejecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
aws ssm get-parameter --name /aws/service/datasync/ami --region us-east-1
:::

::alert[La ejecución de este comando le permite conocer la versión más reciente de la AMI de AWS DataSync (ami-id).]{type="info"}

3. Copie el resultado de la ejecución del comando anterior y guárdelo en un archivo de texto.
4. Copie la siguiente URL y sustituya el valor de **ami-id** por el valor de **value** resultado de la ejecución del comando del paso anterior:

:::code{showCopyAction=true showLineNumbers=false language=java}
https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard:ami=ami-id
:::

5. Una vez que haya sustituido los valores, copie la URL y péguela en su navegador web. Esta URL lo llevará a desplegar el agente de AWS DataSync como una instancia de Amazon EC2.
6. Ingrese **Agente AWS DataSync** en el campo de **Name**
7. Del menú desplegable de **Instance type**, seleccione **m5.2xlarge**.
8. Del menú desplegable de **Key pair**, seleccione el key pair que creó previamente.
9. Haga clic en **Edit** en el apartado de **Network settings**.
10. En **VPC**, seleccione la VPC **Migracion-datos-VPC**.
11. En el apartado de **Firewall (security groups)** seleccione la opción de **Create security group** y cree una regla nueva que habilite el acceso al puerto TCP 80 (HTTP) desde su dirección IP: 

* Type = **HTTP**
* Source type = **My IP**

12. Elimine la regla que permite el acceso al puerto 22 (SSH) ya que en este acceso no se necesita.
13. En el apartado de **Configure storage** mantenga los valores predeterminados (no es necesario agregar almacenamiento adicional).
14. Haga clic en **Launch**.
15. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **EC2**.
16. Asegúrese de que la instancia de su agente indique **<span style="color\:green">✔ Running**</span> bajo el apartado de **Instance State** y **<span style="color\:green">✔ 2/2 checks passed**</span> bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/ds/statuscheck.png)

17. Seleccione la casilla del agente de AWS DataSync, copie las direcciones IP pública y privada, y guárdelas en un archivo de texto.
18. Seleccione la casilla de la instancia **Servidor NFS** y modifique el grupo de seguridad para permitir el acceso por el puerto TCP 2049 (NFS) desde la dirección IP privada del agente de AWS DataSync.

![Habilitar puerto 2049](/static/images/ds/puerto2049.png)

19. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **DataSync**.
20. Haga clic en **Agents** en el menú lateral izquierdo.
21. Haga clic en el botón de **Create agent**.
22. En el campo de **Agent adress** ingrese la dirección IP pública del agente de AWS DataSync.
23. Haga clic en **Get key**.
24. Ingrese **Agente AWS DataSync** en el campo de **Agent name**.
25. Haga clic en **Create agent**.
26. Haga clic en **Agents** en el menú lateral izquierdo y compruebe que su agente se encuentra activo (**Status = Online**).


![Agente en línea](/static/images/ds/agenteenlinea.png)

27. Proceda al siguiente módulo.