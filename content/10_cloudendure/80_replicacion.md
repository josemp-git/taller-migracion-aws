---
draft: true
title: 8. Replicación continua de datos
weight: 80
---
A continuación, hará un cambio en el contenido de la instancia de origen para probar la funcionalidad de **Continuous Data Replication** (como es que los cambios que se hacen en el instancia de origen se están replicando continuamente al área de staging) y posteriormente lanzará de nuevo su instancia (LAUNCH 1 TARGET MACHINE), con lo cual CloudEndure eliminará la instancia que fue lanzada previamente y creará una instancia nueva con los últimos cambios que se llevaron a cabo en la instancia de origen.

1. Haga clic en **Services** (esquina superior izquierda) y posteriormente en **EC2** bajo la la categoría de **Compute**.
2. Haga clic en **Running Instances**.
3. Seleccione la instancia de **Linux Server** y haga clic en el botón de **Connect**.
4. En la pantalla de **Connect to instance** haga clic en el botón de **Connect**.
5. Una vez en el CLI de la instancia ejecute los siguientes comandos: 

:::code{showCopyAction=true showLineNumbers=false language=java}
cd /var/www/html
:::

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo wget https://taller-migracion-dev.s3.amazonaws.com/new/index.html
:::

Este último comando va a descargar un archivo **index.html** en la ruta raíz del servidor Apache (/var/www/html/) con el que se va a sustituir la página de bienvenida de Apache que vio en el módulo anterior. Esta es la modificación que hará para probar la funcionalidad de **Continuous Data Replication**. 

6. Regrese a la consola de CloudEndure y asegúrese que el status de **DATA REPLICATION PROGRESS** sea **Continuous Data Replication** y **ETA|LAG** sea **none**.
7. Repita los pasos [**1 al 7 del módulo 7**](/10_cloudendure/70_lanzamiento/) para lanzar de nuevo la instancia de tal manera que se vea reflejado el nuevo archivo index.html del servidor web Apache. 
8. Una vez que la instancia haya sido lanzada de nuevo exitosamente, obtenga la nueva IP pública [**(pasos 8 al 11 del módulo 7)**](/10_cloudendure/70_lanzamiento/) e ingrésela en el navegador para ver como es que los cambios que hizo en la instancia origen se ven reflejados en la instancia destino (debe mostrarse la nueva página que fue cargada en el paso 6 de este módulo).

##### Fin del laboratorio