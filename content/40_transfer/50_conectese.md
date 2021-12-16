---
draft: false
pre: <b style="color:#fff;">5. </b>
title: Conéctese a su servidor SFTP
weight: 50
---
1. Utilice un cliente de SFTP como [**FileZilla**](https://filezilla-project.org/download.php) o [**Cyberduck**](https://cyberduck.io/download/) para conectarse al servidor SFTP con el usuario que creó (**user01**) y la **llave privada** que generó anteriormente. La dirección del servidor es el valor de **Endpoint** que guardó en el editor de texto.

![Create S3 bucket](/static/images/tr/conectar.png)

2. Una vez conectado navegue a través de los directorios y comience a subir archivos.
3. Verifique que efectivamente su(s) usuario(s) solamente tiene(n) acceso al directorio de su nombre.
4. Haga clic en **Services** y diríjase al servicio de **S3**.
5. Ingrese al bucket que creó inicialmente y corrobore que los archivos que subió por medio del servidor SFTP se encuentran ahí.

Fin del laboratorio