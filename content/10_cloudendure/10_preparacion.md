---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
Antes de comenzar, debe asegurarse de estar trabajando en la región de N. Virgina. Esto lo puede verificar en el menú desplegable que se encuentra en la esquina superior derecha de la consola de AWS.

#### 1. Creación de key pair
Lo primero que debe hacer es crear un key pair. Este key pair le permitirá acceder a la instancia que creará más adelante y la cual migrará a otra región de AWS utilizando CloudEndure. Para crear un key pair debe hacer lo siguiente:

1. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2** el cual se encuentra bajo la categoría de **Compute**.
2. Una vez en **EC2**, haga clic en la sección de **Key Pairs** que se encuentra en el menú de la izquierda y posteriormente haga clic en **Create key pair**.
3. En el campo de **Name** ingrese un nombre para su key pair (ejemplo: **cloudendure-lab**).
4. En el apartado de  **File format** se recomienda elegir:
    - **Pem**, para usuarios de Linux/Mac (terminal).
    - **Ppk**, para usuarios de Windows (PuTTy).
5. Haga clic en **Create key pair** y guarde el archivo que se va a descargar.

#### 2. Despliegue de plantilla de CloudFormation

A continuación, desplegará una instancia de Linux en la región de N. Virgina utilizando una plantilla de CloudFormation. Esta plantilla se hará cargo de instalar la instancia, aplicar las actualizaciones de sistema operativo correspondientes, instalar el servidor web Apache y configurar un security group con los puertos 22 (ssh) y 80 (http) habilitados. Esta instancia es la que migrará utilizando CloudEndure. Esta plantilla también creará una VPC con tres subnets (dos públicas y una privada). En esta VPC es donde va a desplegar su instancia una vez que haya sido migrada y es también donde CloudEndure desplegará el servidor de replicación necesario para el proceso de migración.

Para desplegar dicha plantilla siga los siguientes pasos:

6. Haga clic en **Services** y después en **CloudFormation** que se encuentra bajo la categoría de **Management & Governance** (también puede teclear CloudFormation en el campo de búsqueda).
7. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.
8. En el campo de **Amazon S3 URL** ingrese la siguiente URL: 


:::code{showCopyAction=true showLineNumbers=false language=java}
https://taller-migracion-dev.s3.amazonaws.com/cloudendurelab.yaml
:::

9. Haga clic en **Next**.
10. En el campo de **Stack name** escriba **CloudEndureLab**.
11. En el menú desplegable de **KeyPair** bajo la sección de **Parameters** elija el key pair que creó anteriormente **(cloudendure-lab)**.
12. Haga clic en **Next**.
13. En la siguiente pantalla haga clic de nuevo en **Next**.
14. En la siguiente pantalla haga clic en **Create stack**.
15. Proceda al siguiente módulo mientras AWS CloudFormation termina de desplegar los recursos.