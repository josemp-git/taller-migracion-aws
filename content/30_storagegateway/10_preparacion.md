---
draft: false
title: 1. Preparación del ambiente
weight: 10
---
::alert[**ANTES DE CONTINUAR.** Si usted hizo el laboratorio de **Migración de datos con AWS DataSync** y no ha eliminado los recursos creados, puede omitir este módulo y continuar utilizando los recursos ya existentes.]{type="info"}

A continuación, desplegará una plantilla de AWS CloudFormation que creará una instancia Amazon EC2 en la cual montará el recurso compartido que creará con AWS Storage Gateway. Esta **instancia cliente** actuará como si fuera su computadora "en sitio".

1. Descargue esta :link[plantilla de CloudFormation]{href="/static/30_storagegateway/dm-lab-sg.yaml" action=download}.
2. Haga clic en **Services** y después en **CloudFormation** (también puede usar el campo de búsqueda).

![CloudFormation](/static/images/mgn/cloudformation1.png)

3. Haga clic en **Create stack** y seleccione la opción de **With new resources (standard)**.

![CloudFormation](/static/images/mgn/cloudformation2.png)

4. Seleccione **Upload a template file** y cargue la plantilla de CloudFormation que descargó anteriormente.

![CloudFormation](/static/images/mgn/cloudformation3.png)

5. Haga click en **Next**.
6. En el campo de **Stack name** escriba **storage-gateway-lab**.
7. Haga click en **Next**.
8. En la siguiente pantalla haga click de nuevo en **Next**.
9. En la siguiente pantalla seleccione la casilla de **I acknowledge that AWS CloudFormation might create IAM resources** que aparece el final.
10. Haga click en **Create stack**.

![CloudFormation](/static/images/sg/acknowledgerole.png)

11. Espere unos minutos a que el status de lanzamiento de la plantilla indique **CREATE_COMPLETE**.
12. Una vez que la plantilla haya sido desplegada, haga click en la sección de ***Outputs*** y copie el valor del parámetro ***ClientInstancePrivateIP*** (la dirección IP privada de la instancia cliente) y guárdelo en un archivo de texto ya que lo utilizará más adelante. En este apartado también encontrará el nombre del bucket que se creó para almacenar sus datos una vez que estos sean migrados.