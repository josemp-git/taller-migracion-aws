---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
::alert[**ANTES DE CONTINUAR.** Si usted hizo el laboratorio de **Migración de datos con AWS DataSync** y no ha eliminado los recursos creados, puede omitir este módulo y continuar utilizando los recursos ya existentes.]{type="info"}

##### 1. Crear de Key Pair

Lo primero que debe hacer es crear un key pair. Este key pair le permitirá acceder a las instancias que creará más adelante.

1. Asegúrese de estar trabajando en la región de ***N. Virgina*** durante este laboratorio. Esto lo puede verificar en el menú desplegable que se encuentra en la esquina superior derecha de la consola de AWS.
2. Haga click en ***Services*** y posteriormente seleccione el servicio de ***EC2***.
3. Una vez dentro de la consola de Amazon EC2, haga click en la sección de ***Key Pairs*** que se encuentra en el menú lateral izquierdo.
4. Haga click en ***Create key pair***.
5. En el campo de ***Key pair name*** ingrese un nombre para su key pair (ejemplo: ***dm-lab***).
6. Haga click en ***Create*** y guarde el archivo que se va a descargar.


##### 2. Desplegar plantilla de AWS CloudFormation

A continuación, desplegará una plantilla de AWS CloudFormation que creará una instancia Amazon EC2 en la cual montará el recurso compartido que creará con AWS Storage Gateway. Esta **instancia cliente** actuará como si fuera su computadora "en sitio".

7. Haga click en ***Services*** y después en ***CloudFormation***.
8. Haga click en ***Create stack*** y seleccione la opción ***With new resources (standard)***.
9. En el campo de ***Amazon S3 URL*** ingrese la siguiente URL: 

```
https://taller-migracion-dev.s3.amazonaws.com/dm-lab-sg.yaml
```

10. Haga click en ***Next***.
11. En el campo de ***Stack name*** escriba ***MigracionDatosStack***.
12. En el menú desplegable de ***KeyPair*** bajo la sección de ***Parameters*** elija el key pair que creó anteriormente (***dm-lab***).
13. Haga click en ***Next***.
14. En la siguiente pantalla haga click de nuevo en ***Next***.
15. En la siguiente pantalla haga click en ***Create stack***.
16. Espere unos minutos a que el status de lanzamiento de la plantilla indique ***CREATE_COMPLETE***.
17. Una vez que la plantilla haya sido desplegada, haga click en la sección de ***Outputs*** y copie el valor del parámetro ***ClientInstancePrivateIP*** (la dirección IP privada de la instancia cliente) y guárdelo en un archivo de texto ya que lo utilizará más adelante.


##### 3. Creación de bucket de Amazon S3

En los siguientes pasos creará un bucket de Amazon S3 en donde almacenará la información que migre utilizando AWS DataSync.

18. Haga click en ***Services*** y posteriormente seleccione el servicio de ***S3***.
19. Haga click en ***Create bucket***.
20. Ingrese un nombre para su bucket en el campo de ***Bucket name*** con la siguiente nomenclatura: 
***migracion-datos-su-nombre***.
21. En el menú desplegable de ***Region*** asegúrese de que la región sea ***US East (N. Virginia)***.
22. Haga click en ***Create***.
23. Proceda al siguiente módulo.