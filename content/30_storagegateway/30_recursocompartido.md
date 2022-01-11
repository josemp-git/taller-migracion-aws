---
draft: false
title: 3. Creación de recurso compartido
weight: 30
---
Después de haber creado su File Gateway, deberá crear un File Share el cual montará en su instancia cliente.

1. Haga clic en ***Services*** y después en ***Storage Gateway***.
2. Haga clic en ***File Shares*** en el menú lateral del lado izquierdo.
3. Haga clic en ***Create file share***.
4. En el menú desplegable de ***Gateway*** seleccione el Gateway que creó anteriormente.
5. En el campo de ***Amazon S3 bucket name*** ingrese el nombre del bucket de Amazon S3 que creó para este laboratorio.
6. En la opción de ***Access objects using*** seleccione ***Network File System (NFS)***.
 

![File Share Settings](/static/images/sg/filesharesettings.png)

7. Haga clic en ***Next***.
8. En ***Storage class for new objects*** seleccione ***S3 Standard***.
9. Haga clic en ***Next***.
10. En la pantalla de ***File access settings*** mantenga los valores predeterminados y haga clic en ***Next***.
11. En la pantalla de ***Review*** haga clic en ***Create file share***.
12. Haga clic en ***File Shares*** en el menú lateral del izquierdo.
13. Corrobore que el status del recurso compartido recién creado sea ***Available***
14. Haga clic sobr el valor de ***File share ID*** de su recurso compartido (share-XXXXXXXX)
15. Diríjase al apartado de ***Example Commands*** y copie las instrucciones para conectarse a su recurso compartido desde ***Linux*** y guárdelas en un editor de texto ya que las utilizará en el siguiente módulo.
16. Proceda al siguiente módulo.