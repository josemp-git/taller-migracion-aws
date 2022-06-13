---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
##### 1. Crear de Key Pair

Lo primero que debe hacer es crear un key pair. Este key pair le permitirá acceder a las instancias que creará más adelante.

1. Asegúrese de estar trabajando en la región de **N. Virgina** durante este laboratorio. Esto lo puede verificar en el menú desplegable que se encuentra en la esquina superior derecha de la consola de AWS.
2. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
3. Una vez dentro de la consola de Amazon EC2, haga click en la sección de **Key Pairs** que se encuentra en el menú lateral izquierdo.
4. Haga click en **Create key pair**.
5. En el campo de **Key pair name** ingrese un nombre para su key pair (ejemplo: **dm-lab**).
6. Haga click en **Create** y guarde el archivo que se va a descargar.


##### 2. Desplegar plantilla de AWS CloudFormation

A continuación, desplegará una plantilla de AWS CloudFormation que creará las siguientes instancias Amazon EC2:

- **Instancia NFS**
    - Esta instancia comparte un directorio en la red por medio de NFS. En este directorio se encuentra información estadística de baseball de los últimos 20 años que usted migrará a Amazon S3 utilizando AWS DataSync. Esta instancia actuará como un servidor NFS "en sitio" con información que se predente migrar a la nube de AWS.
- **Instancia cliente**
    - En esta instancia usted montará el recurso compartido por la instancia NFS. Esta instancia cliente actuará como si fuera su computadora "en sitio".

7. Descargue [esta plantilla](/static/20_datasync/dm-lab-ds.yaml) de CloudFormation.

8. Abra la siguiente URL en la pestaña de su navegador, copie la dirección IP que ahí aparece y guárdela en un archivo de texto.

:::code{showCopyAction=true showLineNumbers=false language=java}
http://checkip.amazonaws.com/
:::

9. Haga clic en **Services** y después en **CloudFormation** (también puede usar el campo de búsqueda).

![CloudFormation](/static/images/mgn/cloudformation1.png)

10. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.

![CloudFormation](/static/images/mgn/cloudformation2.png)

11. Seleccione **Upload a template file** y cargue la plantilla de CloudFormation que descargó anteriormente.

![CloudFormation](/static/images/mgn/cloudformation3.png)


12. Haga click en **Next**.
13. En el campo de **Stack name** escriba **datasync-lab**.
14. En el campo de **IPPublica** ingrese la dirección IP que copió anteriormente.
15. En el menú desplegable de **KeyPair** bajo la sección de **Parameters** elija el key pair que creó anteriormente (**dm-lab**).
16. Haga click en **Next**.
17. En la siguiente pantalla haga click de nuevo en **Next**.
18. En la siguiente pantalla haga click en **Create stack**.
19. Espere unos minutos a que el status de lanzamiento de la plantilla indique **CREATE_COMPLETE**.
20. Una vez que la plantilla haya sido desplegada, haga click en la sección de **Outputs** y copie el valor del parámetro **NFSInstancePrivateIP** (la dirección IP privada del servidor NFS) y guárdelo en un archivo de texto ya que lo utilizará más adelante.

![Outputs](/static/images/ds/outputs.png)


##### 3. Creación de bucket de Amazon S3

En los siguientes pasos creará un bucket de Amazon S3 en donde almacenará la información que migre utilizando AWS DataSync.

21. Haga click en **Services** y posteriormente seleccione el servicio de **S3**.
22. Haga click en **Create bucket**.
23. Ingrese un nombre para su bucket en el campo de **Bucket name** con la siguiente nomenclatura: 
**migracion-datos-su-nombre**.
24. En el menú desplegable de **Region** asegúrese de que la región sea **US East (N. Virginia)**.
25. Haga click en **Create**.

##### 4. Configuración de la instancia cliente

A continuación se conectará a la instancia cliente para montar el recurso compartido por el servidor NFS y así poder acceder a los datos contenidos en directorio compartido.

26. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
27. Haga click en **Running instances**.
28. Seleccione la casilla  **Instancia cliente**.
29. Haga click en **Connect**.
30. Seleccione **EC2 Instance Connect** y haga click en **Connect** para tener acceso a la instancia cliente vía SSH por medio del navegador web.

![Connect to Linux Server](/static/images/ds/conectarec2.png)

31. Una vez conectado a su instancia cliente ejecute el siguiente comando sustituyendo el parámetro **NFSInstancePrivateIP** por la dirección IP correspondiente que guardó en el editor de texto:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo mount -t nfs NFSInstancePrivateIP:/mnt/nfs ~/nas
:::

::alert[Este comando montará un directorio compartido por la instancia que funge como servidor NFS.]{type="info"}

32. Proceda a explorar el contenido de este directorio con los siguientes comandos:

Para acceder al directorio
:::code{showCopyAction=true showLineNumbers=false language=java}
cd ~/nas
:::

Para enlistar el contenido
:::code{showCopyAction=true showLineNumbers=false language=java}
ls ~/nas
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
ls ~/nas/baseballdatabank-master/
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
ls ~/nas/baseballdatabank-master/core
:::

En este directorio compartido encontrará información estadística de baseball de los últimos 20 años. En este laboratorio usted migrará esta información histórica a un bucket de Amazon S3 utilizando AWS DataSync.

![EC2 CLI](/static/images/ds/explorenfs.png)

33. Proceda al siguiente módulo.