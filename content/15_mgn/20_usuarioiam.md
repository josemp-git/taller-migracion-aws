---
draft: false
title: 2. Creación de usuario AWS IAM
weight: 20
---
Para instalar el Agente de Replicación, primero debe generar las credenciales de AWS necesarias. Deberá crear al menos un usuario de AWS IAM y asignarle la política de permisos adecuada. Al crear este usuario, obtendrá una clave de acceso y una clave de acceso secreta, que deberá ingresar durante la instalación del agente.

1. Haga clic en **Services** y posteriormente seleccione el servicio de **IAM** que se encuentra bajo la categoría de **Security, Identity & Compliance** (también puede teclear IAM en el campo de búsqueda).
2. Dentro de **IAM**, haga clic en **Users** en el menú lateral izquierdo y posteriormente haga clic en el botón de **Add user**.
3. En el campo de **User name** escriba el nombre del usuario que va a crear **(mgn)** y en **Access type** seleccione **Access key - Programmatic access**. 
4. Haga clic en **Next: Permissions**.
5. En la pantalla **Set permissions** seleccione la opción de **Attach existing policies directly** y en el campo de búsqueda ingrese **AWSApplicationMigrationAgentPolicy**. 
6. Seleccione la política y haga clic en **Next: Tags**.
7. En la siguiente pantalla haga clic en **Next: Review**.
8. Haga clic en **Create user**.
9. Si todo salió bien, debe ver un mensaje de **<span style="color\:green">Success</span>** en la siguiente pantalla. Haga clic en **Download .csv** para descargar las credenciales del usuario que acaba de crear. Guarde este archivo ya que lo utilizará más adelante.
10. Proceda al siguiente módulo.


::alert[Para más información acerca las credenciales requeridas, puede consultar la documentación disponible: [Generating the required AWS credentials](https://docs.aws.amazon.com/mgn/latest/ug/credentials.html)]{type="info"}