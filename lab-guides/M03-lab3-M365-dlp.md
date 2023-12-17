Create and Deploy data loss prevention policies
Article
12/13/2023
3 contributors
In this article
Before you begin
Policy creation scenarios
Deployment
There are many configuration options in a Microsoft Purview Data Loss Prevention (DLP) policy. Each option changes the policy's behavior. This article presents some common intent scenarios for policies that you map to configuration options. Then it walks you through configuring those options. Once you familiarize yourself with these scenarios, you're comfortable using the DLP policy creation UX to create your own policies.

How you deploy a policy is as important policy design. You have multiple options to control policy deployment. This article shows you how to use these options so that the policy achieves your intent while avoiding costly business disruptions.

 Tip

If you're not an E5 customer, use the 90-day Microsoft Purview solutions trial to explore how additional Purview capabilities can help your organization manage data security and compliance needs. Start now at the Microsoft Purview compliance portal trials hub. Learn details about signing up and trial terms.

Before you begin
If you're new to Microsoft Purview DLP, here's a list of the core articles you should be familiar with as you implement DLP:

Administrative units
Learn about Microsoft Purview Data Loss Prevention - The article introduces you to the data loss prevention discipline and Microsoft's implementation of DLP.
Plan for data loss prevention (DLP) - By working through this article you will:
Identify stakeholders
Describe the categories of sensitive information to protect
Set goals and strategy
Data Loss Prevention policy reference - This article introduces all the components of a DLP policy and how each one influences the behavior of a policy.
Design a DLP policy - This article walks you through creating a policy intent statement and mapping it to a specific policy configuration.
Create and Deploy data loss prevention policies - This article, which you're reading now, presents some common policy intent scenarios that you map to configuration options. It then walks you through configuring those options, and gives guidance on deploying a policy.
Learn about investigating data loss prevention alerts - This article introduces you to the lifecycle of alerts from creation, through final remediation and policy tuning. It also introduces you to the tools you use to investigate alerts.
SKU/subscriptions licensing
Before you get started with DLP policies, you should confirm your Microsoft 365 subscription and any add-ons.

For full licensing details, see: Microsoft 365 licensing guidance for security & compliance

Permissions
The account you use to create and deploy policies must be a member of one of these role groups

Compliance administrator
Compliance data administrator
Information Protection
Information Protection Admin
Security administrator
 Important

Be sure you understand the difference between an unrestricted administrator and an administrative unit restricted administrator Administrative units before you start.

Granular Roles and Role Groups
There are roles and role groups that you can use to fine tune your access controls.

Here's a list of applicable roles. To learn more, see Permissions in the Microsoft Purview compliance portal.

DLP Compliance Management
Information Protection Admin
Information Protection Analyst
Information Protection Investigator
Information Protection Reader
Here's a list of applicable role groups. To learn more, see To learn more about them, see Permissions in the Microsoft Purview compliance portal.

Information Protection
Information Protection Admins
Information Protection Analysts
Information Protection Investigators
Information Protection Readers
Policy creation scenarios
The previous article Design a DLP policy introduced you to the methodology of creating a policy intent statement and then mapping that intent statement to policy configuration options. This section takes those examples, plus a few more and walks you through the actual policy creation process. You should work through these scenarios in your test environment to familiarize yourself with the policy creation UI.

There are so many configuration options in the policy creation flow that it's not possible to cover every, or even most configurations. So this article covers several of the most common DLP policy scenarios. Going through these gives you hands on experience across a broad range of configurations.

Scenario 1 Block emails with credit card numbers
 Important

This is a hypothetical scenario with hypothetical values. It's only for illustrative purposes. You should substitute your own sensitive information types, sensitivity labels, distribution groups and users.

Scenario 1 prerequisites and assumptions
This scenario uses the Highly confidential sensitivity label, so it requires that you have created and published sensitivity labels. To learn more, see:

Learn about sensitivity labels
Get started with sensitivity labels
Create and configure sensitivity labels and their policies
This procedure uses a hypothetical distribution group Finance team at Contoso.com and a hypothetical SMTP recipient adele.vance@fabrikam.com.

This procedure uses alerts, see: Get started with the data loss prevention alerts

