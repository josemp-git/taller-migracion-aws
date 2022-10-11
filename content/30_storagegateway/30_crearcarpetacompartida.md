---
draft: false
title: 3. Creación de carpeta compartida
weight: 30
---
Después de haber creado su File Gateway, deberá crear una carpeta compartida (file Share) el cual montará en su instancia cliente.

1. Haga clic en **Services** y después en **Storage Gateway**.
2. Haga clic en **File Shares** en el menú lateral del lado izquierdo.
3. Haga clic en **Create file share**.
4. En el menú desplegable de **Gateway** seleccione el Gateway que creó anteriormente.
5. En el apartado de **Amazon S3 location** seleccione **S3 bucket name**.
6. En el campo de **Amazon S3 bucket name** ingrese el nombre del bucket de Amazon S3 que se creó cuando lanzó la plantilla de CloudFormation al inicio.

![File Share Settings](/static/images/sg/filesharesettings1.png)

7. En el menú desplegable de AWS region seleccione **US East (N. Virginia) us-east-1**.
8. En la opción de **Access objects using** seleccione **Network File System (NFS)**.

![File Share Settings](/static/images/sg/filesharesettings2.png)

9. Haga clic en **Next**.
10. En el menú desplegable de **Storage class for new objects** seleccione ***S3 Standard*** y mantenga los valores predeterminados del resto de las opciones.

![Storage class for new objects](/static/images/sg/storageclass.png)

11. Haga clic en **Next**.
12. En la pantalla de **File access settings** mantenga los valores predeterminados y haga clic en **Next**.
13. En la pantalla de **Review and create** haga clic en **Create**.
14. Haga clic en **File Shares** en el menú lateral del izquierdo.
15. Corrobore que el status de la carpeta compartida recién creado sea **Available**.
16. Haga clic sobre el valor de **File share ID** de su carpeta compartida (share-XXXXXXXX).

![File share ID](/static/images/sg/fileshareid.png)

17. Diríjase al apartado de **Example Commands** y copie las instrucciones para montar su carpeta compartida en **Linux** y guárdelas en un editor de texto ya que las utilizará en el siguiente módulo.
16. Proceda al siguiente módulo.