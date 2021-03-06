---
draft: false
title: 4. Comenzar la migración
weight: 40
---
Una vez que su tarea haya sido creada con todos los parámetros necesarios, deberá iniciar esta tarea para comenzar el proceso de migración de datos.

1. Haga clic en **Tasks** en el menú lateral de la izquierda.
2. Seleccione la casilla de su tarea.
3. Asegúrese de que el status de su tarea sea **Available**.
3. Haga clic en el menú desplegable de **Actions**.

![Start task](/static/images/ds/iniciartarea.png)

4. Haga clic en **Start**. Podrá ver como el status de su tarea cambió a **Running**. Espere unos minutos a que la tarea de migración termine y el status de su tarea cambie de nuevo a **Available**.

![Task running](/static/images/ds/tareaejecutando.png)

5. Espere a que el status de la tarea cambie de nuevo a **Available**. Este cambio indicará que la tarea de migración ha concluido.
6. Haga clic en **History** bajo **Tasks** en el menú lateral izquierdo. Aquí podrá corroborar que su tarea de migración se ejecutó satisfactoriamente.

![Task history](/static/images/ds/tareahistory.png)

::alert[Haga clic en el valor de **Execution ID** si desea conocer más detalles acerca de la ejecución de su tarea.]{type="info"}

7. Haga clic en **Services** y posteriormente seleccione el servicio de **S3**.
8. Haga clic en el bucket que creó anteriormente y corrobore que los archivos que migró se encuentran ahí.