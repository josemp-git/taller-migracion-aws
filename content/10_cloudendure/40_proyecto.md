---
draft: false
pre: <b style="color:#fff;">4. </b>
title: Creación de un proyecto de migración
weight: 40
---
Para poder llevar a cabo un proceso de migración de servidores con CloudEndure, debe crear un proyecto en la consola en donde establecerá parámetros tales como las credenciales de AWS que se utilizarán, las ubicaciones de origen y destino de los servidores a migrar, tipo de instancia de los servidores de replicación, VPC y subred de destino, etc. En este caso, hará una migración sencilla utilizando la mayoría de los valores predeterminados.

1. Ingrese a la siguiente dirección https://console.cloudendure.com/ con el usuario y contraseña que creó en el módulo anterior.
2. Una vez dentro de la consola de CloudEndure, haga clic en el botón de **+ (clic this button to create new Project)** que se encuentra en la esquina superior izquierda.

![Create New Project](/static/images/ce/newproject.png)

3. En la siguiente pantalla ingrese el nombre de su proyecto y haga clic en **CREATE PROJECT**.

![Create New Project](/static/images/ce/create.png)

4. En la siguiente pantalla haga clic en **Start**.
5. En la siguiente pantalla haga clic en **Continue**.
6. En la pantalla de **AWS Credentials** ingrese el **Access Key ID** y **Secret Access Key** del usuario **cloudendure** que creó anteriormente utilizando el servicio de **IAM** en la consola de AWS. Estas credenciales se encuentran en el **archivo .CSV** que descargó cuando creó el usuario. 
7. Haga clic en **SAVE**.

![AWS Credentials](/static/images/ce/credentials.png)

8. En la siguiente pestaña, **Replication Settings**, debe indicar el origen y destino de su proyecto de migración. Como origen, seleccione **AWS US East (Northen Virgina)** bajo el menú desplegable de **Migration Source**. Como destino, seleccione **AWS US East (Northen Virgina)** bajo el menú desplegable de **Migration Target**. 

![Replication Settings](/static/images/ce/replicationsettings.png)

9. En la misma pestaña de **Replication Settings** debe indicar en qué subred serán lanzados los servidores de replicación. Para llevar a cabo lo anterior diríjase al apartado de **Choose the subnet where the Replication Server will be launched** y del menú desplegable elija la subnet del área de staging de la VPC CloudEndureLab **(Staging-Area Subnet – CloudEndureLab)**.

![Staging Area subnet](/static/images/ce/stagingareasubnet.png)

10. En la misma pestaña de **Replication Settings** debe indicar el tipo de disco que utilizarán los servidores de replicación para guardar los datos que reciben desde el punto de origen. Para llevar a cabo lo anterior diríjase al apartado de **Choose the default disk type to be used by the Replication Servers** y del menú desplegable elija  **(Use slower, low cost standard data disks)**.

![Replication Servers disk type](/static/images/ce/disks-replication-server.png)

11. Haga clic en el botón de **SAVE REPLICATION SETTINGS** que se encuentra al final de la página.
12. En la siguiente pantalla haga clic en **SHOW ME HOW**.
13. Proceda al siguiente módulo.