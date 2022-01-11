---
draft: false
title: 3. Plantilla de configuración de replicación
weight: 30
---
La primera vez que ingresa al servicio de AWS Application Migration Service deberá configurar el servicio y crear la plantilla de configuración de replicación.

1. Haga clic en **Services** y posteriormente seleccione el servicio de **AWS Application Migration Service** que se encuentra bajo el rubro de **Migration & Transfer**.
2. Haga clic en **Get started**.
3. En la siguiente pantalla seleccione los siguientes parámetros bajo el apartado de **Create Replication Settings template**:

* **Staging area subnet** = Staging area subnet - MGN lab
* **Replication Server instance type** = mantenga el valor predeterminado
* **EBS volume type** = Lower cost
* **EBS encryption** = Default

![Plantilla de configuración de replicación](/static/images/mgn/configplantilla.png)

El resto de los parámetros deben permanecer con sus valores predeterminados.

4. Haga clic en **Create template**.
5. Proceda al siguiente módulo.

::alert[Si en el futuro requiere modificar esta configuración, puede hacerlo en el apartado de **Settings** del menú lateral de la consola de AWS MGN.]{type="info"}