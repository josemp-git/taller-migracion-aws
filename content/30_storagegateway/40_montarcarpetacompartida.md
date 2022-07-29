---
draft: false
title: 4. Montar carpeta compartida
weight: 40
---
1. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
2. Haga click en **Running instances**.
2. Seleccione la casilla que se encuentra a lado de la **Instancia cliente**.
4. Haga click en **Connect**.
5. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect** para tener acceso a su instancia vía SSH por medio del navegador web.

![Connect (browser-based SSH connection)](/static/images/sg/conectarec2.png)

6. Ejecute el siguiente comando para obtener privilegio root:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo su
:::

7. Para montar su file share debe crear un directorio en donde montarlo; para esto jecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
mkdir /home/ec2-user/gateway
:::

8. Ejecute el comando que guardó en el editor de texto para montar el file share en Linux sustituyendo **_[MounthPath]_** por la siguiente ruta:

:::code{showCopyAction=true showLineNumbers=false language=java}
/home/ec2-user/gateway
:::

9. Ejecute el siguiente comando para enlistar el contenido de la directorio compartido que acaba de montar:
:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/gateway
:::

::alert[Si ejecutó el laboratorio de AWS DataSync y utilizó los mismos recursos para este laboratorio, encontrará los archivos que migró anteriormente.]{type="info"}

10. Dentro de la ruta en la que se encuentra hay un directorio llamado **_baseball-data-2021-version_** que contiene archivos CSV con estadísticas de baseball. Ejecute el siguiente comando para copiar estos archivos al recurso compartido que acaba de montar:

:::code{showCopyAction=true showLineNumbers=false language=java}
cp -rv /home/ec2-user/baseball-data-2021-version/ /home/ec2-user/gateway/
:::

11. Ejecute el siguiente comando para enlistar de nuevo el contenido de la directorio compartido que acaba de montar:

:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/gateway
:::

12. Ejecute el siguiente comando para enlistar el contenido del directorio que copió:

:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/gateway/baseball-data-2021-version
:::

![Comandos)](/static/images/sg/comandos.png)

13. Haga click en **_Services_** y después en ***S3***.
14. Ingrese al bucket que creó la plantilla de CloudFormation para este laboratorio.
15. Verifique que el directorio que acaba de copiar se encuentre en el bucket.