---
draft: false
pre: <b style="color:#fff;">5. </b>
title: Eliminar recursos
weight: 50
---
Para evitar cargos innecesarios, se recomienda elimnar los recursos creados durante este laboratorio una vez que lo haya concluido. Para eliminar los recursos creados ejecute los siguientes pasos:

1. Haga clic en **Services** y después en **EC2**.
2. Seleccione la casilla de la instancia **Agente AWS DataSync**
3. Haga clic en el botón de **Instance state**.
4. Haga clic en **Terminate instance** en el menú desplegable.
5. Haga clic en **Services** y después en **CloudFormation**.
6. Haga clic en **Stacks** en el menú lateral izquierdo.
7. Seleccione la plantilla de AWS CloudFormation que desplegó al inicio de este laboratorio.
8. Haga clic en el botón de **Delete**. Esto eliminará la VPC y las instancias (Cliente y Servidor NFS) creadas al inicio.
9. Haga clic en **Services** y después en **S3**.
10. Seleccione el bucket que creó para este laboratorio.
11. Haga clic en **Empty** y siga las instrucciones que aparecen a continuación (esto eliminará los datos alojados en el bucket).
12. Regrese a la consola de S3 y seleccione de nuevo su bucket.
13. Haga clic en el botón de **Delete** y siga las instrucciones que aparecen a continuación (esto eliminará el bucket).