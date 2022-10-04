---
draft: false
title: '9. Eliminar recursos'
weight: 80
---
Para evitar cargos innecesarios, se recomienda elimnar los recursos creados durante este laboratorio una vez que lo haya concluido. Para eliminar los recursos creados ejecute los siguientes pasos:

1. Diríjase al servicio de **Application Migration Service**.
2. Seleccione la casilla del servidor que migró durante este laboratorio.
3. Haga clic en el menú desplegable de **Actions** y después en **Disconnect from service**.

![Disconnect from service](/static/images/mgn/disconnect1.png)

4. Haga clic en el botón de **Disconnect**.

![Disconnect from service](/static/images/mgn/disconnect2.png)

5. Seleccione de nuevo la casilla del servidor que migró durante este laboratorio.
6. Haga clic de nuevo en el menú desplegable de **Actions** y después en **Mark as archived**.

![Mark as archived](/static/images/mgn/archived.png)

7. Haga clic en el botón de **Archive**.

![Archive](/static/images/mgn/archive.png)

8. Diríjase al servicio de **EC2**.
9. Seleccione la casilla del servidor **Linux Migrado**.
10. Haga clic en el menú desplegable de **Instance state** y después en **Terminate instance**.

![Terminate instance](/static/images/mgn/terminate.png)

11. Haga clic en **Terminate**.
12. Haga clic en **Services** y después en **CloudFormation**.
13. Seleccione la plantilla de AWS CloudFormation que desplegó al inicio de este laboratorio (**mgn-lab**).
14. Haga clic en **Delete**

![Delete stack](/static/images/mgn/deletestack.png)

15. Haga clic en **Delete stack**.