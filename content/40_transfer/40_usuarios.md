---
draft: false
title: 4. Creación de usuarios del servidor SFTP
weight: 40
---
1. Haga clic en **Services** y diríjase al servicio de **CloudShell**.
2. Ejecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
ssh-keygen -P "" -f user01
:::

::alert[La ejecución de este comando generará dos archivos: **user01** (*llave privada*) y **user01.pub** (*llave pública*). Usted utilizará estas llaves para que su usuario se conecte al servidor SFTP.]{type="info"}

3. Ejecute los siguiente comandos:

:::code{showCopyAction=true showLineNumbers=false language=java}
cat user01.pub
:::

:::code{showCopyAction=true showLineNumbers=false language=java}
cat user01
:::

::alert[La ejecución de estos comandos desplegará el contenido de cada archivo.]{type="info"}

4. Copie el contenido de cada llave y guárdelas como archivos de texto individuales.
5. Haga clic en **Services** y diríjase al servicio de **AWS Transfer Family**.
6. Seleccione la casilla del servidor que creó anteriormente y haga clic en el botón de **Add user**.

![Add user](/static/images/tr/adduser.png)

7. Ingrese :code[user01]{showCopyAction=true} en el campo de **Username**.
8. En el menú desplegable de **Role** seleccione el rol que creó anteriormente (:code[AWSTransferCustomRole]{showCopyAction=true}).
9. En **Policy** seleccione **None**.
10. En el menú desplegable de **Home directory** seleccione el bucket que creó para este laboratorio.
11. En el campo adicional de **Home directory** ingrese :code[user01]{showCopyAction=true} (que es el nombre del usuario que está creando y del directorio que creó dentro del bucket de Amazon S3).
12. Seleccione la casilla de **Restricted**.
13. En el campo de **SSH public key** ingrese el contenido del archivo **user01.pub** (la llave pública) que generó anteriormente.

![Cración de usuarios](/static/images/tr/creacionusuarios.png)

14. Haga clic en **Add**.
15. **Opcional:** repita los pasos de este módulo para crear un segundo usuario (:code[user02]{showCopyAction=true}).
16. Proceda al siguiente módulo.