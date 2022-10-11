---
draft: false
title: 3. Creación de las ubicaciones
weight: 30
---
Una vez que su agente ha sido creado, usted definirá las ubicaciones origen y destino para el proceso de migración de sus datos:

- Ubicación origen: **servidor NFS**.
- Ubicación destino: **bucket de Amazon S3**.

##### 1. Ubicación origen

1. En el servicio de DataSync, haga clic en **Locations** en el menú lateral izquierdo.
2. Haga clic en **Create location**.
3. En **Location type** seleccione **Network File System (NFS)**.
4. En **Agents** seleccione el agente de AWS DataSync que creó anteriormente.
5. En **NFS Server** ingrese la **IP PRIVADA** de la instancia NFS que guardó en el editor de texto.
6. En **Mount path** ingrese la siguiente ruta:

:::code{showCopyAction=true showLineNumbers=false language=java}
/mnt/nfs
:::

7. Haga clic en **Create location**.

![Ubicación origen](/static/images/ds/origen.png)

##### 2. Ubicación destino

8. Haga clic de nuevo en **Locations** en el menú lateral izquierdo.
9. Haga clic en **Create location**.
10. En **Location type** seleccione **Amazon S3**.
11. En **S3 bucket** seleccione el bucket que creó la plantilla de CloudFormation (data-migration-lab-XXXXXXXXXXXX-YYYYYYY).
12. En **S3 Storage class** seleccione **Standard**.

::alert[En el menú desplegable de **S3 Storage class** usted podrá ver que AWS DataSync le permite transferir datos directamente a cualquiera de las clases de almacenamiento de Amazon S3. Si, por ejemplo, usted requiere archivar datos históricos que no necesita acceder frecuentemente, puede transferir estos datos directamente a Amazon S3 Glacier o Amazon S3 Glacier Deep Archive.]{type="info"}

13. En **IAM role** haga clic en **Autogenerate** para generar un rol que permita a AWS DataSync interactuar con su bucket.

14. Haga clic en **Create location**.

![Ubicación origen](/static/images/ds/destino.png)

15. Haga clic en **Locations** y encontrará las dos ubicaciones que acaba de crear.

![Ubicaciones](/static/images/ds/locations.png)

16. Proceda al siguiente módulo.