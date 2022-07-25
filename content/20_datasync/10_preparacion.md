---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
##### 1. Desplegar plantilla de AWS CloudFormation

A continuación, desplegará una plantilla de AWS CloudFormation que creará las siguientes instancias Amazon EC2:

- **Instancia NFS**
    - Esta instancia comparte un directorio en la red por medio de NFS. En este directorio se encuentra información estadística de baseball de los últimos 20 años que usted migrará a Amazon S3 utilizando AWS DataSync. Esta instancia actuará como un servidor NFS "en sitio" con información que se predente migrar a la nube de AWS.
- **Instancia cliente**
    - En esta instancia usted montará el recurso compartido por la instancia NFS. Esta instancia cliente actuará como si fuera su computadora "en sitio".


1. Descargue esta :link[plantilla de CloudFormation]{href="/static//20_datasync/dm-lab-ds.yaml" action=download}.
2. Haga clic en **Services** y después en **CloudFormation** (también puede usar el campo de búsqueda).

![CloudFormation](/static/images/ds/cloudformation1.png)

3. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.

![CloudFormation](/static/images/ds/cloudformation2.png)

4. Seleccione **Upload a template file** y cargue la plantilla de CloudFormation que descargó anteriormente.

![CloudFormation](/static/images/ds/cloudformation3.png)

5. Haga click en **Next**.
6. En el campo de **Stack name** escriba **datasync-lab**.
7. Haga click en **Next**.
8. En la siguiente pantalla haga click de nuevo en **Next**.
9. En la siguiente pantalla seleccione la casilla de **I acknowledge that AWS CloudFormation might create IAM resources** que aparece el final.
10. Haga click en **Create stack**.

![CloudFormation](/static/images/ds/acknowledgerole.png)

11. Espere unos minutos a que el status de lanzamiento de la plantilla indique **CREATE_COMPLETE**.
12. Una vez que la plantilla haya sido desplegada, haga click en la sección de **Outputs** y copie el valor del parámetro **NFSInstancePrivateIP** (la dirección IP privada del servidor NFS) y guárdelo en un archivo de texto ya que lo utilizará más adelante.

![Outputs](/static/images/ds/outputs.png)


##### 2. Creación de bucket de Amazon S3

A continuación creará un bucket de Amazon S3 en donde almacenará la información que migre utilizando AWS DataSync.

13. Haga click en **Services** y posteriormente seleccione el servicio de **S3**.
14. Haga click en **Create bucket**.
15. Ingrese un nombre para su bucket en el campo de **Bucket name** con la siguiente nomenclatura: 
migracion-datos-lab-**SU-NOMBRE**.

16. En el menú desplegable de **Region** asegúrese de que la región sea **US East (N. Virginia)**.
17. Haga click en **Create**.

##### 3. Configuración de la instancia cliente

A continuación se conectará a la instancia cliente para montar el recurso compartido por el servidor NFS y así poder acceder a los datos contenidos en directorio compartido.

18. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
19. Haga click en **Running instances**.
20. Seleccione la casilla  **Instancia cliente**.
21. Haga clic en el botón de **Connect**.

![Connect to Linux Server](/static/images/ds/connect1.png)

22. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect**.

![Connect to Linux Server](/static/images/ds/connect2.png)

23. Una vez conectado a su instancia cliente ejecute el siguiente comando sustituyendo el parámetro **NFSInstancePrivateIP** por la dirección IP correspondiente que guardó en el editor de texto:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo mount -t nfs NFSInstancePrivateIP:/mnt/nfs /home/ssm-user/nas
:::

::alert[Este comando montará un directorio compartido por la instancia que funge como servidor NFS.]{type="info"}

24. Proceda a explorar el contenido de este directorio con los siguientes comandos:

Para acceder al directorio
:::code{showCopyAction=true showLineNumbers=false language=java}
cd /home/ssm-user/nas
:::

Para enlistar el contenido
:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ssm-user/nas
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ssm-user/nas/baseballdatabank-master/
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ssm-user/nas/baseballdatabank-master/core
:::

En este directorio compartido encontrará información estadística de baseball de los últimos 20 años. En este laboratorio usted migrará esta información histórica a un bucket de Amazon S3 utilizando AWS DataSync.

![EC2 CLI](/static/images/ds/explorenfs.png)

25. Proceda al siguiente módulo.