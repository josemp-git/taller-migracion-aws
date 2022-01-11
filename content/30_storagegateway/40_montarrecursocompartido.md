---
draft: false
title: 4. Montar recurso compartido
weight: 40
---
1. Haga click en **_Services_** y posteriormente seleccione el servicio de **_EC2_**.
2. Haga click en **_Running instances_**.
2. Seleccione la casilla que se encuentra a lado de la instancia **Instance cliente**.
4. Haga click en **_Connect_**.
5. Seleccione ***EC2 Instance Connect*** y haga click en ***Connect*** para tener acceso a la instancia cliente vía SSH por medio del navegador web.

![Connect (browser-based SSH connection)](/static/images/sg/conectarec2.png)

6. Ejecute el siguiente comando para obtener privilegio root:

```
sudo su
```

7. Para montar su file share debe crear un directorio en donde montarlo; para esto jecute el siguiente comando:

```
mkdir /home/ec2-user/gateway
```

8. Ejecute el comando que guardó en el editor de texto para montar el file share en Linux sustituyendo **_[MounthPath]_** por la siguiente ruta:

```
/home/ec2-user/gateway
```

9. Ejecute el siguiente comando para enlistar el contenido de la directorio compartido que acaba de montar (si llevó a cabo los módulos de AWS DataSync encontrará los archivos que migró anteriormente):

```
ls /home/ec2-user/gateway
```

10. Dentro de la ruta en la que se encuentra hay un directorio llamado **_baseball-data-2018-version_** que contiene archivos CSV con estadísticas de baseball. Ejecute el siguiente comando para copiar estos archivos al recurso compartido que acaba de montar:

```
cp -rv /home/ec2-user/baseball-data-2018-version/ /home/ec2-user/gateway/
```

11. Ejecute de nuevo el comando del paso 9 para corroborar que el directorio **_baseball-data-2018-version_** se copió correctamente al recurso compartido.
12. Ejecute el siguiente comando para enlistar el contenido del directorio que copió:

```
ls /home/ec2-user/gateway/baseball-data-2018-version
```

13. Haga click en **_Services_** y después en ***S3***.
14. Ingrese al bucket que creó para este laboratorio.
15. Verifique que el directorio que acaba de copiar se encuentre en el bucket.