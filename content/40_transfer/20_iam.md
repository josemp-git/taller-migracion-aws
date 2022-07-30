---
draft: false
title: 2. Creación de rol IAM
weight: 20
---
A continuación creará una política de IAM que se aplicará a un rol de IAM y permitirá al servicio de AWS Transfer Family interactuar con el bucket de Amazon S3 que creó en el módulo anterior.

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
                "s3:ListBucket",
                "s3:GetBucketLocation"
            ],
            "Effect": "Allow",
            "Resource": [
                "arn:aws:s3:::bucket_name"
            ]
        },
        {
            "Sid": "HomeDirObjectAccess",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:GetObject",
                "s3:DeleteObject",
                "s3:DeleteObjectVersion", 
                "s3:GetObjectVersion",
                "s3:GetObjectACL",
                "s3:PutObjectACL"
            ],
            "Resource": "arn:aws:s3:::bucket_name/*"
        }
    ]
}
```

5. Haga clic el botón de **Next: Tags**.
6. Haga clic en **Next: Review**.
7. Ingrese un **AWSTransferCustomPolicy** en el campo de **Name**.
8. Haga clic en **Create policy**.

#### Creación de rol IAM

9. Diríjase de nuevo al servicio de **IAM**
10. Haga clic en **Roles** en el menú lateral izquierdo.
11. Haga clic en **Create role**.
12. Bajo el apartado de **Select type of trusted entity** seleccione el recuadro de **AWS service**.
13. En el menú desplegable de **Use cases for other AWS services** seleccione **Transfer**.

![Create role](/static/images/tr/crearrol.png)

13. Haga clic en **Next**.
14. En el campo de **Permission policies** ingrese el nombre de la política que creó anteriormente (**AWSTransferCustomPolicy**) y seleccione dicha política.

![Select policy](/static/images/tr/selectpolicy.png.png)

15. haga clic en **Next**.
16. Ingrese **AWSTransferCustomRole** en el campo de **Role name**.
18. Haga clic en **Create role**.
29. Proceda al siguiente módulo.