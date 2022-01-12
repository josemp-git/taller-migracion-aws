---
draft: false
title: 7. Replicación continua de datos
weight: 70
---
A continuación, hará un cambio en el contenido de la instancia de origen para probar la funcionalidad de **Replicación continua de datos** (como es que los cambios que se hacen en el instancia de origen se están replicando continuamente al área de staging) y posteriormente lanzará de nuevo su instancia, con lo cual AWS MGN eliminará la instancia que fue lanzada previamente y creará una instancia nueva con los últimos cambios que se llevaron a cabo en la instancia de origen.

1. Haga clic en **Services** y posteriormente en **EC2**.
2. Haga clic en **EC2 Dashboard** y después en **Instances (running)**.
3. Seleccione la instancia de **Servidor Linux** y haga clic en el botón de **Connect**.
4. En la pantalla de **Connect to instance** haga clic en el botón de **Connect**.
5. En el CLI de la instancia ejecute los siguientes comandos: 

:::code{showCopyAction=true showLineNumbers=false language=java}
cd /var/www/html
:::

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo mv index.html index.html.bak
:::

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo wget https://migracion.workshop.aws/15_mgn/new/index.html
:::

Este último comando descargará un archivo **index.html** en la ruta raíz del servidor Apache (/var/www/html/) con el que se sustituirá el mensaje anterior con uno nuevo. Esta es la modificación que hará para probar la funcionalidad de **Replicación continua de datos**. 

6. Regrese a la consola de AWS MGN.
7. Seleccione la casilla de su servidor.
8. Haga clic en el menú desplegable de **Test and Cutover**.
9. Haga clic en **Revert to "Ready for testing"**.
10. Haga clic en **Revert**.

![Revert testing for 1 server](/static/images/mgn/revert.png)

Esta operación eliminará el servidor que fue lanzado previamente y dejará su servidor listo para ser probado de nuevo (**Migration lifecycle = Ready for testing**).

11. Seleccione de nuevo la casilla de su servidor.
12. Haga clic de nuevo en el menú desplegable de **Test and Cutover**.
13. Haga clic en **Launch test instances**. 
14. Haga clic en **Launch**.

Lo anterior lanzará de nuevo su instancia con los cambios que se hicieron en el servidor origen y que ya fueron replicados al área de Staging.

15. Haga clic en **Launch history**.
16. Haga clic en el **Job ID** correspondiente al lanzamiento que acaba de realizar para monitorear el progreso.

Una vez que el lanzamiento haya concluido, el servidor mostrará de nuevo el estado de **Launched** bajo la columna de **Alerts** y **Test in progress** bajo la columna de **Migration lifecycle** en la consola de AWS MGN.

![Servidor lanzado en modo prueba](/static/images/mgn/lanzado.png)

17. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2**.
18. Seleccione la casilla de la instancia **Linux migrado**.
19. Bajo el apartado de **Details** copie la dirección IP pública (Public IPv4 address) y péguela en su navegador y corrobore que, en esta ocación, se despliega un mensaje diferente al que se mostraba originalmente en el servidor de origen.

::alert[Usted puede repetir estos pasos para llevar a cabo cuantas pruebas considere pertinentes previo a la migración final. Una vez que haya hecho las pruebas necesarias, deberá marcar sus servidores como listos para el trapaso (cutover).]{type="info"}

20. Proceda al siguiente módulo.