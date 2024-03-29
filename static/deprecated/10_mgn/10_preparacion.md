---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
Antes de comenzar, debe asegurarse de estar trabajando en la región de **N. Virgina**. Esto lo puede verificar en el menú desplegable que se encuentra en la esquina superior derecha de la consola de AWS.

A continuación, desplegará una instancia de Linux en la región de N. Virgina utilizando una plantilla de CloudFormation. Esta plantilla se creará la instancia, aplicar las actualizaciones de sistema operativo correspondientes, instalar el servidor web Apache y configurará un grupo de seguridad con los puertos 22 (ssh) y 80 (http) habilitados. Esta instancia es la que migrará utilizando AWS MGN. Esta plantilla también creará una VPC con tres subredes:

* **Staging Area subnet** - Esta es la subred en la que se desplegará el **servidor de replicación** necesario para el proceso de migración
*  **Target subnet** - Esta es la subred destino en la que lanzará su servidor una vez que este haya sido migrado por completo.
*  **Private subnet** - Esta es una subred privada que no se utilizará en este laboratorio.


1. Abra la siguiente URL en la pestaña de su navegador, copie la dirección IP que ahí aparece y guárdela en un archivo de texto.

:::code{showCopyAction=true showLineNumbers=false language=java}
http://checkip.amazonaws.com/
:::

2. Descargue la plantilla de AWS CloudFormation: :button[Descargar]{href="/static/15_mgn/mgn-lab.yaml" action=download variant="primary"}

3. Haga clic en **Services** y después en **CloudFormation** (también puede usar el campo de búsqueda).

![CloudFormation](/static/images/mgn/cloudformation1.png)

4. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.

![CloudFormation](/static/images/mgn/cloudformation2.png)

5. Seleccione **Upload a template file** y cargue la plantilla de CloudFormation que descargó anteriormente.

![CloudFormation](/static/images/mgn/cloudformation3.png)

6. Haga clic en **Next**.
7. En el campo de **Stack name** ingrese :code[mgn-lab]{showCopyAction=true}.
8. En el campo de **IPPublica** ingrese la dirección IP que copió anteriormente.
9. Haga clic en **Next**.
10. En la siguiente pantalla haga clic de nuevo en **Next**.
11. En la siguiente pantalla seleccione la casilla de **I acknowledge that AWS CloudFormation might create IAM resources** que aparece el final.
12. Haga clic en **Create stack**.

![CloudFormation](/static/images/mgn/acknowledgerole.png)

13. Proceda al siguiente módulo mientras AWS CloudFormation termina de desplegar los recursos.