---
draft: false
title: 6. Configuración del Blueprint
weight: 60
---
En el apartado de Blueprint se definen los parámetros necesarios para el lanzamiento del servidor tales como la subred, direcciones IP, roles IAM, grupos de seguridad y tipo de disco, entre otros.
En este módulo usted configurará algunos de los parámetros necesarios para ejecutar esta migración satisfactoriamente.

1. Diríjase a la sección de **Machines** en la consola de CloudEndure.
2. Haga clic sobre **Linux Server** (sobre el nombre del servidor como tal, no seleccione la casilla) para ver los detalles del servidor que acaba de migrar.
3. En la nueva pantalla haga clic en la pestaña de **BLUEPRINT** del lado derecho.
4. En el menú desplegable de **Machine Type** usted puede elegir el tipo de instancia para su servidor. En este caso asegúrse de elegir el parámetro de **Copy Source**, con lo cual CloudEndure definirá una instancia con características similares a las del servidor de origen.

![Copy Source](/static/images/ce/copysource.png)

5. En el menú desplegable de **Launch Type** asegúrase de seleccionar el valor de **On demand**.

![On demand](/static/images/ce/ondemand.png)

6. Usted debe definir en qué subnet se encontrará su servidor una vez que haya sido migrado. Para esto, en el menú desplegable de **Subnet**, elija la subnet destino de la VPC CloudEndureLab **(Target Subnet – CloudEndureLab)**.

![Target subnet](/static/images/ce/targetsubnet.png)

7. En el menú desplegable de **Private IP** seleccione **Create new**.

![Private IP](/static/images/ce/privateip.png)

8. En el apartado de **tags** puede ingresar etiquetas para identificar su servidor una vez que haya sido migrado a AWS. Ingrese la etiqueta con llave **Name** y el valor de **SERVIDOR MIGRADO**.

![Tag](/static/images/ce/tag.png)

9. En el apartado de **Disks** usted puede elegir el tipo de disco que mejor se ajuste a las necesidades de IOPs y throughput de los volúmenes de su servidor. Para efectos de este laboratorio, del menú desplegable elija **Standard**.
10. Haga clic en **SAVE BLUEPRINT**.
11. Proceda al siguiente módulo.