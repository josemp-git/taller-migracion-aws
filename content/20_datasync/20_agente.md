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
3. Ingrese :code[Agente AWS DataSync]{showCopyAction=true} en el campo de **Name**.
4. Del menú desplegable de **Instance type**, seleccione **m5.2xlarge**.

![Tipo de instancia](/static/images/ds/instancetype.png)

5. Del menú desplegable de **Key pair**, elija **Proceed without a key pair**.

![Proceed without a key pair](/static/images/ds/nokeypair.png)

6. Bajo el apartado de **Network settings** seleccione los siguientes parámetros:

* VPC = **MigrationLabVPC**
* Subnet = **Source Subnet**
* Auto-assign public IP = **Enable**

![VPC](/static/images/ds/networksettings.png)

7. En el apartado de **Firewall (security groups)** seleccione la opción de **Create security group** e ingrese :code[datasync-agente-sg]{showCopyAction=true} en el campo de **Security group name**.

![Create securigy group](/static/images/ds/createsg.png)

8. Bajo el apartado de **Inbound security groups rules**, elimine la regla que permite el acceso al puerto 22 (SSH) y agregue una regla nueva que habilite el acceso al puerto TCP 80 (HTTP) desde su dirección IP: 

* Type = **HTTP**
* Source type = **My IP**

![New rule](/static/images/ds/reglanueva.png)

9. Haga clic en **Launch instance**.
10. Haga clic en **View all instances**.
11. De regreso en la consola de EC2, espere a que la instancia de su agente indique **✔ Running** bajo el apartado de **Instance State** y **✔ 2/2 checks passed** bajo el apartado de **Status check**.

![Status check passed (2/2)](/static/images/ds/statuscheck.png)

::alert[Este paso puede tomar unos minutos.]{type="info"}

12. Seleccione la casilla del agente de AWS DataSync, copie la dirección **IP pública (Public IPv4 address)** y guárdela en un archivo de texto.

![IP pública (Public IPv4 address)](/static/images/ds/direccionip.png)

13. Dentro de la consola de AWS, haga clic en **Services** y diríjase al servicio de **DataSync**.
14. Haga clic en **Transfer data**.
15. Haga clic en **Agents** en el menú lateral izquierdo.

![Menu - Agents)](/static/images/ds/agentsmenu.png)

16. Haga clic en el botón de **Create agent**.
17. Seleccione **Public service endpoints in US East (N. Virginia)** en el menú desplegable de **Endpoint type**.

![Public Endpoints)](/static/images/ds/publicendpoint.png)

18. Bajo el apartado de **Activation key** selccione la opción de **Automatically get the activation key from your agent**.
19. En el campo de **Agent address** ingrese la dirección **IP pública** del agente de AWS DataSync que creó anteriormente.
20. Haga clic en **Get key**.

![Activation key)](/static/images/ds/activationkey.png)

21. Ingrese :code[Agente AWS DataSync]{showCopyAction=true} en el campo de **Agent name**.
22. Haga clic en **Create agent**.
23. Haga clic en **Agents** en el menú lateral izquierdo y compruebe que su agente se encuentra activo (**Status = Online**).

![Agente en línea](/static/images/ds/agenteenlinea.png)

24. Proceda al siguiente módulo.