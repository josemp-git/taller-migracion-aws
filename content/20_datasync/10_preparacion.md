---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
##### 1. Desplegar plantilla de AWS CloudFormation

A continuación, desplegará una plantilla de AWS CloudFormation que creará los siguientes recursos:

- **Servidor NFS**
    - Esta instancia de Amazon EC2 comparte un directorio en la red por medio de NFS. En este directorio se encuentra información estadística de baseball de los últimos 20 años que usted migrará a Amazon S3 utilizando AWS DataSync. Esta instancia actuará como un servidor NFS "en sitio" con información que se predente migrar a la nube de AWS.
- **Instancia cliente**
    - En esta instancia de Amazon EC2 usted montará el recurso compartido por la instancia NFS. Esta instancia cliente actuará como si fuera su computadora "en sitio".
- **Bucket Amazon S3**
    - El destino al cual migrará los datos.
- **VPC y subred**
    - Donde se alojarán las instancias creadas para esta laboratorio y el agende de AWS DataSync.

1. Descargue esta :link[plantilla de CloudFormation]{href="/static/20_datasync/dm-lab-ds.yaml" action=download}.
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
12. Una vez que la plantilla haya sido desplegada, haga click en la sección de **Outputs** y copie el valor del parámetro **NFSInstancePrivateIP** (la dirección IP privada del servidor NFS) y guárdelo en un archivo de texto ya que lo utilizará más adelante. En este apartado también encontrará el nombre del bucket que se creó para almacenar sus datos una vez que estos sean migrados.

![Outputs](/static/images/ds/outputs.png)

##### 2. Configuración de la instancia cliente

A continuación se conectará a la instancia cliente para montar el recurso compartido por el servidor NFS y así poder acceder a los datos contenidos en directorio compartido.

13. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
14. Haga click en **Running instances**.
15. Seleccione la casilla  **Instancia cliente**.
16. Haga clic en el botón de **Connect**.

![Connect to Linux Server](/static/images/ds/connect1.png)

17. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect**.

![Connect to Linux Server](/static/images/ds/connect2.png)

18. Una vez conectado a su instancia cliente ejecute el siguiente comando sustituyendo el parámetro **NFSInstancePrivateIP** por la dirección IP correspondiente que guardó en el editor de texto:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo mount -t nfs NFSInstancePrivateIP:/mnt/nfs /home/ec2-user/nas
:::

::alert[Este comando montará un directorio compartido por la instancia que funge como servidor NFS.]{type="info"}

19. Proceda a explorar el contenido de este directorio con los siguientes comandos:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo ls /home/ec2-user/nas
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
sudo ls /home/ec2-user/nas/baseballdatabank-master/
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
sudo ls /home/ec2-user/nas/baseballdatabank-master/core
:::

::alert[En este directorio compartido encontrará información estadística de baseball de los últimos 20 años. En este laboratorio usted migrará esta información histórica a un bucket de Amazon S3 utilizando AWS DataSync.]{type="info"}

![EC2 CLI](/static/images/ds/explorenfs.png)

20. Proceda al siguiente módulo.