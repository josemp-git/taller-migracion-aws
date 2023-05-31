---
draft: false
title: 2. Creación de carpeta compartida
weight: 20
---
Después de haber creado su File Gateway, deberá crear una carpeta compartida (file Share) el cual montará en su instancia cliente.

1. Haga clic en **Services** y después en **Storage Gateway**.
2. Haga clic en **File Shares** en el menú lateral del lado izquierdo.
3. Haga clic en **Create file share**.
4. Seleccione los siguientes parámetros:

* Gateway = S3 File gateway
* File share type = NFS
* S3 bucket = **migration-lab-XXXXXXXXXXXX-YYYYYYY**

![File Share Settings](/static/images/sg/filesharesettings.png)

5. Haga clic en **Create file share**.
6. Haga clic en **File Shares** en el menú lateral del izquierdo.
7. Corrobore que el status de la carpeta compartida recién creado sea **Available**.
8. Haga clic sobre el valor de **File share ID** de su carpeta compartida (share-XXXXXXXX).

![File share ID](/static/images/sg/fileshareid.png)

9. Diríjase al apartado de **Example Commands** y copie las instrucciones para montar su carpeta compartida en **Linux** y guárdelas en un editor de texto ya que las utilizará en el siguiente módulo.
10. Proceda al siguiente módulo.