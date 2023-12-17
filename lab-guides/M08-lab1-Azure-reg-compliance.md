Assign security standards
Article
11/27/2023
10 contributors
In this article
Before you start
Assign a standard (Azure)
Assign a standard (AWS)
Assign a standard (GCP)
Next steps
Defender for Cloud's regulatory standards and benchmarks are represented as security standards. Each standard is an initiative defined in Azure Policy.

In Defender for Cloud, you assign security standards to specific scopes such as Azure subscriptions, AWS accounts, and GCP projects that have Defender for Cloud enabled.

Defender for Cloud continually assesses the environment-in-scope against standards. Based on assessments, it shows in-scope resources as being compliant or noncompliant with the standard, and provides remediation recommendations.

This article describes how to add regulatory compliance standards as security standards in an Azure subscriptions, AWS account, or GCP project.

Before you start
To add compliance standards, at least one Defender for Cloud plan must be enabled.
You need Owner or Policy Contributor permissions to add a standard.
Assign a standard (Azure)
To assign regulatory compliance standards on Azure:

Sign in to the Azure portal.

Navigate to Microsoft Defender for Cloud > Regulatory compliance. For each standard, you can see the applied subscription.

Select Manage compliance policies.

Screenshot of the regulatory compliance page that shows you where to select the manage compliance policy button.

Select the subscription or management group on which you want to assign the security standard.

 Note

We recommend selecting the highest scope for which the standard is applicable so that compliance data is aggregated and tracked for all nested resources.

Select Security policies.

Locate the standard you want to enable and toggle the status to On.

Screenshot showing regulatory compliance dashboard options.

If any information is needed in order to enable the standard, the Set parameters page appears for you to type in the information.

The selected standard appears in Regulatory compliance dashboard as enabled for the subscription it was enabled on.

Assign a standard (AWS)
To assign regulatory compliance standards on AWS accounts:

Sign in to the Azure portal.

Navigate to Microsoft Defender for Cloud > Regulatory compliance. For each standard, you can see the applied subscription.

Select Manage compliance policies.

Select the relevant AWS account.

Select Security policies.

In the Standards tab, select the three dots in the standard you want to assign > Assign standard.

Screenshot that shows where to select a standard to assign.

At the prompt, select Yes. The standard is assigned to your AWS account.

Screenshot of the prompt to assign a regulatory compliance standard to the AWS account.

The selected standard appears in Regulatory compliance dashboard as enabled for the account.

Assign a standard (GCP)
To assign regulatory compliance standards on GCP projects:

Sign in to the Azure portal.

Navigate to Microsoft Defender for Cloud > Regulatory compliance. For each standard, you can see the applied subscription.

Select Manage compliance policies.

Select the relevant GCP project.

Select Security policies.

In the Standards tab, select the three dots alongside an unassigned standard and select Assign standard.

Screenshot that shows how to assign a standard to your GCP project.

At the prompt, select Yes. The standard is assigned to your GCP project.

The selected standard appears in the Regulatory compliance dashboard as enabled for the project.
