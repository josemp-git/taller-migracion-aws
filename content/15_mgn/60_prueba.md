---
draft: false
title: 6. Lanzamiento en modo prueba
weight: 60
---
Antes de lanzar su instancia en la ubicación destino de manera definitiva, debe llevar a cabo lanzamientos en modo prueba. Al llevar a cabo estas pruebas, usted podrá verificar que su servidor origen funciona correctamente en la ubicación destino. La ejecución del lanzamiento en modo de prueba se puede realizar después de que se haya completado la etapa inicial de sincronización y una vez que se haya configurado adecuadamente la plantilla de lanzamiento (módulo anterior).

1. Haga clic en **Source Servers** en el menú lateral izquierdo del servicio de AWS MGN.
2. Verifique el estado de los siguientes parámetros:

* **Migration lifecyle** = Ready for testing
* **Data replication status** = Healthy

![Data replication status = Healthy](/static/images/mgn/statushealthy.png)

Esto significa que el proceso de replicación se ha completado al 100%, por lo tanto su servidor ya puede ser lanzado en modo de prueba.

::alert[Si hace clic en el nombre de su servidor, también podrá verificar el estado de **Ready for testing** del ciclo de vida del proceso de migración.]{type="info"}

![Ready for testing](/static/images/mgn/readyfortesting.png)

3. Seleccione la casilla de su servidor.
4. Haga clic en el menú desplegable de **Test and Cutover**.
5. Haga clic en **Launch test instances**. 
6. Haga clic en **Launch**. Esto lanzará su instancia en modo de prueba de acuerdo a los parámetros especificados en la plantilla de lanzamiento.

7. Haga clic en **Launch history**. En **Launch history** se guarda el historial de lanzamientos que se hacen en modo de prueba y cutover.
8. Haga clic en el **Job ID** correspondiente al lanzamiento que acaba de realizar para monitorear el progreso. También puede hacer clic en el botón de **View job details** que apareció en la esquina superior derecha.

![View job details](/static/images/mgn/viewjobdetails.png)

Una vez que el lanzamiento haya concluido, el servidor mostrará el estado de **Launched** bajo la columna de **Alerts** y **Test in progress** bajo la columna de **Migration lifecycle** en la consola de AWS MGN.

![Servidor lanzado en modo prueba](/static/images/mgn/lanzado.png)

::alert[Si hace clic en el nombre de su servidor, podrá verificar también el estado de **Test in progress** del ciclo de vida del proceso de migración.]{type="info"}

![Test in progress](/static/images/mgn/testinprogress.png)

9. Haga clic en **Services** y posteriormente seleccione el servicio de **EC2**.
10. Haga clic en **EC2 Dashboard** y después en **Instances (running)**. En la consola de Amazon EC2 verá su servidor origen (Servidor Linux) y el servidor que acaba de lanzar con el nombre de **Linux migrado**. Si selecciona la casilla de cada uno de los servidores, podrá ver bajo el apartado de **Details** que cada uno pertenece a una VPC, subred y segmentos de red diferentes.

11. Seleccione la casilla de la instancia **Linux migrado**.
12. Bajo el apartado de **Details** copie la dirección IP pública (Public IPv4 address) y péguela en su navegador y corrobore que se despliega el mismo mensaje que se mostraba en el servidor de origen.
 
![Este servidor será migrado utilizando AWS Application Migration Service](/static/images/mgn/seramigrado.png)

13. Proceda al siguiente módulo.