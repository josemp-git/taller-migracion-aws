---
draft: false
pre: <b style="color:#fff;">2. </b>
title: Creación de usuario IAM
weight: 20
---
CloudEndure requiere de acceso a la consola de AWS donde va a desplegar el servidor que se va a migrar, por lo tanto, en la consola de AWS debe crear un usuario de IAM con los permisos necesarios para poder interactuar con CloudEndure.

#### 1. Creación de política.

1. Haga clic en Services y posteriormente seleccione el servicio de **IAM** que se encuentra bajo la categoría de **Security, Identity & Compliance** (también puede teclear IAM en el campo de búsqueda).
2. Haga clic en **Policies** en el menú del lado izquierdo.
3. Haga clic en **Create policy**.
4. En la pantalla **Create policy** haga clic en la pestaña de **JSON**, borre el contenido existente en el campo y pegue siguiente política:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "VisualEditor0",
      "Effect": "Allow",
      "Action": "ec2\:CreateTags",
      "Resource": "arn\:aws\:ec2:*:*:*/*",
      "Condition": {
        "StringEquals": {
          "ec2\:CreateAction": "RunInstances"
        }
      }
    },
    {
      "Sid": "VisualEditor1",
      "Effect": "Allow",
      "Action": "ec2\:CreateTags",
      "Resource": "arn\:aws\:ec2:*:*:*/*",
      "Condition": {
        "StringEquals": {
          "ec2\:CreateAction": "CreateVolume"
        }
      }
    },
    {
      "Sid": "VisualEditor2",
      "Effect": "Allow",
      "Action": [
        "ec2\:RevokeSecurityGroupIngress",
        "ec2\:DetachVolume",
        "ec2\:AttachVolume",
        "ec2\:DeleteVolume",
        "ec2\:TerminateInstances",
        "ec2\:StartInstances",
        "ec2\:RevokeSecurityGroupEgress",
        "ec2\:StopInstances"
      ],
      "Resource": [
        "arn\:aws\:ec2:*:*\:dhcp-options/*",
        "arn\:aws\:ec2:*:*\:instance/*",
        "arn\:aws\:ec2:*:*\:volume/*",
        "arn\:aws\:ec2:*:*\:security-group/*"
      ],
      "Condition": {
        "StringLike": {
          "ec2\:ResourceTag/Name": "CloudEndure*"
        }
      }
    },
    {
      "Sid": "VisualEditor3",
      "Effect": "Allow",
      "Action": [
        "ec2\:RevokeSecurityGroupIngress",
        "ec2\:DetachVolume",
        "ec2\:AttachVolume",
        "ec2\:DeleteVolume",
        "ec2\:TerminateInstances",
        "ec2\:StartInstances",
        "ec2\:RevokeSecurityGroupEgress",
        "ec2\:StopInstances"
      ],
      "Resource": [
        "arn\:aws\:ec2:*:*\:dhcp-options/*",
        "arn\:aws\:ec2:*:*\:instance/*",
        "arn\:aws\:ec2:*:*\:volume/*",
        "arn\:aws\:ec2:*:*\:security-group/*"
      ],
      "Condition": {
        "StringLike": {
          "ec2\:ResourceTag/CloudEndure creation time": "*"
        }
      }
    },
    {
      "Sid": "VisualEditor4",
      "Effect": "Allow",
      "Action": [
        "ec2\:DisassociateAddress",
        "ec2\:CreateDhcpOptions",
        "ec2\:AuthorizeSecurityGroupIngress",
        "ec2\:DeregisterImage",
        "ec2\:DeleteSubnet",
        "ec2\:DeleteSnapshot",
        "ec2\:ModifySnapshotAttribute",
        "ec2\:ModifyVolumeAttribute",
        "ec2\:CreateVpc",
        "ec2\:AttachInternetGateway",
        "ec2\:GetConsoleScreenshot",
        "ec2\:GetConsoleOutput",
        "elasticloadbalancing\:DescribeLoadBalancer*",
        "ec2\:CreateRoute",
        "ec2\:CreateInternetGateway",
        "ec2\:CreateSecurityGroup",
        "ec2\:CreateSnapshot",
        "ec2\:ModifyVpcAttribute",
        "ec2\:ModifyInstanceAttribute",
        "ec2\:ReleaseAddress",
        "ec2\:AuthorizeSecurityGroupEgress",
        "ec2\:AssociateDhcpOptions",
        "ec2\:ImportKeyPair",
        "ec2\:CreateTags",
        "ec2\:RegisterImage",
        "ec2\:ModifyNetworkInterfaceAttribute",
        "ec2\:AssociateRouteTable",
        "ec2\:CreateRouteTable",
        "ec2\:DetachInternetGateway",
        "iam\:ListInstanceProfiles",
        "ec2\:AllocateAddress",
        "ec2\:ReplaceNetworkAclAssociation",
        "ec2\:CreateVolume",
        "kms\:ListKeys",
        "ec2\:Describe*",
        "ec2\:DeleteVpc",
        "iam\:GetUser",
        "ec2\:CreateSubnet",
        "ec2\:AssociateAddress",
        "ec2\:DeleteKeyPair",
        "ec2\:CreateNetworkAclEntry",
        "outposts\:GetOutpostInstanceTypes"
      ],
      "Resource": "*"
    },
    {
      "Sid": "MigrationHubConfig",
      "Effect": "Allow",
      "Action": [
        "mgh\:GetHomeRegion"
      ],
      "Resource": "*"
    },
    {
      "Sid": "VisualEditor5",
      "Effect": "Allow",
      "Action": [
        "ec2\:RevokeSecurityGroupIngress",
        "mgh\:CreateProgressUpdateStream",
        "kms\:Decrypt",
        "kms\:Encrypt",
        "ec2\:RevokeSecurityGroupEgress",
        "ec2\:DeleteDhcpOptions",
        "ec2\:RunInstances",
        "kms\:DescribeKey",
        "kms\:CreateGrant",
        "ec2\:DeleteNetworkAclEntry",
        "kms\:ReEncrypt*",
        "kms\:GenerateDataKey*"
      ],
      "Resource": [
        "arn\:aws\:mgh:*:*\:progressUpdateStream/*",
        "arn\:aws\:ec2:*:*\:subnet/*",
        "arn\:aws\:ec2:*:*\:key-pair/*",
        "arn\:aws\:ec2:*:*\:dhcp-options/*",
        "arn\:aws\:ec2:*:*\:instance/*",
        "arn\:aws\:ec2:*:*\:volume/*",
        "arn\:aws\:ec2:*:*\:security-group/*",
        "arn\:aws\:ec2:*:*\:network-acl/*",
        "arn\:aws\:ec2:*:*\:placement-group/*",
        "arn\:aws\:ec2:*:*\:vpc/*",
        "arn\:aws\:ec2:*:*\:network-interface/*",
        "arn\:aws\:ec2:*::image/*",
        "arn\:aws\:ec2:*:*\:snapshot/*",
        "arn\:aws\:kms:*:*\:key/*"
      ]
    },
    {
      "Sid": "VisualEditor6",
      "Effect": "Allow",
      "Action": [
        "ec2\:CreateTags",
        "mgh\:ImportMigrationTask",
        "mgh\:AssociateCreatedArtifact",
        "mgh\:NotifyMigrationTaskState",
        "mgh\:DisassociateCreatedArtifact",
        "mgh\:PutResourceAttributes"
      ],
      "Resource": [
        "arn\:aws\:mgh:*:*\:progressUpdateStream/*/migrationTask/*",
        "arn\:aws\:ec2:*:*\:subnet/*",
        "arn\:aws\:ec2:*::network-interface/*",
        "arn\:aws\:ec2:*:*\:dhcp-options/*",
        "arn\:aws\:ec2:*::snapshot/*",
        "arn\:aws\:ec2:*:*\:security-group/*",
        "arn\:aws\:ec2:*::image/*"
      ]
    },
    {
      "Sid": "VisualEditor7",
      "Effect": "Allow",
      "Action": "ec2\:Delete*",
      "Resource": [
        "arn\:aws\:ec2:*:*\:route-table/*",
        "arn\:aws\:ec2:*:*\:dhcp-options/*",
        "arn\:aws\:ec2:*:*\:instance/*",
        "arn\:aws\:ec2:*:*\:volume/*",
        "arn\:aws\:ec2:*:*\:security-group/*",
        "arn\:aws\:ec2:*:*\:internet-gateway/*"
      ],
      "Condition": {
        "StringLike": {
          "ec2\:ResourceTag/Name": "CloudEndure*"
        }
      }
    },
    {
      "Sid": "VisualEditor8",
      "Effect": "Allow",
      "Action": "ec2\:Delete*",
      "Resource": [
        "arn\:aws\:ec2:*:*\:route-table/*",
        "arn\:aws\:ec2:*:*\:dhcp-options/*",
        "arn\:aws\:ec2:*:*\:instance/*",
        "arn\:aws\:ec2:*:*\:volume/*",
        "arn\:aws\:ec2:*:*\:security-group/*",
        "arn\:aws\:ec2:*:*\:internet-gateway/*"
      ],
      "Condition": {
        "StringLike": {
          "ec2\:ResourceTag/CloudEndure creation time": "*"
        }
      }
    },
     {
            "Sid": "VisualEditor9",
            "Effect": "Allow",
            "Action": "ec2\:ModifyVolume",
            "Resource": "arn\:aws\:ec2:*:*\:volume/*",
            "Condition": {
                "StringLike": {
                    "ec2\:ResourceTag/Name": "CloudEndure*"
                }
            }
        },
        {
            "Sid": "VisualEditor10",
            "Effect": "Allow",
            "Action": "cloudwatch\:GetMetricData",
            "Resource": "*"
        }
  ]
}
```

::alert[Esta política también puede encontrarse en esta liga: https://docs.cloudendure.com/Content/IAMPolicy.json]{type="info"}

5. Haga clic en **Next: Tags**.
6. Haga clic en **Next: Review**.
7. Ingrese un nombre para la política **(CloudEndurePolicy)** en el campo de **Name**.
8. Haga clic en **Create policy**.

#### 2. Creación de usuario IAM.

A continuación, debe crear un usuario al cual anexará la política que acaba de crear. Al crear este usuario, generará las credenciales con las que la consola de CloudEndure podrá interactuar con la consola de AWS y así poder llevar a cabo el proceso de migración. 

9. Haga clic en **Services** y posteriormente seleccione el servicio de **IAM** que se encuentra bajo la categoría de **Security, Identity & Compliance** (también puede teclear IAM en el campo de búsqueda).
10. Dentro de **IAM**, haga clic en **Users** en el menú lateral izquierdo y posteriormente haga clic en el botón de **Add user**.
11. En el campo de **User name** escriba el nombre del usuario que va a crear **(cloudendure)** y en **Access type** seleccione **Programmatic access**. 
12. Haga clic en **Next: Permissions**.
13. En la pantalla **Set permissions** seleccione la opción de **Attach existing policies directly** y en el campo de búsqueda ingrese el nombre de la política que creó anteriormente **(CloudEndurePolicy)**. 
14. Seleccione la política y haga clic en **Next: Tags**.
15. En la siguiente pantalla haga clic en **Next: Review**.
16. Haga clic en **Create user**.
17. Si todo salió bien, debe ver un mensaje de Success en la siguiente pantalla. Haga clic en **Download .csv** para descargar las credenciales del usuario que acaba de crear. Guarde este archivo ya que lo necesitará más adelante.
18. Proceda al siguiente módulo.