---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
Antes de comenzar, debe asegurarse de estar trabajando en la región de N. Virgina. Esto lo puede verificar en el menú desplegable que se encuentra en la esquina superior derecha de la consola de AWS.

#### 1. Creación de key pair

Lo primero que debe hacer es crear un key pair. Este key pair le acceder a la instancia que se creará más adelante y que migrará utilizando AWS MGN. PAra crear un key pair debe hacer lo siguiente:

1. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2** el cual se encuentra bajo la categoría de **Compute**.
2. Una vez en **EC2**, haga clic en la sección de **Key Pairs** que se encuentra en el menú de la izquierda y posteriormente haga clic en **Create key pair**.
3. En el campo de **Name** ingrese un nombre para su key pair (ejemplo: **mgn-lab**).
4. En el apartado de **Key type** seleccione **RSA**.
5. En el apartado de  **Private key file format** se recomienda elegir:
    - **Pem**, para usuarios de Linux/Mac (terminal).
    - **Ppk**, para usuarios de Windows (PuTTy).
6. Haga clic en **Create key pair** y guarde el archivo que se va a descargar.

#### 2. Despliegue de plantilla de CloudFormation

A continuación, desplegará una instancia de Linux en la región de N. Virgina utilizando una plantilla de CloudFormation. Esta plantilla se hará cargo de instalar la instancia, aplicar las actualizaciones de sistema operativo correspondientes, instalar el servidor web Apache y configurar un grupo de seguridad con los puertos 22 (ssh) y 80 (http) habilitados. Esta instancia es la que migrará utilizando AWS MGN. Esta plantilla también creará una VPC con tres subredes:

* **Staging Area Subnet** - Esta es la subred en la que se desplegará el **servidor de replicación** necesario para el proceso de migración
*  **Target subnet** - Esta es la subred destino en la que lanzará su servidor una vez que este haya sido migrado por completo.
*  **Private subnet** - Esta es una subred privada que no se utilizará en este laboratorio.

Para desplegar dicha plantilla siga los siguientes pasos:

7. Haga clic en **Services** y después en **CloudFormation** que se encuentra bajo la categoría de **Management & Governance** (también puede teclear CloudFormation en el campo de búsqueda).
8. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.
9. En el campo de **Amazon S3 URL** ingrese la siguiente URL: 

:::code{showCopyAction=true showLineNumbers=false language=java}
https://taller-migracion-dev.s3.amazonaws.com/15_mgn/mgn-lab.yaml
:::

10. Haga clic en **Next**.
11. En el campo de **Stack name** escriba **MGN-Lab**.
12. En el menú desplegable de **KeyPair** bajo la sección de **Parameters** elija el key pair que creó anteriormente **(mgn-lab)**.
13. Haga clic en **Next**.
14. En la siguiente pantalla haga clic de nuevo en **Next**.
15. En la siguiente pantalla haga clic en **Create stack**.
16. Proceda al siguiente módulo mientras AWS CloudFormation termina de desplegar los recursos.