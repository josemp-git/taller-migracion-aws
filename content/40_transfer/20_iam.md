---
draft: false
title: 2. Creación de rol IAM
weight: 20
---
A continuación creará dos políticas de IAM. La primera política se aplicará a un rol de IAM y permitirá al servicio de AWS Transfer Family interactuar con el bucket de Amazon S3 que creó en el primer módulo. La segunda política permitirá que los usuarios que cree más adelante únicamente puedan acceder al directorio que lleva su nombre dentro del bucket de Amazon S3.

#### Creación de política de IAM

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

5. Haga clic el botón de **Review policy**.
6. Ingrese un **AWSTransferCustomPolicy** en el campo de **Name**.
7. Haga clic en **Create policy**.

#### Creación de rol IAM

8. Diríjase de nuevo al servicio de **IAM**
9. Haga clic en **Roles** en el menú lateral izquierdo.
10. Haga clic en **Create role**.
11. En **Select type of trusted entity** seleccione el recuadro de **AWS service**.
12. En **Choose the service that will use this role** seleccione **Transfer**.

![Create S3 bucket](/static/images/tr/crearrol.png)

13. Haga clic en **Next: Permissions**.
14. En el campo de **Filter policies** ingrese el nombre de la primera política (**AWSTransferCustomPolicy**).
15. Seleccione la política (**AWSTransferCustomPolicy**) y haga clic en **Next: Tags**.2
16. Haga clic en **Next: Review**.
17. Ingrese **AWSTransferCustomRole** en el campo de **Role name**.
18. Haga clic en **Create role**.
29. Proceda al siguiente módulo.