Scenario 1 policy intent statement and mapping
We need to block emails to all recipients that contain credit card numbers or that have the ‘highly confidential’ sensitivity label applied except if the email is sent from someone on the finance team to adele.vance@fabrikam.com. We want to notify the compliance admin every time an email is blocked and notify the user who sent the item and no one can be allowed to override the block. Track all occurrences of this high risk event in the log and we want the details of any events captured and made available for investigation

Statement	Configuration question answered and configuration mapping
"We need to block emails to all recipients..."	- Where to monitor: Exchange
- Administrative scope: Full directory
- Action: Restrict access or encrypt the content in Microsoft 365 locations > Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files > Block everyone
"...that contain credit card numbers or have the 'highly confidential' sensitivity label applied..."	- What to monitor use the Custom template
- Conditions for a match edit it to add the highly confidential sensitivity label
"...except if..."	- Condition group configuration: Create a nested boolean NOT condition group joined to the first conditions using a boolean AND
"...the email is sent from someone on the finance team..."	- Condition for match: Sender is a member of
"...and..."	- Condition for match: add a second condition to the NOT group
"...to adele.vance@fabrikam.com..."	- Condition for match: Sender is
"...Notify..."	- User notifications: enabled
- Policy tips: enabled
"...the compliance admin every time an email is blocked and notify the user who sent the item..."	- Policy tips: enabled
- Notify these people: selected
- The person who sent, shared, or modified the content: selected
- Send the email to these additional people: add the email address of the compliance administrator
"...and no one can be allowed to override the block...	- Allow overrides from M365 Services: not selected
"...Track all occurrences of this high risk event in the log and we want the details of any events captured and made available for investigation."	- Use this severity level in admin alerts and reports: high
- Send an alert to admins when a rule match occurs: selected
- Send alert every time an activity matches the rule: selected
Steps to create policy for scenario 1
 Important

For the purposes of this policy creation procedure, you'll accept the default include/exclude values and leave the policy turned off. You'll be changing these when you deploy the policy.

Sign in to the Microsoft Purview compliance portal.

In the Microsoft Purview compliance portal > left navigation > Solutions > Data loss prevention > Policies > + Create policy.

Select Custom from the Categories list.

Select Custom from the Regulations list.

Give the policy a name.

 Important

Policies cannot be renamed.

Fill in a description. You can use the policy intent statement here.

Select Next.

Select Full directory under Admin units.

Set the Exchange email location status to On. Set all the other location status to Off.

SAccept the default values for Include = All and Exclude = None.

Select Next.

The Create or customize advanced DLP rules option should already be selected.

Select Next.

Select Create rule. Name the rule and provide a description.

Under Conditions select Add condition > Content contains > Add > Sensitive info types > Credit Card Number. Choose Add.

Select Add > Sensitivity labels > Highly confidential. Choose Add.

Select Add group > AND > NOT > Add condition.

Select Sender is a member of > Add or Remove Distribution Groups > Finance Team.

Choose Add condition > AND > Recipient is. Add adele.vance@fabrikam.com and select Add.

Select Add and action > Restrict access or encrypt the content in Microsoft 365 locations > Restrict access or encrypt the content in Microsoft 365 locations > Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams file. > Block everyone.

Set User notifications to On.

Select Email notification > Notify these people: > The person who sent, shared, or modified the content.

Under Send the email to these additional people and add the email address of the compliance administrator.

Make sure that Allow override from M365 services isn't selected.

Set Use this severity level in admin alerts and reports to high.

Under Incident reports set Send an alert to admins when a rule match occurs to On.

Select Send alert every time an activity matches the rule.

Choose Save.

Choose Next > Keep it off > Next > Submit.

Scenario 2 Block sharing of sensitive items via SharePoint and OneDrive in Microsoft 365 with external users
For SharePoint and OneDrive in Microsoft 365, you create a policy to block sharing of sensitive items with external users via SharePoint and OneDrive.

Scenario 2 prerequisites and assumptions
This scenario uses the Confidential sensitivity label, so it requires that you have created and published sensitivity labels. To learn more, see:

Learn about sensitivity labels
Get started with sensitivity labels
Create and configure sensitivity labels and their policies
This procedure uses a hypothetical distribution group Human Resources and a distribution group for the security team at Contoso.com.

This procedure uses alerts, see: Get started with the data loss prevention alerts

