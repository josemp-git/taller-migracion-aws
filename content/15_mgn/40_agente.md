---
draft: false
title: 4. Instalación del Agente de Replicación
weight: 40
---
AWS Application Migration Service es una solución de migración a la nube basada en un **Agente de Replicación** que le permite migrar cargas de trabajo que se ejecuten en versiones soportadas de sistemas operativos Windows y Linux. A continuación, instalará el Agente de Replicación de AWS MGN en la instancia que migrará.

Antes de instalar el agente, conozca los detalles del servidor que migrará.

1. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2**.
2. Haga clic en **EC2 Dashboard** y después en **Instances (running)**.
3. Seleccione la casilla de la instancia **Servidor Linux**. En el apartado de **Details** podrá ver información como VPC, subred y segmento de red en el que se encuentra su servidor, así como las direcciones IP pública y privada.

4. Copie la dirección IP pública (Public IPv4 address) que se encuentra bajo el apartado de **Details**  y péguela en una pestaña de su navegador. Encontrará el siguiente mensaje:

![Este servidor será migrado utilizando AWS Application Migration Service](/static/images/mgn/seramigrado.png)
 
5. Regrese la consola de Amazon EC2 y seleccione de nuevo la casilla de la instancia **Servidor Linux**.
6. Haga clic en el botón de **Connect**.

![Connect to Linux Server](/static/images/mgn/connect1.png)

7. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect** para tener acceso a su instancia vía SSH por medio del navegador web.

![Connect to Linux Server](/static/images/mgn/connect2.png)

8. Ingrese el siguiente comando en el CLI del servidor para descargar el instalador del Agente de Replicación:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo wget -O ./aws-replication-installer-init.py https://aws-application-migration-service-us-east-1.s3.amazonaws.com/latest/linux/aws-replication-installer-init.py
:::

9. Ejecute el siguiente comando para instalar el agente, sustituyendo **ACCESS-KEY** y **SECRET-ACCESS-KEY** por el access key y secret access key que descargó previamente al crear el usuario IAM:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo python3 aws-replication-installer-init.py --region us-east-1 --no-prompt --aws-access-key-id ACCESS-KEY --aws-secret-access-key SECRET-ACCESS-KEY
:::

La instalación del agente tomará un par de minutos y al finalizar mostrará el siguiente mensaje: **The AWS Replication Agent was successfully installed.**

![Agent Installation](/static/images/mgn/commands.png)

::alert[Para más información acerca de como agregar servidores origen, puede consultar la documentación disponible: [Adding source servers](https://docs.aws.amazon.com/mgn/latest/ug/adding-servers.html)]{type="info"}

10. Haga clic en **Services** y posteriormente seleccione el servicio de **AWS Application Migration Service** para regresar a la consola de AWS MGN.

De regreso en el servicio de AWS MGN podrá verificar que el servidor ya aparece en la consola después de haber instalado el agente, y que la replicación ha comenzado. Usted podrá monitorear el progreso de la replicación bajo el apartado de **Data replication status**.

11. Proceda al siguiente módulo en lo que se termina el proceso de replicación.