---
draft: true
title: 5. Instalación del agente de CloudEndure
weight: 50
---
CloudEndure es una solución de migración a la nube basada en agentes que le permite migrar todas las aplicaciones y bases de datos que se ejecuten en versiones soportadas de sistemas operativos Windows y Linux. A continuación, instalará el agente de CloudEndure en la instancia que va a migrar para lo cual debe regresar a la consola de AWS y llevar a cabo los siguientes pasos:

1. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2** el cual se encuentra bajo la categoría de **Compute**.
2. Haga clic en **Running instances**.
3. Seleccione la casilla que se encuentra a lado de la instancia **Linux Server**.
4. Haga clic en el botón de **Connect**.

![Connect to Linux Server](/static/images/ce/connect1.png)

5. En la pantalla de **Connect to instance** haga clic en **Connect** para tener acceso a su instancia vía SSH por medio del navegador web.

![Connect to Linux Server](/static/images/ce/connect2.png)

6. Regrese la consola de ClouedEndure y diríjase a la sección de **Machines** del menú de la izquierda. En esta sección se le indican los comandos que debe ejecutar para descargar e instalar el agente de CloudEndure tanto en Linux como en Windows. En este caso va a migrar una instancia Linux así que los comandos que va a utilizar son los que se indican en el apartado de **For Linux Machines**.

![Agent Installation](/static/images/ce/commands.png)

7. Copie los comandos directamente de la consola de CloudEndure y ejecútelos sobre el CLI de su instancia. Una vez que el agente haya sido instalado correctamente verá el status de **Installation finished successfully**.

![Installation finished successfully](/static/images/ce/cli.png)

8. Regrese a la consola de CloudEndure y vaya a la sección de **Machines**. Bajo la sección de **DATA REPLICATION PROGRESS** podrá ver el avance del proceso de replicación de la instancia.

![Installation finished successfully](/static/images/ce/replication.png)

9. Después de este último paso, deberá esperar unos minutos hasta que el proceso de replicación sea completado. Una vez que el proceso de replicación termine, bajo **DATA REPLICATION PROGRESS** verá el status de **Continuous Data Replication**, bajo **ETA|LAG** verá **n/a|none** y bajo **MIGRATION LIFECYCLE** verá **Ready for Testing**.

![Ready for testing](/static/images/ce/readyfortesting.png)

10. En lo que el proceso de replicación termina, haga clic en la sección de **Machines**.
11. Haga clic sobre **Linux Server** (sobre el nombre del servidor como tal, no seleccione la casilla) para ver los detalles del servidor que está en proceso de replicación.
12. Haga clic en la pestaña de **SOURCE** y copie la IP pública del apartado de **Public IPs**.

![Source IP](/static/images/ce/sourceip.png)

13. Ingrese esta IP en su navegador web y podrá ver el mensaje de bienvenida del servidor web Apache que está instalado en la instancia:

![Apache](/static/images/ce/apache.png)

14. Guarde esta IP pública en un editor de notas ya que podrá utilizarla más tarde.
15. Proceda al siguiente módulo.