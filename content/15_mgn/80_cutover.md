---
draft: false
title: 'OPCIONAL: 8. Lanzamiento en modo cutover (traspaso)'
weight: 80
---
En este módulo lanzará de nuevo su servidor, esta vez en modo cutover, y marcará el proceso de migración como finalizado, lo cual eliminará los recursos contenidos en el área de Staging.

1. Regrese a la consola de AWS MGN.
2. Seleccione la casilla de su servidor.
3. Haga clic en el menú desplegable de **Test and Cutover**.
4. Haga clic en **Mark as "Ready for cutover"**.
5. Haga clic en **Continue**.

![Continue](/static/images/mgn/continue.png)

La operación anterior eliminará la instancia de prueba que lanzó previamente y dejará marcado su servidor como listo para el traspaso (**Ready for cutover**).

![Ready for cutover](/static/images/mgn/readyforcutover1.png)
![Ready for cutover](/static/images/mgn/readyforcutover2.png)

6. Seleccione la casilla de su servidor.
7. Haga clic en **Test and cutover** y posteriormente en **Launch cutover instances**. Esto lanzará su instancia de nuevo y el valor de **Migration lifecycle** aparecerá como **Cutover in progress**.

![Ready for cutover](/static/images/mgn/cutoverinprogress1.png)
![Ready for cutover](/static/images/mgn/cutoverinprogress2.png)

Una vez terminado el proceso de lanzamiento de su instancia, deberá finalizar el proceso de traspaso.

8. Seleccione la casilla de su servidor.
9. Haga clic en **Test and cutover** y posteriormente en **Finalize cutover**.

::alert[Esta acción no puede ser revertida. Esto ocasiona que los datos y recursos contenidos en el área de Staging sean eliminados por completo, por lo cual no podrá regresar a alguno de los puntos anteriores del ciclo de vida del proceso de migración.]{type="warning"}

10. Haga clic en **Finalize**.

![Finalize cutover](/static/images/mgn/finalize.png)

La operación anterior indica que el proceso de migración ha finalizado por completo (**Migration lifecycle = Cutover complete**), la replicación de datos hacia el área de Staging también ha sido detenida (**Data replicacion status = Disconnected**), y el servidor de replicación y los datos contenidos en el área de Staging han sido eliminados.

![Cutover](/static/images/mgn/cutovercomplete1.png)
![Cutover](/static/images/mgn/cutovercomplete2.png)

11. Seleccione la casilla de su servidor. Haga clic en **Actions** y posteriormente en **Mark as archive**.
12. Haga clic en **Archive**. Esto eliminará el servidor de la lista de **Source Servers** en la consola de AWS MGN.

![Cutover](/static/images/mgn/markasarchive.png)

##### Fin del laboratorio