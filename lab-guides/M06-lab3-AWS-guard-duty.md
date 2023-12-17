Getting started with GuardDuty
PDF
RSS
This tutorial provides a hands-on introduction to GuardDuty. The minimum requirements for enabling GuardDuty as a standalone account or as a GuardDuty administrator with AWS Organizations are covered in Step 1. Steps 2 through 5 cover using additional features recommended by GuardDuty to get the most out of your findings.

Topics
Before you begin
Step 1: Enable Amazon GuardDuty
Step 2: Generate sample findings and explore basic operations
Step 3: Configure exporting GuardDuty findings to an Amazon S3 bucket
Step 4: Set up GuardDuty finding alerts through SNS
Next steps
Before you begin

GuardDuty is a threat detection service that monitors Foundational data sources such as AWS CloudTrail event logs, AWS CloudTrail management events, Amazon VPC Flow Logs, and DNS logs. GuardDuty also analyzes features associated with its protection types only if you enable them separately. Features include Kubernetes audit logs, RDS login activity, S3 logs, EBS volumes, Runtime monitoring, and Lambda network activity logs. Using these data sources and features (if enabled), GuardDuty generates security findings for your account.

After you enable GuardDuty, it starts monitoring your environment. You can disable GuardDuty for any account in any Region, at any time. This will stop GuardDuty from processing the foundational data sources and any features that were enabled separately.

You do not need to enable any of the Foundational data sources explicitly. Amazon GuardDuty pulls independent streams of data directly from those services. For a new GuardDuty account, all the available protection types that are supported in an AWS Region are enabled and included in the 30-day free trial period by default. You can opt out of any or all of them. If you're an existing GuardDuty customer, you can choose to enable any or all of the protection plans that are available in your AWS Region. For more information, see Features associated with each protection type in GuardDuty.

When enabling GuardDuty, consider the following items:

GuardDuty is a Regional service, meaning any of the configuration procedures you follow on this page must be repeated in each Region that you want to monitor with GuardDuty.

We highly recommend that you enable GuardDuty in all supported AWS Regions. This enables GuardDuty to generate findings about unauthorized or unusual activity even in Regions that you are not actively using. This also enables GuardDuty to monitor AWS CloudTrail events for global AWS services such as IAM. If GuardDuty is not enabled in all supported Regions, its ability to detect activity that involves global services is reduced. For a full list of Regions where GuardDuty is available, see Regions and endpoints.

Any user with administrator privileges in an AWS account can enable GuardDuty, however, following the security best practice of least privilege, it is recommended that you create an IAM role, user, or group to manage GuardDuty specifically. For information about the permissions required to enable GuardDuty see Permissions required to enable GuardDuty.

When you enable GuardDuty for the first time in any AWS Region, by default, it also enables all the available protection types that are supported in that Region, including Malware Protection. GuardDuty creates a service–linked role for your account called AWSServiceRoleForAmazonGuardDuty. This role includes the permissions and the trust policies that allow GuardDuty to consume and analyze events directly from the Foundational data sources to generate security findings. Malware Protection creates another service–linked role for your account called AWSServiceRoleForAmazonGuardDutyMalwareProtection. This role includes the permissions and trust policies that allow Malware Protection perform agentless scans to detect malware in your GuardDuty account. It allows GuardDuty to create an EBS volume snapshot in your account, and share that snapshot with the GuardDuty service account. For more information, see Service-linked role permissions for GuardDuty. For more information about service-linked roles, see Using service-linked roles.

When you enable GuardDuty for the first time in any Region your AWS account is automatically enrolled in a 30-day GuardDuty free trial for that Region.

Step 1: Enable Amazon GuardDuty

The first step to using GuardDuty is to enable it in your account. Once enabled, GuardDuty will immediately begin to monitor for security threats in the current Region.

If you want to manage GuardDuty findings for other accounts within your organization as a GuardDuty administrator, you must add member accounts and enable GuardDuty for them as well. Choose an option to learn how to enable GuardDuty for your environment.



Standalone account environment

Multi-account environment

Open the GuardDuty console at https://console.aws.amazon.com/guardduty/

Choose Get Started.

Choose Enable GuardDuty.

Step 2: Generate sample findings and explore basic operations

