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
5. En el campo de **Key pair name** ingrese un nombre para su key pair (ejemplo: **datasync**).
6. Haga click en **Create** y guarde el archivo que se va a descargar.

![Create key pair](/static/images/ds/keypair.png)

##### 2. Desplegar plantilla de AWS CloudFormation

A continuación, desplegará una plantilla de AWS CloudFormation que creará las siguientes instancias Amazon EC2:

- **Instancia NFS**
    - Esta instancia comparte un directorio en la red por medio de NFS. En este directorio se encuentra información estadística de baseball de los últimos 20 años que usted migrará a Amazon S3 utilizando AWS DataSync. Esta instancia actuará como un servidor NFS "en sitio" con información que se predente migrar a la nube de AWS.
- **Instancia cliente**
    - En esta instancia usted montará el recurso compartido por la instancia NFS. Esta instancia cliente actuará como si fuera su computadora "en sitio".

7. Descargue esta plantilla de CloudFormation:

```bash
:assetUrl{path="/20_datasync/dm-lab-ds.yaml"}
```

8. Abra la siguiente URL en la pestaña de su navegador, copie la dirección IP que ahí aparece y guárdela en un archivo de texto.

:::code{showCopyAction=true showLineNumbers=false language=java}
http://checkip.amazonaws.com/
:::

9. Haga clic en **Services** y después en **CloudFormation** (también puede usar el campo de búsqueda).

![CloudFormation](/static/images/ds/cloudformation1.png)

10. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.

![CloudFormation](/static/images/ds/cloudformation2.png)

11. Seleccione **Upload a template file** y cargue la plantilla de CloudFormation que descargó anteriormente.

![CloudFormation](/static/images/ds/cloudformation3.png)


12. Haga click en **Next**.
13. En el campo de **Stack name** escriba **datasync-lab**.
14. En el campo de **IPPublica** ingrese la dirección IP que copió anteriormente.
15. En el menú desplegable de **KeyPair** bajo la sección de **Parameters** elija el key pair que creó anteriormente (**datasync**).
16. Haga click en **Next**.
17. En la siguiente pantalla haga click de nuevo en **Next**.
18. En la siguiente pantalla seleccione la casilla de **I acknowledge that AWS CloudFormation might create IAM resources** que aparece el final.
19. Haga click en **Create stack**.

![CloudFormation](/static/images/ds/acknowledgerole.png)

20. Espere unos minutos a que el status de lanzamiento de la plantilla indique **CREATE_COMPLETE**.
21. Una vez que la plantilla haya sido desplegada, haga click en la sección de **Outputs** y copie el valor del parámetro **NFSInstancePrivateIP** (la dirección IP privada del servidor NFS) y guárdelo en un archivo de texto ya que lo utilizará más adelante.

![Outputs](/static/images/ds/outputs.png)


##### 3. Creación de bucket de Amazon S3

En los siguientes pasos creará un bucket de Amazon S3 en donde almacenará la información que migre utilizando AWS DataSync.

22. Haga click en **Services** y posteriormente seleccione el servicio de **S3**.
23. Haga click en **Create bucket**.
24. Ingrese un nombre para su bucket en el campo de **Bucket name** con la siguiente nomenclatura: 
**migracion-datos-su-nombre**.
25. En el menú desplegable de **Region** asegúrese de que la región sea **US East (N. Virginia)**.
26. Haga click en **Create**.

##### 4. Configuración de la instancia cliente

A continuación se conectará a la instancia cliente para montar el recurso compartido por el servidor NFS y así poder acceder a los datos contenidos en directorio compartido.

27. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
28. Haga click en **Running instances**.
29. Seleccione la casilla  **Instancia cliente**.
30. Haga clic en el botón de **Connect**.

![Connect to Linux Server](/static/images/ds/connect1.png)

31. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect** para tener acceso a su instancia vía SSH por medio del navegador web.

![Connect to Linux Server](/static/images/ds/connect2.png)

32. Una vez conectado a su instancia cliente ejecute el siguiente comando sustituyendo el parámetro **NFSInstancePrivateIP** por la dirección IP correspondiente que guardó en el editor de texto:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo mount -t nfs NFSInstancePrivateIP:/mnt/nfs ~/nas
:::

::alert[Este comando montará un directorio compartido por la instancia que funge como servidor NFS.]{type="info"}

33. Proceda a explorar el contenido de este directorio con los siguientes comandos:

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

34. Proceda al siguiente módulo.