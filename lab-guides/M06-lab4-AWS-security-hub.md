Enabling Security Hub
PDF
RSS
There are two ways to enable AWS Security Hub, by integrating with AWS Organizations or manually.

We strongly recommend integrating with Organizations for multi-account and multi-Region environments. If you have a standalone account, it's necessary to set up Security Hub manually.

Verifying necessary permissions

After you sign up for Amazon Web Services (AWS), you must enable Security Hub to use its capabilities and features. To enable Security Hub, you first have to set up permissions that allow you to access the Security Hub console and API operations. You or your AWS administrator can do this by using AWS Identity and Access Management (IAM) to attach the AWS managed policy called AWSSecurityHubFullAccess to your IAM identity.

To enable and manage Security Hub through the Organizations integration, you also should attach the AWS managed policy called AWSSecurityHubOrganizationsAccess.

For more information, see AWS managed policies for AWS Security Hub.

Enabling Security Hub with Organizations integration

To start using Security Hub with AWS Organizations, the AWS Organizations management account for the organization designates an account as the Security Hub delegated administrator account for the organization. Security Hub is automatically enabled in the delegated administrator account in the current Region.

Choose your preferred method, and follow the steps to designate the delegated administrator.



Security Hub console

Security Hub API

AWS CLI

To designate the Security Hub delegated administrator when onboarding
Open the AWS Security Hub console at https://console.aws.amazon.com/securityhub/.

Choose Go to Security Hub. You're prompted to sign in to the Organizations management account.

On the Designate delegated administrator page, in the Delegated administrator account section, specify the delegated administrator account. We recommend choosing the same delegated administrator that you have set for other AWS security and compliance services.

Choose Set delegated administrator.

For more information about the integration with Organizations, see Integrating Security Hub with AWS Organizations.

After designating the delegated administrator, we recommend that you continue setting up Security Hub with central configuration. The console prompts you to do so. By using central configuration, you can simplify the process of enabling and configuring Security Hub for your organization and ensure that your organization has adequate security coverage.

Central configuration lets the delegated administrator customize Security Hub across multiple organization accounts and Regions rather than configuring Region-by-Region. You can create a configuration policy for your entire organization, or create different configuration policies for different accounts and OUs. The policies specify whether Security Hub is enabled or disabled in associated accounts and which security standards and controls are enabled.

The delegated administrator can designate accounts as centrally managed or self-managed. Centrally managed accounts are configurable only by the delegated administrator. Self-managed accounts can specify their own settings.

If you don't use central configuration, the delegated administrator has a more limited ability to configure Security Hub. For more information, see Managing accounts with AWS Organizations.

Enabling Security Hub manually

You must enable Security Hub manually if you have a standalone account, or if you don't integrate with AWS Organizations. Standalone accounts can't integrate with AWS Organizations and must use manual enablement.

When you enable Security Hub manually, you designate a Security Hub administrator account and invite other accounts to become member accounts. The administrator-member relationship is established when a prospective member account accepts the invitation.

Choose your preferred method, and follow the steps to enable Security Hub. When you enable Security Hub from the console, you also have the option to enable the supported security standards.



Security Hub console

Security Hub API

AWS CLI

Open the AWS Security Hub console at https://console.aws.amazon.com/securityhub/.

When you open the Security Hub console for the first time, choose Go to Security Hub.

On the welcome page, the Security standards section lists the security standards that Security Hub supports.

Select the check box for a standard to enable it, and clear the check box to disable it.

You can enable or disable a standard or its individual controls at any time. For information about managing security standards and controls, see Security controls and standards in AWS Security Hub.

Choose Enable Security Hub.

Multi-account enablement script
Note
Instead of this script, we recommend using central configuration to enable and configure Security Hub across multiple accounts and Regions.

The Security Hub multi-account enablement script in GitHub allows you to enable Security Hub across accounts and Regions. The script also automates the process of sending invitations to member accounts and enabling AWS Config.

The script automatically enables resource recording for all resources, including global resources, in all Regions. It does not limit recording of global resources to a single Region.

There is a corresponding script to disable Security Hub across accounts and Regions.

Next steps after enabling Security Hub

After you enable Security Hub, we recommend enabling the security standards and security controls that are important for your security needs. After you enable controls, Security Hub begins running security checks and generating control findings. You can also leverage integrations between Security Hub and other AWS services and third-party solutions to see their findings in Security Hub.


