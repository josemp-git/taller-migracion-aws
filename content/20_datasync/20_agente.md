---
draft: false
title: 2. Creación del agente
weight: 20
---
En este módulo, usted desplegará el agente de AWS DataSync en una instancia de Amazon EC2.

1. Copie la siguiente URL y sustituya **ami-id** por el valor de **value** que guardó en el archivo de texto (**ami-0123456789XXXXXX**):

:::code{showCopyAction=true showLineNumbers=false language=java}
https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard:ami=ami-id
:::

::alert[Ejemplo de la URL anterior: https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#LaunchInstanceWizard:ami=ami-06dffdffeed1ce3c9.]{type="info"}

2. Una vez que haya sustituido los valores, copie la URL y péguela en su navegador web. Esta URL lo llevará a desplegar el agente de AWS DataSync como una instancia de Amazon EC2.
3. Ingrese **Agente AWS DataSync** en el campo de **Name**.
4. Del menú desplegable de **Instance type**, seleccione **m5.2xlarge**.

![Tipo de instancia](/static/images/ds/instancetype.png)

5. Del menú desplegable de **Key pair**, elija **Proceed without a key pair**.

![Proceed without a key pair](/static/images/ds/nokeypair.png)

6. Haga clic en **Edit** en el apartado de **Network settings**.
7. En **VPC**, seleccione la VPC **Lab-Migracion-datos-VPC**.

![VPC](/static/images/ds/requiredvpc.png)

8. Bajo el apartado de **Auto-assign public IP** elija **Enable**.

![Auto-assign public IP - Enable](/static/images/ds/auto-assign-publicip.png)

9. En el apartado de **Firewall (security groups)** seleccione la opción de **Create security group** e ingrese un nombre en el campo de **Security group name** (**datasync-agente-sg**).

![Create securigy group](/static/images/ds/createsg.png)

10. Bajo el apartado de **Inbound security groups rules**, elimine la regla que permite el acceso al puerto 22 (SSH) y agregue una regla nueva que habilite el acceso al puerto TCP 80 (HTTP) desde su dirección IP: 

* Type = **HTTP**
* Source type = **My IP**

![New rule](/static/images/ds/reglanueva.png)

11. Haga clic en **Launch**.
12. Haga clic en **View all instances**.

![View all instances](/static/images/ds/viewallinstances.png)

13. De regreso en la consola de EC2, asegúrese de que la instancia de su agente indique **✔ Running** bajo el apartado de **Instance State** y **✔ 2/2 checks passed** bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/ds/statuscheck.png)

::alert[Este paso puede tomar unos minutos.]{type="info"}

14. Seleccione la casilla del agente de AWS DataSync, copie la dirección **IP PÚBLICA** y guárdela en un archivo de texto.

![IPs)](/static/images/ds/direccionip.png)

15. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **DataSync**.
16. Haga clic en **Agents** en el menú lateral izquierdo.
17. Haga clic en el botón de **Create agent**.
18. Seleccione **Public service endpoints** in US East (N. Virginia).

![Public Endpoints)](/static/images/ds/publicendpoint.png)

19. Bajo el apartado de **Activation key** selccione la opción de **Automatically get the activation key from your agent**.
20. En el campo de **Agent aDdress** ingrese la dirección IP **PÚBLICA** del agente de AWS DataSync.
21. Haga clic en **Get key**.

![Activation key)](/static/images/ds/activationkey.png)

22. Ingrese **Agente AWS DataSync** en el campo de **Agent name**.
23. Haga clic en **Create agent**.
24. Haga clic en **Agents** en el menú lateral izquierdo y compruebe que su agente se encuentra activo (**Status = Online**).

![Agente en línea](/static/images/ds/agenteenlinea.png)

25. Proceda al siguiente módulo.