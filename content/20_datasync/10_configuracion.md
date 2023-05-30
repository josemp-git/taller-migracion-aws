---
draft: false
title: 1. Configuración del cliente NFS
weight: 10
---
A continuación se conectará a la instancia cliente para montar el recurso compartido por el servidor NFS y así poder acceder a los datos contenidos en este recurso.

1. Haga click en **Services** y posteriormente seleccione el servicio de **EC2**.
2. Haga click en **Running instances**.
3. Seleccione la casilla  **Cliente NFS*.
4. Copie la dirección *IP privada (Private IPv4 addresses)* y guárdela en un archivo de texto ya que la usará más adelante.

![Copiar dirección IP privada](/static/images/ds/ipprivada.png)

5. Haga clic en el botón de **Connect**.

![Connect to Linux Server](/static/images/ds/connect1.png)

6. En la pantalla de **Connect to instance** haga clic en **Session Manager** y después en **Connect**.

![Connect to NFS Client](/static/images/ds/connect2.png)

7. Una vez conectado a su instancia cliente ejecute el siguiente comando sustituyendo el parámetro **NFSInstancePrivateIP** por la dirección IP correspondiente que guardó en el editor de texto:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo mount -t nfs NFSInstancePrivateIP:/mnt/nfs /home/ec2-user/nas
:::

::alert[Este comando montará un directorio compartido por la instancia que funge como servidor NFS.]{type="info"}

8. Proceda a explorar el contenido de este directorio con los siguientes comandos:

:::code{showCopyAction=true showLineNumbers=false language=java}
sudo ls /home/ec2-user/nas
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
sudo ls /home/ec2-user/nas/baseballdatabank-master/
:::
:::code{showCopyAction=true showLineNumbers=false language=java}
sudo ls /home/ec2-user/nas/baseballdatabank-master/core
:::

::alert[En este directorio compartido encontrará información estadística de baseball de los últimos 20 años. En este laboratorio usted migrará esta información histórica a un bucket de Amazon S3 utilizando AWS DataSync.]{type="info"}

![EC2 CLI](/static/images/ds/explorenfs.png)

9. Ejecute el siguiente comando:

:::code{showCopyAction=true showLineNumbers=false language=java}
aws ssm get-parameter --name /aws/service/datasync/ami --region us-east-1
:::

10. Copie el valor parámetro de **value** (sin las comillas) y guárdelo en un archivo de texto ya que lo utilizará en el siguiente módulo.

![Copy AMI id](/static/images/ds/copyami-id.png)

::alert[La ejecución de este comando le permite conocer la versión más reciente de la AMI del agente de AWS DataSync (ami-id).]{type="info"}

11. Proceda al siguiente módulo.