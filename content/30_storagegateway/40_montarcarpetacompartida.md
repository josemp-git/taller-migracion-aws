---
draft: false
title: 3. Montar carpeta compartida
weight: 30
---
1. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
2. Haga click en **Running instances**.
2. Seleccione la casilla de la Instancia **Cliente NFS**.
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

8. Ejecute el comando que guardó en el editor de texto para montar el file share en Linux sustituyendo **[MounthPath]** por la siguiente ruta:

:::code{showCopyAction=true showLineNumbers=false language=java}
/home/ec2-user/gateway
:::

9. Ejecute el siguiente comando para enlistar el contenido de la directorio compartido que acaba de montar:
:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/gateway
:::

::alert[Si ejecutó el laboratorio de AWS DataSync, encontrará los archivos que migró anteriormente.]{type="info"}

10. Ejecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/
:::

::alert[Este comando le mostrará el contenido de la ruta **/home/ec2-user/** en la que se encuentra montado el directorio compartido de la instancia Servidor NFS (**nas**) y el directorio compartido del S3 File Gateway (**gateway**). También encontrará un directorio llamado **baseball-data-2021-version** que contiene archivos CSV con estadísticas de baseball.]{type="info"}

![Comandos)](/static/images/sg/comandos1.png)

11. Ejecute el siguiente comando para copiar el directorio **baseball-data-2021-version** a la carpeta compartida que acaba de montar:

:::code{showCopyAction=true showLineNumbers=false language=java}
cp -rv /home/ec2-user/baseball-data-2021-version/ /home/ec2-user/gateway/
:::

12. Ejecute el siguiente comando para enlistar de nuevo el contenido de la directorio compartido que acaba de montar:

:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/gateway
:::

13. Ejecute el siguiente comando para enlistar el contenido del directorio que copió:

:::code{showCopyAction=true showLineNumbers=false language=java}
ls /home/ec2-user/gateway/baseball-data-2021-version
:::

![Comandos)](/static/images/sg/comandos2.png)

14. Haga click en **Services** y después en **S3**.
15. Ingrese al bucket que utilizó para crear el S3 File Gateway (**migration-lab-XXXXXXXXXXXX-YYYYYYY**).
16. Verifique que el directorio que acaba de copiar se encuentre en el bucket.

![Comandos)](/static/images/sg/bucket.png)