---
draft: false
title: 3. Plantilla de lanzamiento
weight: 30
---
1. En la consola de AWS MGN, haga clic en **Launch template** bajo **Settings** en el menú lateral izquierdo.

![Launch settings](/static/images/mgn/launchsettings.png)

2. Haga clic en **Edit**.
3. Bajo el apartado de **General launch settings**, desactive la funcionalidad de **Activate instance type right-sizing** .

![General launch settings](/static/images/mgn/generallaunchsettings.png)

4. Bajo el apartado de **Default EC2 Launch Template**, efectúe los siguientes cambios:

* Default target subnet =  **Target Subnet**
* Additional security groups = **MGN Lab SG**
* EBS volume type =  **General Purpose SSD (gp3)**

![Default EC2 Launch Template](/static/images/mgn/defaultec2launchtemplate.png)

5. Haga clic en **Save template**.

6. En el apartado de **EC2 Launch Template**, guarde el **Template ID** en un archivo de texto ya que lo utilizará más tarde.
7. Haga clic en **Modify**.
8. Haga clic de nuevo en **Modify**.

::alert[Lo anterior lo llevará a modificar la plantilla de lanzamiento, en la cual creará una nueva versión con los parámetros necesarios para hacer las pruebas de lanzamiento de su servidor.]{type="info"}

9. Ingrese :code[mgn-lab-template]{showCopyAction=true} en el campo de **Template version description**.
10. Bajo el apartado de **Instance type** seleccione **t2.micro** del menú desplegable.

![Instance type](/static/images/mgn/instancetype.png)

11. En el apartado de **Network settings** seleccione la subred llamada **Target subnet - MGN lab** bajo el menú desplegable de **Subnet**.
12. Seleccione la opción de **Select existing security group**.
13. En el menú desplegable de **Common security groups** seleccione el grupo de seguridad llamado **MGN lab SG Destino**.

![Red](/static/images/mgn/networksettings1.png)

14. Bajo el apartado de **Advanced network configuration** seleccione **Enable** en el menú desplegable de **Auto-assign public IP**.

![Red](/static/images/mgn/networksettings2.png)

15. Bajo el apartado de **Storage (volumes)** haga clic sobre **Volume 1 (Custom)** para desplegar las opciones de configuración.
16. En **Volume type** seleccione la opción de **standard** del menú desplegable.


![Storage Settings](/static/images/mgn/storagesettings.png)

17. Bajo el apartado de **Resource tags** ingrese :code[Linux migrado]{showCopyAction=true} en el campo **Value** de la llave **Name**.

![Etiquetas](/static/images/mgn/nametag.png)

18. Haga clic en **Create template version**.
19. Anote el ID de su plantilla.

![Etiquetas](/static/images/mgn/launchtemplateid.png)

20. Haga clic en **View launch templates**.
21. Seleccione su plantilla (**Launch template ID**).
22. Haga clic en **Actions** y posteriormente en **Set default version**.

![Set default version](/static/images/mgn/setdefaultversion.png)

23. Bajo el menú desplegable de **Template version** seleccione la versión que creó previamente (**mgn-lab-template**)
24. Haga clic en **Set as default version**.

![Set default version](/static/images/mgn/setdefaultversion2.png)

25. Regrese al servicio de AWS MGN y verifique que los cambios efectuados en la plantilla se ven reflejados en ela sección de **Launch settings**.

![EC2 Launch Template](/static/images/mgn/ec2launchtemplatemodified.png)

26. Proceda al siguiente módulo.

::alert[Para más información acerca de la configuración del lanzamiento, puede consultar la documentación disponible: [Launch settings](https://docs.aws.amazon.com/mgn/latest/ug/launch-settings.html)]{type="info"}