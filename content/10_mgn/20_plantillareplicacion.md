---
draft: false
title: 2. Plantilla de replicación
weight: 20
---
La primera vez que ingresa al servicio de AWS Application Migration Service deberá configurar el servicio y crear la plantilla de configuración de replicación.

1. Haga clic en **Services** y posteriormente seleccione el servicio de **AWS Application Migration Service** (también puede usar el campo de búsqueda).
2. Haga clic en **Get started**.
3. Haga clic en **Set up service**.

::alert[Las pantallas anteriores aparecen cuando se accede por primera vez al servicio de AWS Application Migration Service. Si ya ha usado el servicio anteriormente o si las pantallas anteriores no aparecen, proceda directamente al paso 4.]{type="warning"}

4. Haga clic en **Relication template** bajo *Settings** en el menú lateral izquierdo.

![Replication template](/static/images/mgn/replicationtemplate.png)

5. Haga clic en **Edit**.

6. Bajo el apartado de **Replication server configuration** seleccione los siguientes valores:

* **Staging area subnet** = Staging Area Subnet
* **Replication Server instance type** = t3.small

![Replication server configuration](/static/images/mgn/replicationserverconfiguration.png)

7. Bajo el apartado de **Volumes** seleccione los siguientes valores:

* **EBS volume type (for replicating disks over 500GiB)** = Lower cost, Throughput Optimized HHD (st1)
* **EBS encryption** = Default

![Volumes](/static/images/mgn/volumes.png)

El resto de los parámetros deben permanecer con sus valores predeterminados.

8. Haga clic en **Save template**.
9. Proceda al siguiente módulo.

::alert[Si en el futuro requiere modificar esta configuración, puede hacerlo en el apartado de **Settings** del menú lateral de la consola de AWS MGN.]{type="info"}