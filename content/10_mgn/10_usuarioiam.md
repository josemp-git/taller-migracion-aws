---
draft: false
title: 2. Creación de usuario AWS IAM
weight: 10
---
Para instalar el Agente de Replicación, primero debe generar las credenciales de AWS necesarias. En este módulo usted creará un usuario de AWS IAM y le asignará la política de permisos adecuada. Al crear este usuario, obtendrá una clave de acceso y una clave de acceso secreta, que ingresará durante la instalación del agente.

1. Haga clic en **Services** y posteriormente seleccione el servicio de **IAM** (también puede usar el campo de búsqueda).
2. Dentro de **IAM**, haga clic en **Users** en el menú lateral izquierdo y posteriormente haga clic en el botón de **Add users**.

![Add user](/static/images/mgn/adduser.png)

3. En el campo de **User name** ingrese :code[mgn]{showCopyAction=true} y haga clic en **Next**.

![User name](/static/images/mgn/username.png)

4. En la pantalla **Set permissions** seleccione la opción de **Attach existing policies directly** y en el campo de búsqueda ingrese :code[AWSApplicationMigrationAgentPolicy]{showCopyAction=true}. 

![Attach existing policies directly](/static/images/mgn/attachpolicy.png)

5. Seleccione la política y haga clic en **Next**.
6. En la siguiente pantalla revise que todo esté correcto y haga clic en **Create user**.

![Create user](/static/images/mgn/createuser.png)

7. Haga clic en **Users** en el menú lateral izquierdo y posteriormente haga clic en el usuario de **mgn** que acaba de crear.
8. Haga clic en **Security credentials**.

![Security credentials](/static/images/mgn/securitycredentials.png)

9. Haga clic en **Create access key**.

![Create access key](/static/images/mgn/createaccesskey1.png)

10. Seleccione la opción de **Application running outside AWS** y haga clic en **Next**.

![Application running outside AWS](/static/images/mgn/outsideaws.png)

11. En el campo de **Description tag value** ingrese **mgn** y haga clic en **Create access key**.

![Create access key](/static/images/mgn/createaccesskey2.png)

12. Copie y guarde el **Acess key** y **Secret access key** que acaba de crear. También puede hacer clic en el botón de **Download .csv file** para descargar las credenciales en un archivo CSV.

![Retrieve access keys](/static/images/mgn/retrieveaccesskeys.png)

13. Haga clic en **Done** y proceda al siguiente módulo.



::alert[Para más información acerca las credenciales requeridas, puede consultar la documentación disponible: [Generating the required AWS credentials](https://docs.aws.amazon.com/mgn/latest/ug/credentials.html)]{type="info"}