---
draft: false
title: 3. Creación de la tarea
weight: 30
---
Una vez que su agente ha sido creado, deberá crear una tarea (task). En esta tarea usted definirá parámetros tales como el tipo de ubicación origen, la dirección IP de su servidor NFS, el bucket de Amazon S3 hacia donde migrará sus datos, y el agente de DataSync que utilizará para este proceso.

1. Haga clic en **Tasks** en el menú lateral izquierdo.
2. Haga clic en **Create task**.
3. En **Location type** seleccione **Network File System (NFS)**.
4. En **Agents** seleccione el agente de AWS DataSync que creó anteriormente.
5. En **NFS Server** ingrese la IP del parámetro **NFSInstancePrivateIP** que guardó en el editor de texto.
6. En **Mount path** ingrese la siguiente ruta:

```
/mnt/nfs
```

![Tarea - ubicación origen](/static/images/ds/tareaorigen.png)

7. Haga clic en **Next**.
8. En **Location type** seleccione **Amazon S3 bucket**.
9. En **S3 bucket** seleccione el bucket que creó anteriormente.
10. En **S3 Storage class** seleccione **Standard**.

::alert[En el menú desplegable de **S3 Storage class** usted podrá ver que AWS DataSync le permite transferir datos directamente a cualquiera de las clases de almacenamiento de Amazon S3. Si, por ejemplo, usted requiere archivar datos históricos que no necesita acceder frecuentemente, puede transferir estos datos directamente a Amazon S3 Glacier o Amazon S3 Glacier Deep Archive.]{type="info"}

11. En **IAM role** haga clic en **Autogenerate** para generar un rol que permita a AWS DataSync interactuar con su bucket.

![Tarea - Ubicación destino](/static/images/ds/tareadestino.png)

12. Haga clic en **Next**
13. En **Task Name** ingrese un nombre para su tarea.
14. En **Task logging** seleccione **Log basic information such as transfer errors** del menú desplegable de **Log level**.
15. Haga clic en el botón de **Autogenerate**.

::alert[En la pantalla de **Configure settings**, usted puede configurar diferentes opciones adicionales como habilitar la verificación de los datos, regular el ancho de banda, modificar el modo de la transferencia, filtrar archivos y directorios, y calendarizar la frecuencia de ejecución de la tarea.]{type="info"}

16. Haga clic en **Next**.
17. En la pantalla de **Review** haga clic en **Create task**.
18. Haga clic en **Tasks** en el menú lateral de la izquierda. Usted podrá ver que la tarea se está creando (**status = Creating**).

![Creando tarea](/static/images/ds/creandotarea.png)

19. Espere unos minutos a que el status de la tarea cambie a **Available**.

![Tarea disponible](/static/images/ds/tareadisponible.png)

20. Proceda al siguiente módulo.