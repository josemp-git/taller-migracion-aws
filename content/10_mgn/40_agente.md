---
draft: false
title: 4. Instalación del Agente de Replicación
weight: 40
---
AWS Application Migration Service es una solución de migración a la nube basada en un **Agente de Replicación** que le permite migrar cargas de trabajo que se ejecuten en versiones soportadas de sistemas operativos Windows y Linux. A continuación, instalará el Agente de Replicación de AWS MGN en la instancia que migrará.

Antes de instalar el agente, conozca los detalles del servidor que migrará.

1. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2**.
2. Haga clic en **Instances (running)**.
3. Seleccione la casilla de la instancia **Servidor Web**.
4. Copie la dirección **IP pública (Public IPv4 address)** que se encuentra bajo el apartado de **Details** y guárdela en un archivo de texto ya que la utilizará más adelante.

![Details - Copy Public IP Address](/static/images/mgn/publicipaddress.png)

5. Haga clic en el apartado de **Security**, junto a **Details**.
6. Haga clic el grupo de seguridad de la instancia **sg-0xxxxxxxxxxxxxxxx (MGN Lab SG)**

![Security - Security groups](/static/images/mgn/securitygroups.png)

7. Haga clic en **Edit Inbound rules**

![Edit Inbound rules](/static/images/mgn/editinboundrules.png)

8. Para la regla de acceso por medio de **HTTP**, cambie el origen permitido **(Source)** de **Custom** por **My IP**.

![Source - Custom source](/static/images/mgn/customsource.png)

9. Haga clic en **Save rules**.

![Source - My IP](/static/images/mgn/httpmyip.png)

::alert[Esto permitirá que la instancia **Servidor Web** pueda ser accedida por HTTP desde su dirección IP.]{type="info"}

10. Tome la dirección **IP pública** que guardó anteriormente y péguela en una pestaña de su navegador. Encontrará el siguiente mensaje:

![Este servidor será migrado utilizando AWS Application Migration Service](/static/images/mgn/seramigrado.png)

 
11. Regrese la consola de Amazon EC2 y seleccione de nuevo la casilla de la instancia **Servidor Web**.
12. Haga clic en el botón de **Connect**.

![Connect to Web Server](/static/images/mgn/connect1.png)

13. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect** para tener acceso a su instancia vía SSH por medio del navegador web.

![Connect to Web Server](/static/images/mgn/connect2.png)

14. Ingrese el siguiente comando en el CLI del servidor para descargar el instalador del Agente de Replicación:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo wget -O ./aws-replication-installer-init.py https://aws-application-migration-service-us-east-1.s3.amazonaws.com/latest/linux/aws-replication-installer-init.py
:::

![Descargar agente](/static/images/mgn/agentdownload.png)

15. Ejecute el siguiente comando para instalar el agente, sustituyendo **ACCESS-KEY** y **SECRET-ACCESS-KEY** por el access key y secret access key que descargó previamente al crear el usuario IAM:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo python3 aws-replication-installer-init.py --region us-east-1 --no-prompt --aws-access-key-id ACCESS-KEY --aws-secret-access-key SECRET-ACCESS-KEY
:::

La instalación del agente tomará un par de minutos y al finalizar mostrará el siguiente mensaje: **The AWS Replication Agent was successfully installed.**

![Agent Installation](/static/images/mgn/agentinstallation.png)

::alert[Para más información acerca de como agregar servidores origen, puede consultar la documentación disponible: [Adding source servers](https://docs.aws.amazon.com/mgn/latest/ug/adding-servers.html)]{type="info"}

16. Haga clic en **Services** y posteriormente seleccione el servicio de **AWS Application Migration Service** para regresar a la consola de AWS MGN. Podrá verificar que el servidor ya aparece en la consola después de haber instalado el agente, y que la replicación ha comenzado. Usted podrá monitorear el progreso de la replicación bajo el apartado de **Data replication status**.

![Source servers](/static/images/mgn/sourceservers.png)

17. Proceda al siguiente módulo en lo que se termina el proceso de replicación.