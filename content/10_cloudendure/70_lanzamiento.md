---
draft: false
title: 7. Lanzamiento del servidor migrado
weight: 70
---
Antes de lanzar su instancia en la ubicación destino de manera definitiva, debe llevar a cabo lanzamientos en modo prueba. 
Al llevar a cabo estas pruebas, usted podrá verificar que su instancia de origen funciona correctamente en la ubicación destino. 
La ejecución del lanzamiento en modo de prueba se puede realizar después de que se haya completado la etapa inicial de sincronización y una vez que se haya configurado adecuadamente el [blueprint](/10_cloudendure/60_blueprint/) para la instancia (módulo anterior).

1. Diríjase de nuevo a la sección de **Machines** en la consola de CloudEndure.
2. Seleccione la casilla del servidor **Linux Server** y diríjase al menú desplegable de **LAUNCH 1 TARGET MACHINE** que se encuentra en la derecha de la consola de CloudEndure. 
3. De las dos opciones que se presentan en el menú desplegable, seleccione **Test Mode**.

![Test mode](/static/images/ce/testmode.png)

4. En la siguiente pantalla haga clic en **Continue** y esto dará comienzo al proceso de lanzamiento de su instancia en la VPC  que creó al inicio de este laboratorio.
5. Una vez iniciado este proceso, diríjase a la sección de **Job Progress** del menú de la izquierda de la consola de CloudEndure para ver el status del lanzamiento.

![Job Progress](/static/images/ce/inprogress.png)

6. Una vez que el proceso de lanzamiento haya terminado satisfactoriamente, verá una barra verde al lado del nombre de su servidor y bajo el apartado de **MIGRATION LIFECYCLE** verá el status de **Tested (X minutes/hours ago)**.

![Tested X minutes ago](/static/images/ce/tested.png)

7. Si el proceso de lanzamiento ya terminó, diríjase de nuevo al apartado de **Job Progress** y verá el status de **Launch Test** como **Completed Successfully**.
8. Haga clic en la sección de **Machines** de la consola de CloudEndure.
9. Haga clic sobre **Linux Server** (sobre el nombre del servidor como tal, no seleccione la casilla) para ver los detalles del servidor que acaba de migrar.
10. Haga clic en la pestaña de **TARGET** y copie la IP pública del apartado de **Public IPs**.

![Job Progress](/static/images/ce/targetip.png)

11. Ingrese esta IP en su navegador web y podrá ver el mensaje de bienvenida de Apache que vio en la instancia de origen:

![Apache](/static/images/ce/apache.png)

Su servidor ha sigo migrado a una nueva ubicación y probado satisfactoriamente. 

12. Proceda al siguiente módulo.