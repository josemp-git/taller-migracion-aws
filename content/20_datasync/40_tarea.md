---
draft: false
title: 4. Creación de la tarea
weight: 40
---
Una vez que su agente ha sido creado, deberá crear una tarea (task). En esta tarea usted definirá parámetros tales como el tipo de ubicación origen, la dirección IP de su servidor NFS, el bucket de Amazon S3 hacia donde migrará sus datos, y el agente de DataSync que utilizará para este proceso.

1. Haga clic en **Tasks** en el menú lateral izquierdo.
2. Haga clic en **Create task**.
3. Seleccione la opción de **Choose an existing location**
4. Bajo el menú desplegable de **Existing locations** seleccione el servidor NFS.
5. Haga clic en **Next**.

![Tarea - Ubicación origen](/static/images/ds/tareaorigen.png)

6. Seleccione de nuevo la opción de **Choose an existing location**
7. Bajo el menú desplegable de **Existing locations** seleccione el bucket de Amazon S3. 
8. Haga clic en **Next**.

![Tarea - Ubicación destino](/static/images/ds/tareadestino.png)

9. En **Task Name** ingrese un nombre para su tarea (**nfs-s3-task**).
10. Bajo el apartado de **Task logging** seleccione **Log basic information such as transfer errors** del menú desplegable de **Log level**.
11. Bajo el mismo apartado de **Task logging** haga clic en el botón de **Autogenerate**.

::alert[En la pantalla de **Configure settings**, usted puede configurar diferentes opciones adicionales como habilitar la verificación de los datos, regular el ancho de banda, modificar el modo de la transferencia, filtrar archivos y directorios, y calendarizar la frecuencia de ejecución de la tarea.]{type="info"}

12. Haga clic en **Next**.
13. En la pantalla de **Review** haga clic en **Create task**.
14. Haga clic en **Tasks** en el menú lateral de la izquierda y espere a que el status de la tarea cambie a **Available**.

![Tarea disponible](/static/images/ds/tareadisponible.png)

15. Proceda al siguiente módulo.