Scenario 2 policy intent statement and mapping
We need to block all sharing of SharePoint and OneDrive items to all external recipients that contain social security numbers, credit card data or have the "Confidential" sensitivity label. We do not want this to apply to anyone on the Human Resources team. We also have to meet alerting requirements. We want to notify our security team with an email every time a file is shared and then blocked. In addition, we want the user to be alerted via email and within the interface if possible. Lastly, we don’t want any exceptions to the policy and need to be able to see this activity within the system.

Statement	Configuration question answered and configuration mapping
“We need to block all sharing of SharePoint and OneDrive items to all external recipients...”	- Administrative scope: Full directory
- Where to monitor: SharePoint sites, OneDrive accounts
- Conditions for a match: First Condition > Shared outside my org
- Action: Restrict access or encrypt the content in Microsoft 365 locations > Block users from receiving email or accessing shared SharePoint, OneDrive > Block only people outside your organization
"...that contain social security numbers, credit card data or have the "Confidential" sensitivity label...”	- What to monitor: use the Custom template
- Condition for a match: Create a second condition that is joined to the first condition with a boolean AND
- Conditions for a match: Second condition, first condition group > Content contains Sensitive info types U.S. Social Security Number (SSN), Credit Card Number
- Condition group configuration Create a second Condition group connected to the first by boolean OR
- Condition for a match: Second condition group, second condition > Content contains any of these sensitivity labels Confidential.
“...We don't want this to apply to anyone on the Human Resources team...”	- Where to apply exclude the Human Resources Team OneDrive accounts
"...We want to notify our Security team with an email every time a file is shared and then blocked..."	- Incident reports: Send an alert to admins when a rule match occurs
- Send email alerts to these people (optional): add the Security team
- Send an alert every time an activity matches the rule: selected
- Use email incident reports to notify you when a policy match occurs: On
- Send notifications to these people: add individual admins as desired
- You can also include the following information in the report: Select all options
"...In addition, we want the user to be alerted via email and within the interface if possible...”	- User notifications: On
- Notify uses in Office 365 with a policy tip: selected
“...Lastly, we don’t want any exceptions to the policy and need to be able to see this activity within the system...”	-User overrides: Not selected
When the conditions are configured, the summary looks like this:

Policy conditions for match summary for scenario 2.

Steps to create policy for scenario 2
 Important

For the purposes of this policy creation procedure you'll leave the policy turned off. You change these when you deploy the policy.

Sign in to the Microsoft Purview compliance portal.

In the Microsoft Purview compliance portal > left navigation > Solutions > Data loss prevention > Policies > + Create policy.

Select Custom from the Categories list.

Select Custom policy from the Regulations list.

Select Next.

Give the policy a name.

 Important

Policies cannot be renamed.

Fill in a description. You can use the policy intent statement here.

Select Next.

Leave the Full directory selection under Admin units.

Choose Next.

Set the SharePoint sites and OneDrive accounts location status to On. Set all the other location status to Off.

Edit the OneDrive accounts scope. Select All users and group >Exclude users and groups > + Exclude > Exclude groups and add the Human Resources group.

Select Done.

Select Done.

Select Next.

On the Define policy settings page, the Create or customize advanced DLP rules option should already be selected.

Select Next.

Select Create rule. Name the rule and provide a description.

Under Conditions select + Add condition > Content is shared from Microsoft 365 > with people outside my organization.

Choose Add condition > set the boolean to AND

Select Content contains > Add > Sensitive info types > U.S. Social Security Number (SSN) and Credit Card Number. Choose Add.

Select Create group. Set the boolean operator to OR

Select > Add > Sensitivity labels > and Confidential.

Select Add.

Under Actions, select Add an action > Restrict access or encrypt the content in Microsoft 365 locations > Block only people outside your organization.

Set User notifications to On.

Select Notify users in Office 365 services with a policy tip > Notify the user who sent, shared, or last modified the content.

Under User overrides, make sure that Allow override from M365 services isn't selected.

Under Incident reports Set Use this severity level in admin alerts and reports to low.

Set Send an alert to admins when a rule match occurs to On.

Add the email address of the security team to Send email alerts to these people (optional).

Select Send alert every time an activity matches the rule.

Choose Save.

Choose Next.

On the Policy mode page, choose Leave the policy turned off > Next > Submit.

Choose Done