When GuardDuty discovers a security issue, it generates a finding. A GuardDuty finding is a dataset containing details relating to that unique security issue. The finding's details can be used to help you investigate the issue.

GuardDuty supports generating sample findings with placeholder values, which can be used to test GuardDuty functionality and familiarize yourself with findings before needing to respond to a real security issue discovered by GuardDuty. Follow the guide below to generate sample findings for each finding type available in GuardDuty, for additional ways to generate sample findings, including generating a simulated security event within your account, see Sample findings.

To create and explore sample findings

In the navigation pane, choose Settings.

On the Settings page, under Sample findings, choose Generate sample findings.

In the navigation pane, choose Summary to view the insights about the findings generated in your AWS environment. For more information about the components of the Summary dashboard, see Summary dashboard.

In the navigation pane, choose Findings. The sample findings are displayed on the Current findings page with the prefix [SAMPLE].

Select a finding from the list to display details for the finding.

You can review the different information fields available in the finding details pane. Different types of findings can have different fields. For more information about the available fields across all finding types see Finding details. From the details pane you can take the following actions:

Select the finding ID at the top of the pane to open the complete JSON details for the finding. The complete JSON file can also be downloaded from this panel. The JSON contains some additional information not included in the console view and is the format that can be ingested by other tools and services.

View the Resource affected section. In a real finding, the information here will help you identify a resource in your account that should be investigated and will include links to the appropriate AWS Management Console for actionable resources.

Select the + or - looking glass icons to create an inclusive or exclusive filter for that detail. For more information about finding filters see Filtering findings.

Archive all your sample findings

Select all findings by selection the check box at the top of the list.

Deselect any findings that you wish to keep.

Select the Actions menu and then select Archive to hide the sample findings.

Note
To view the archived findings select Current and then Archived to switch the findings view.

Step 3: Configure exporting GuardDuty findings to an Amazon S3 bucket

GuardDuty recommends configuring settings to export findings because it allows you to export your findings to an S3 bucket for indefinite storage beyond the GuardDuty 90-day retention period. This allows you to keep records of findings or track issues within your AWS environment over time. The process outlined here walks you through setting up a new S3 bucket and creating a new KMS key to encrypt findings from within the console. For more information about this, including how to use your own existing bucket or a bucket in another account, see Exporting findings.

To configure S3 export findings option
To encrypt the findings, you'll need a KMS key with a policy that allows GuardDuty to use that key for encryption. The following steps will help you create a new KMS key. If you are using a KMS key from another account, you need to apply the key policy by logging in to the AWS account that owns the key. The Region of your KMS key and S3 bucket must be the same. However, you can use this same bucket and key pair for each Region from where you want to export findings.

Open the AWS KMS console at https://console.aws.amazon.com/kms.

To change the AWS Region, use the Region selector in the upper-right corner of the page.

In the navigation pane, choose Customer managed keys.

Choose Create key.

Choose Symmetric under Key type, and then choose Next.

Note
For detailed steps about creating your KMS key, see Creating keys in the AWS Key Management Service Developer Guide.

Provide an Alias for your key, and then choose Next.

Choose Next, and then again choose Next to accept the default administration and usage permissions.

After you Review the configuration, choose Finish to create the key.

On the Customer managed keys page, choose your key alias.

In the Key policy tab, choose Switch to policy view.

Choose Edit and add the following key policy to your KMS key, granting GuardDuty access to your key. This statement allows GuardDuty to use only the key to which you add this policy. When editing the key policy, ensure that the JSON syntax is valid. If you add the statement before the final statement, you must add a comma after the closing bracket.


{    
    "Sid": "AllowGuardDutyKey",
    "Effect": "Allow",
    "Principal": {
        "Service": "guardduty.amazonaws.com"
    },
    "Action": "kms:GenerateDataKey",
    "Resource": "arn:aws:kms:Region1:444455556666:key/KMSKeyId",
    "Condition": {
        "StringEquals": {
            "aws:SourceAccount": "111122223333",
            "aws:SourceArn": "arn:aws:guardduty:Region2:111122223333:detector/SourceDetectorID"	
        }
    }
}
Replace Region1 with the Region of your KMS key. Replace 444455556666 with the AWS account that owns the KMS key. Replace KMSKeyId with the key ID of the KMS key that you chose for encryption. To identify all these values – Region, AWS account, and key ID, view the ARN of your KMS key. To locate the key ARN, see Finding the key ID and ARN.

