---
draft: false
title: 3. Creación de las ubicaciones
weight: 30
---
Una vez que su agente ha sido creado, usted definirá las ubicaciones origen y destino para el proceso de migración de sus datos:

- Ubicación origen: **servidor NFS**.
- Ubicación destino: **bucket de Amazon S3**.

#### 1. Ubicación origen

1. En el servicio de DataSync, haga clic en **Locations** en el menú lateral izquierdo.
2. Haga clic en **Create location**.
3. Seleccione los siguientes parámetros:

* Location type = **Network File System (NFS)**
* Agents = **el agente de AWS DataSync que creó anteriormente**
* NFS Server =  ingrese la dirección **IP privada** de la instancia NFS que guardó en el editor de texto.

4. En **Mount path** ingrese la siguiente ruta:

:::code{showCopyAction=true showLineNumbers=false language=java}
/mnt/nfs
:::

![Ubicación origen](/static/images/ds/origen.png)

5. Haga clic en **Create location**.

#### 2. Ubicación destino

6. Haga clic de nuevo en **Locations** en el menú lateral izquierdo.
7. Haga clic en **Create location**.
8. Seleccione los siguientes parámetros:

* Location type seleccione = **Amazon S3**.
* S3 bucket = seleccione el bucket con la siguiente nomenclatura: **migration-lab-XXXXXXXXXXXX-YYYYYYY**
* S3 Storage class = **Standard**

::alert[En el menú desplegable de **S3 Storage class** usted podrá ver que AWS DataSync le permite transferir datos directamente a cualquiera de las clases de almacenamiento de Amazon S3. Si, por ejemplo, usted requiere archivar datos históricos que no necesita acceder frecuentemente, puede transferir estos datos directamente a Amazon S3 Glacier o Amazon S3 Glacier Deep Archive.]{type="info"}

9. En **IAM role** haga clic en **Autogenerate** para generar un rol que permita a AWS DataSync interactuar con su bucket.

![Ubicación origen](/static/images/ds/destino.png)

10. Haga clic en **Create location**.
11. Haga clic en **Locations**  en el menú lateral izquierdo y encontrará las dos ubicaciones que acaba de crear.

![Ubicaciones](/static/images/ds/locations.png)

12. Proceda al siguiente módulo.