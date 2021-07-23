---
draft: false
pre: <b style="color:#fff;">2. </b>
title: Creación de políticas y rol IAM
weight: 20
---
A continuación creará dos políticas de IAM. La primera política se aplicará a un rol de IAM y permitirá al servicio de AWS Transfer Family interactuar con el bucket de Amazon S3 que creó en el primer módulo. La segunda política permitirá que los usuarios que cree más adelante únicamente puedan acceder al directorio que lleva su nombre dentro del bucket de Amazon S3.

#### Creación de políticas de IAM

1. Haga clic en **Services** y posteriormente seleccione el servicio de **IAM**.
2. Haga clic en **Policies** en el menú del lado izquierdo.
3. Haga clic en **Create policy**.
4. En la siguiente pantalla haga clic en la pestaña de **JSON**, borre el contenido existente en el campo y pegue la siguiente política sustituyendo las dos entradas de **bucket_name** por el nombre del bucket que creó en el módulo anterior:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowListingOfUserFolder",
            "Action": [
                "s3\:ListBucket",
                "s3\:GetBucketLocation"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn\:aws\:s3:::bucket_name"
            ]
        },
        {
            "Sid": "HomeDirObjectAccess",
            "Effect": "Allow",
            "Action": [
                "s3\:PutObject",
                "s3\:GetObject",
                "s3\:DeleteObjectVersion",
                "s3\:DeleteObject",
                "s3\:GetObjectVersion"
            ],
            "Resource": "arn\:aws\:s3:::bucket_name/*"
        }
    ]
}
```

5.    Haga clic el botón de **Review policy**.
6.    Ingrese un **AWSTransferCustomPolicy** en el campo de **Name**.
7.    Haga clic en **Create policy**.
8.    Haga clic de nuevo en **Policies** en el menú del lado izquierdo.
9.    Haga clic en **Create policy**.
10.    En la siguiente pantalla haga clic en la pestaña de **JSON**, borre el contenido existente en el campo y pegue la siguiente política:

```json
{
  "Version": "2012-10-17",
  "Statement": [
      {
          "Sid": "AllowListingOfUserFolder",
          "Action": [
              "s3\:ListBucket"
          ],
          "Effect": "Allow",
          "Resource": [
              "arn\:aws\:s3:::${transfer\:HomeBucket}"
          ],
          "Condition": {
              "StringLike": {
                  "s3\:prefix": [
                      "${transfer\:HomeFolder}/*",
                      "${transfer\:HomeFolder}"
                  ]
              }
          }
      },
      {
          "Sid": "HomeDirObjectAccess",
          "Effect": "Allow",
          "Action": [
              "s3\:PutObject",
              "s3\:GetObject",
              "s3\:DeleteObjectVersion",
              "s3\:DeleteObject",
              "s3\:GetObjectVersion",
              "s3\:GetObjectACL",
              "s3\:PutObjectACL"
          ],
          "Resource": "arn\:aws\:s3:::${transfer\:HomeDirectory}*"
       }
  ]
}
```

11.    Haga clic el botón de **Review policy**.
12.    Ingrese **AWSTransferScopeDownPolicy** en el campo de **Name**.
13.    Haga clic en **Create policy**.

#### Creación de rol IAM

14.    Diríjase de nuevo al servicio de **IAM**
15.    Haga clic en **Roles** en el menú lateral izquierdo.
16.    Haga clic en **Create role**.
17.    En **Select type of trusted entity** seleccione el recuadro de **AWS service**.
18.    En **Choose the service that will use this role** seleccione **Transfer**.

![Create S3 bucket](/static/images/tr/crearrol.png)

19.    Haga clic en **Next: Permissions**.
20.    En el campo de **Filter policies** ingrese el nombre de la primera política (**AWSTransferCustomPolicy**).
21.    Seleccione la política (**AWSTransferCustomPolicy**) y haga clic en **Next: Tags**.2
22.    Haga clic en **Next: Review**.
23.    Ingrese **AWSTransferCustomRole** en el campo de **Role name**.
24.    Haga clic en **Create role**.
25.    Proceda al siguiente módulo.