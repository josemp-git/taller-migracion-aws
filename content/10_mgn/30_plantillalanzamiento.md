---
draft: false
title: 3. Plantilla de lanzamiento
weight: 30
---
En este módulo usted configurará la plantilla de lanzamiento para los servidores que migrará a AWS.

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