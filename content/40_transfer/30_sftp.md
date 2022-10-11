---
draft: false
title: 3. Creación del servidor SFTP
weight: 30
---
1. Haga clic en **Services** y diríjase al servicio de **AWS Transfer Family**.
2. Haga clic en **Create server**.
3. En **Choose protocols** seleccione **SFTP (SSH File Transfer Protocol) - file transfer over Secure Shell** y haga clic en **Next**.

![Protocol](/static/images/tr/protocolo.png)

4. En **Choose an identity provider** seleccione **Service managed** y haga clic en **Next**.

![Identity provider](/static/images/tr/identityprovider.png)

5. En **Endpoint configuration** seleccione **Publicly accesible** y haga clic en **Next**.

![Identity provider](/static/images/tr/endpointconfiguration.png)

6. En **Domain** seleccione **Amazon S3** y haga clic en **Next**.

![Domain](/static/images/tr/domain.png)

7. En **Configure additional details** mantenga los valores predeterminados y haga clic en **Next**.
8. En **Review and create** verifique los valores que configuró en los pasos anteriores y haga clic en **Create server**.
9 En la siguiente pantalla corrobore que su servidor se está iniciando (**State = Starting**).

![Starting](/static/images/tr/starting.png)

10. Guarde el **Server ID** en un archivo de texto ya que lo utilizará más adelante.
11. Haga clic en el valor de **Server ID**.
12. Copie el valor de **Endpoint** y guárdelo en un archivo de texto ya que lo utilizará más tarde para conectarse a su servidor SFTP.

![Endpoint](/static/images/tr/endpoint.png)

12. Proceda al siguiente módulo.