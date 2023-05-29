---
draft: false
title: 5. Ajustes
weight: 50
---
1. En la consola de AWS MGN, haga clic en **Source servers** en el menú lateral izquierdo.
2. Haga clic en el nombre del servidor que va a migrar bajo la columna de **Source server name**.
3. Haga clic en **Launch settings**.

![Instance type](/static/images/mgn/launchsettings2.png)

4. Anote el template ID que se encuentra en el apartado de **EC2 Launch Template** y haga clic en **Modify**.

![Modify EC2 Launch Template](/static/images/mgn/modifyec2launchtemplate.png)

5. Haga clic de nuevo en **Modify**.

::alert[Lo anterior lo llevará a modificar la plantilla de lanzamiento específica para este servidor, y creará una nueva versión con los parámetros necesarios para hacer las pruebas de lanzamiento de su servidor.]{type="info"}

6. Ingrese :code[Plantilla Servidor Web]{showCopyAction=true} en el campo de **Template version description**.

![Instance type](/static/images/mgn/plantillaservidorweb.png)

10. Bajo el apartado de **Instance type** seleccione **t2.micro** del menú desplegable.

![Instance type](/static/images/mgn/instancetype.png)

11. En el apartado de **Network settings** haga clic en **Advanced network configuration**.
12. seleccione **Enable** en el menú desplegable de **Auto-assign public IP**.

![Red](/static/images/mgn/networksettings.png)

13. Bajo el apartado de **Resource tags** ingrese :code[Servidor Web MIGRADO]{showCopyAction=true} en el campo **Value** de la llave **Name**.

![Etiquetas](/static/images/mgn/nametag.png)

14. Haga clic en **Create template version**.
15. Haga clic en **View launch templates**.
16. Seleccione su plantilla (**Launch template ID**).
17. Haga clic en **Actions** y posteriormente en **Set default version**.

![Set default version](/static/images/mgn/setdefaultversion.png)

18. Bajo el menú desplegable de **Template version** seleccione la versión que creó previamente (**Plantilla Servidor Web**)
19. Haga clic en **Set as default version**.

![Set default version](/static/images/mgn/setdefaultversion2.png)

20. Regrese al servicio de AWS MGN y verifique que los cambios efectuados en la plantilla se ven reflejados en ela sección de **Launch settings**.

![EC2 Launch Template](/static/images/mgn/ec2launchtemplatemodified.png)

21. Proceda al siguiente módulo.

::alert[Para más información acerca de la configuración del lanzamiento, puede consultar la documentación disponible: [Launch settings](https://docs.aws.amazon.com/mgn/latest/ug/launch-settings.html)]{type="info"}