Similarly, replace 111122223333 with the AWS account of the GuardDuty account. Replace Region2 with the Region of the GuardDuty account. Replace SourceDetectorID with the detector ID of the GuardDuty account for Region2.

You can find your own detectorId for your current Region on the Settings page in the https://console.aws.amazon.com/guardduty/ console.

Choose Save.

Open the GuardDuty console at https://console.aws.amazon.com/guardduty/.

In the navigation pane, choose Settings.

Under Findings export options, choose Configure now.

Choose New bucket. Provide a unique name for your S3 bucket.

(Optional) you can test your new export settings by generating sample findings. In the navigation pane, choose Settings.

Under the Sample findings section, choose Generate sample findings. The new sample findings will appear as entries in the S3 bucket created by GuardDuty in up to five minutes.

Step 4: Set up GuardDuty finding alerts through SNS

GuardDuty integrates with Amazon EventBridge, which can be used to send findings data to other applications and services for processing. With EventBridge you can use GuardDuty findings to initiate automatic responses to your findings by connecting finding events to targets such as AWS Lambda functions, Amazon EC2 Systems Manager automation, Amazon Simple Notification Service (SNS) and more.

In this example you will create an SNS topic to be the target of an EventBridge rule, then you'll use EventBridge to create a rule that captures findings data from GuardDuty. The resulting rule forwards the finding details to an email address. To learn how you can send findings to Slack or Amazon Chime, and also modify the types of findings alerts are sent for, see Setup an Amazon SNS topic and endpoint.

To create an SNS topic for your findings alerts

Open the Amazon SNS console at https://console.aws.amazon.com/sns/v3/home.

In the navigation pane, choose Topics.

Choose Create Topic.

For Type, select Standard.

For Name, enter GuardDuty.

Choose Create Topic. The topic details for your new topic will open.

In the Subscriptions section, choose Create subscription.

For Protocol, choose Email.

For Endpoint, enter the email address to send notifications to.

Choose Create subscription.

After you create your subscription, you must confirm the subscription through email.

To check for a subscription message, go to your email inbox, and in the subscription message, choose Confirm subscription.

Note
To check the email confirmation status, go to the SNS console and choose Subscriptions.

To create an EventBridge rule to capture GuardDuty findings and format them

Open the EventBridge console at https://console.aws.amazon.com/events/.

In the navigation pane, choose Rules.

Choose Create rule.

Enter a name and description for the rule.

A rule can't have the same name as another rule in the same Region and on the same event bus.

For Event bus, choose default.

For Rule type, choose Rule with an event pattern.

Choose Next.

For Event source, choose AWS events.

For Event pattern, choose Event pattern form.

For Event source, choose AWS services.

For AWS service, choose GuardDuty.

For Event Type, choose GuardDuty Finding.

Choose Next.

For Target types, choose AWS service.

For Select a target, choose SNS topic, and for Topic, choose the name of the SNS topic you created earlier.

In the Additional settings section, for Configure target input, choose Input transformer.

Adding an input transformer formats the JSON finding data sent from GuardDuty into a human-readable message.

Choose Configure input transformer.

In the Target input transformer section, for Input path, paste the following code:



{
  "severity": "$.detail.severity",
  "Finding_ID": "$.detail.id",
  "Finding_Type": "$.detail.type",
  "region": "$.region",
  "Finding_description": "$.detail.description"
}
                            
To format the email, for Template, paste the following code:



"You have a severity <severity> GuardDuty finding type <Finding_Type> in the <region> region."
"Finding Description:"
"<Finding_description>. "
"For more details open the GuardDuty console at https://console.aws.amazon.com/guardduty/home?region=<region>#/findings?search=id%3D<Finding_ID>"
Choose Confirm.

Choose Next.

(Optional) Enter one or more tags for the rule. For more information, see Amazon EventBridge tags in the Amazon EventBridge User Guide.

Choose Next.

Review the details of the rule and choose Create rule.

(Optional) Test your new rule by generating sample findings with the process in Step 2. You will receive an email for each sample finding generated.
