---
draft: false
pre: <b style="color:#fff;">4. </b>
title: Creación de usuarios del servidor SFTP
weight: 40
---
1. Haga clic en **Services** y diríjase al servicio de **CloudShell**.
2. Ejecute el siguiente comando:

```
ssh-keygen -P "" -f user01
```
::alert[La ejecución de este comando generará dos archivos: **user01** (*llave privada*) y **user01.pub** (*llave pública*). Usted utilizará estas llaves para que su usuario se conecte al servidor SFTP.]{type="info"}

3. Ejecute los siguiente comandos:

```
cat user01.pub
```

```
cat user01
```

::alert[La ejecución de estos comandos desplegará el contenido de cada archivo.]{type="info"}

4. Copie el contenido de cada archivo guarde cada uno como un archivo de texto individual.
5. Haga clic en **Services** y diríjase al servicio de **AWS Transfer Family**.
6. Seleccione la casilla del servidor que creó anteriormente y haga clic en el botón de **Add user**.
7. En el campo de **Username** escriba **user01**.
8. En **Access** seleccione el rol que creó (**AWSTransferCustomRole**) del menú desplegable.
9. En **Policy** seleccione **Select policy from IAM** y del menu desplegable seleccione la segunda política que **AWSTransferScopeDownPolicy**.
10. En **Home directory** seleccione el bucket que creó para este laboratorio.
11. En el campo de **Enter optional folder** escriba **user01** (que es el nombre del usuario que está creando y del folder que creó dentro del bucket de Amazon S3).
12. En el campo de **SSH public key** ingrese el contenido del archivo **user01.pub** (la llave pública) que generó anteriormente.

![Cración de usuarios](/static/images/tr/creacionusuarios.png)

13. Haga clic en **Add**.
14. **Opcional:** repita los pasos de este módulo para crear un segundo usuario (**user02**).
15. Proceda al siguiente módulo.