Using an AWS KMS Customer Managed Key (CMK) for encryption
PDF
If you decide to use a Customer Managed Key (CMK), or if your default Amazon EBS encryption key is a CMK, you will need to add additional permissions to the key to allow AWS Application Migration Service (AWS MGN) to use it.

To modify the existing key policy using the AWS Management Console policy view.

Navigate to the AWS Key Management Service (AWS KMS) Console and select the AWS KMS key you plan to use with AWS MGN.

Scroll to Key policy and click Switch to policy view.

Click Edit and add the following JSON statements to the Statement field.



    {
      "Sid": "Allow AWS Services permission to describe a customer managed key for encryption purposes",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::$ACCOUNT_ID:root"
      },
      "Action": [
        "kms:DescribeKey"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "kms:CallerAccount": [
            "$ACCOUNT_ID"
          ]
        },
        "Bool": {
          "aws:ViaAWSService": "true"
        }
      }
    },
    {
      "Sid": "Allow AWS MGN permissions to use a customer managed key for EBS encryption",
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::$ACCOUNT_ID:root"
      },
      "Action": [
        "kms:CreateGrant"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "kms:CallerAccount": [
            "$ACCOUNT_ID"
          ],
          "kms:GranteePrincipal": [
            "arn:aws:iam::$ACCOUNT_ID:role/aws-service-role/mgn.amazonaws.com/AWSServiceRoleForApplicationMigrationService"
          ]
        },
        "ForAllValues:StringEquals": {
          "kms:GrantOperations": [
            "CreateGrant",
            "DescribeKey",
            "Encrypt",
            "Decrypt",
            "GenerateDataKey",
            "GenerateDataKeyWithoutPlaintext"
          ]
        },
        "Bool": {
          "aws:ViaAWSService": "true"
        }
      }
    },
    {
      "Sid": "Allow EC2 to use this key on behalf of the current AWS Application Migration Service user, during target launches",
      "Effect": "Allow",
      "Principal": {
        "AWS": [
          "arn:aws:iam::$ACCOUNT_ID:root",
          "arn:aws:iam::$ACCOUNT_ID:role/aws-service-role/mgn.amazonaws.com/AWSServiceRoleForApplicationMigrationService"
        ]
      },
      "Action": [
        "kms:ReEncrypt*",
        "kms:GenerateDataKey*"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "kms:CallerAccount": [
            "$ACCOUNT_ID"
          ],
          "kms:ViaService": "ec2.$REGION.amazonaws.com"
        }
      }
    }

                            
Important
Replace $ACCOUNT_ID" with the AWS Account ID you are migrating into.

Replace $REGION with the region you are migrating into.

The last statement can be made stricter by ensuring the principal refers to users who are going to perform StartTest or StartCutover API calls

Click Save changes.

Note
If you are using a Customer Managed Key (CMK) from another account, you need to take an additional step from within that account to allow the service to leverage the CMK.

From the account in which you want to stage MGN replication servers, create a grant that delegates the relevant permissions to the appropriate service-linked role. The Grantee Principal element of the grant is the ARN of the appropriate service-linked role. The key-id is the ARN of the key.

The following is an example create-grant CLI command that gives the service-linked role named AWSServiceRoleForApplicationMigrationService in account 111122223333 permissions to use the customer-managed key in account 444455556666.

aws kms create-grant \

--region us-west-2 \

--key-id arn:aws:kms:us-west-2:444455556666:key/1a2b3c4d-5e6f-1a2b-3c4d-5e6f1a2b3c4d \

--grantee-principal arn:aws:iam::111122223333:role/aws-service-role/mgn.amazonaws.com/AWSServiceRoleForApplicationMigrationService \

--operations "Encrypt" "Decrypt" "ReEncryptFrom" "ReEncryptTo" "GenerateDataKey" "GenerateDataKeyWithoutPlaintext" "DescribeKey" "CreateGrant"

For this command to succeed, the user making the request must have permissions for the CreateGrant action.
