# Microsoft Purview

Microsoft Purview is a family of data governance, risk, and compliance solutions that can help your organization govern, protect, and manage your entire data estate. Microsoft Purview helps you raise your organization's security posture by enabling you to:

-   Gain visibility into data assets across your organization, including on-premises, multi-cloud, and software-as-a-service (SaaS) sources.
-   Identify and classify sensitive data across your data estate, and apply appropriate protection policies to prevent unauthorized access or leakage.
-   Monitor and audit the activity and health of your identity and access management system, and detect and respond to data risks and threats.
-   Comply with regulatory and organizational requirements for data retention and reporting, and leverage data insights to optimize your data strategy.

In this lab, you are a data engineer working for a healthcare organization that provides various services to patients, such as diagnosis, treatment, medication, and surgery. Your organization has a large and complex data estate, consisting of multiple data sources, such as electronic health records, medical images, lab results, billing systems, and external data providers. Your organization also needs to comply with various regulations and standards, such as HIPAA, GDPR, and ISO 27001, to ensure the privacy and security of your data.

You have been tasked with implementing a data governance solution using Microsoft Purview to help your organization discover, catalog, and understand all your data across your enterprise. You will also use Purview to manage and govern your data with policies, roles, and access controls.

In this lab you'll configure and prepare your environment for administration tasks. By following the steps provided, you'll ensure that essential features and settings are enabled in advance, allowing for an easier learning experience in upcoming lab activities. This preparation will include activating necessary features, setting up administrative permissions, and ensuring the proper configuration of key elements.

## Task 1 – Create user accounts and passwords for lab exercises

Getting started: In this task, you'll set passwords for the user accounts that will be needed for the other tasks in this lab.

1.  In **Microsoft Edge**, navigate to +++**https://admin.microsoft.com+++** and log into the portal as the M365 Administrator ID provided by your lab hosting provider.
2.  On the left navigation pane, expand **Users** then select **Active users**.
3.  On the **Active users** page, Create a new user account. Give the new user account a unique name.
4.  Once the user is created, select the **Reset password** key and the **Reset password** flyout page should appear on the right to reset the user’s password.
5.  Ensure none of the checkboxes are selected on the **Reset password** flyout page.
6.  In the **Password** field, enter a password for the user account you can remember.
7.  **IMPORTANT: Remember this username and password. Open Notepad and copy and paste it there for reference.**
8.  Select the **Reset password** button to reset the user’s password.
9.  On the **Password has been reset** page, select the **Close** button to go back to the **Active users** page.
10. Repeat steps 4-8 to create two additional user accounts. Also place the information for these accounts into the Notepad document for later reference.

## Task 2 - Enabling Auditing in the Microsoft Purview portal

The importance of enabling audit in the Microsoft Purview portal is that it allows you to record and retain the user and admin activity in your data estate. By enabling audit, you can:

-   Gain visibility into the data assets across your organization, including on-premises, multi-cloud, and software-as-a-service (SaaS) sources.
-   Identify and classify sensitive data across your data estate and apply appropriate protection policies to prevent unauthorized access or leakage.
-   Monitor and audit the activity and health of your identity and access management system and detect and respond to data risks and threats.
-   Comply with regulatory and organizational requirements for data retention and reporting, and leverage data insights to optimize your data strategy.

In this task, you'll enable Audit in the Microsoft Purview compliance portal. This tracking feature ensures visibility and accountability by monitoring portal activities.

1.  In **Microsoft Edge**, navigate to +++**https://compliance.microsoft.com+++**.
2.  In the left navigation pane select **Audit**.
3.  On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.

## Task 3 – Assign Compliance Roles

Assigning Compliance Roles in Microsoft Purview is important because it allows you to control who can perform various compliance tasks and access different features in the Microsoft Purview compliance portal. By assigning Compliance Roles, you can:

-   Ensure that your users have the appropriate and least privilege permissions to do their jobs across compliance solutions, such as device management, data loss prevention, eDiscovery, insider risk management, retention, and more.
-   Manage the permissions for users who perform compliance tasks in Microsoft 365 services, such as Exchange Online, SharePoint Online, OneDrive for Business, Teams, and Yammer.
-   Comply with regulatory and organizational requirements for data security and privacy, such as GDPR, HIPAA, and NIST.
-   Monitor and audit the activity and health of your identity and access management system and detect and respond to data risks and threats.

As the recently hired Compliance Administrator for Contoso Ltd. in the role of Joni Sherman, your responsibility is to configure your organization's new Microsoft 365 tenant to meet its compliance requirements. Contoso Ltd. is a company headquartered in the United States with new subsidiaries in the European Union, and it is essential for your organization to ensure that the new Microsoft 365 tenant complies with legal requirements in different countries and regulatory standards in your industry sector.

In this task, you will follow the principal of least privilege and use the default Global Administrator to assign the Compliance Admin role to your created user account, which is required to perform the operations described in this lab.

1.  Open **Microsoft Edge**, select the address bar, navigate to +++**https://admin.microsoft.com+++** and log into the Microsoft 365 admin center as **M365 Administrator ID** provided by your lab hosting provider.
2.  On the **Stay signed in?** dialog box, select the **Don’t show this again** checkbox and then select **No**.
3.  Close the password save dialog from the bottom by selecting **Never**, to not save the default global admins credentials in your browser.
4.  If a welcome screen is displayed, close it. If the Office 365 apps notification appears, also close it.
5.  If a welcome window is displayed, select Get started and close it.
6.  In the left navigation pane, expand **Users** then select **Active users**.
7.  In the **Active users** list select **Joni Sherman**. This will open a flyout page to the right with Joni's user settings.
8.  In User’s user setting page, select **Reset password**. On the **Reset password** page deselect **Automatically create a password** and **Require this user to change their password when they first sign in**. There should be no options enabled on this page.
9.  In the **Password** field, enter a password for Joni's account that you'll remember then select the **Reset password** button.
10. Once the user’s password has been reset, you'll see a message confirming **Password has been reset**. Select the back arrow on the upper left of this page to go back to Joni's user settings page.
11. On the User’s user settings page, below the **Account** tab, scroll to **Roles** then select **Manage roles**.
12. On the **Manage admin roles** flyout page, select **Admin center access** then scroll down to select **Show all by category**. Under the category view in the **Security & Compliance** category select **Compliance Administrator** .
13. Select **Save changes** to apply the role. When the **Admin roles updated** message is displayed on the upper part of the page, select the arrow pointing to the left to return to Joni's user settings.
14. Close the flyout page displaying the user’s account with the **X** in the upper right to go back to the **Active users** list.
15. Before switching to the user account, use the Global Admin privileges of M365 Administrator for activating the audit logging by navigating to +++https://compliance.microsoft.com/auditlogsearch+++.
16. On the **Audit** page. select **Start recording user and admin activity** to activate audit logging.
17. Select the circle with **MA** in the upper right and select **Sign out**.
18. Close the **Microsoft Edge** browser window.

You have successfully assigned the User account the Compliance Administrator role, which is required to perform the different exercises of this lab. Continue with the next task.

## Task 4 – Explore the Microsoft Purview portal

In this task, you will sign out of the global admin account and sign-in again as the user account. Now that the user is assigned the Compliance admin role, the account will be sufficient for most of this lab's exercises.

1.  In **Microsoft Edge**, navigate to +++**https://compliance.microsoft.com+++**.
2.  When the **Pick an account** window is displayed, select **Use another account**.
3.  When the **Sign in** window is displayed, sign in as the user account you created.
4.  If the **Improve your compliance posture** message window opens, read the text and select **Next** twice and then select **Done**.
5.  The page **Welcome to the Microsoft Purview compliance portal** is displayed. Investigate the dashboard tiles and the left-side navigation pane.
6.  Get yourself familiar with the different settings. When you are done, leave the browser window open.

## Task 5 – Create Sensitivity Labels

Sensitivity labels are tags that you can apply on assets to classify and protect your data. They help you to state how sensitive certain data is in your organization and enforce appropriate policies based on the labels. For example, you can apply a "Confidential" label to a document or email, and that label encrypts the content and applies a "Confidential" watermark¹. Sensitivity labels can also be applied to containers, such as Teams, Microsoft 365 Groups, and SharePoint sites, to control their settings and access. Sensitivity labels can be created and configured in the Microsoft Purview compliance portal, and they can be automatically or manually applied to your data in the Microsoft Purview Data Map. Sensitivity labels are based on open standards and interoperable with other Decentralized Identity solutions.

In this lab you will assume the role of the user account you have created. Your organization is based in Rednitzhembach, Germany and is currently implementing a sensitivity plan to ensure that all employee documents in the HR department have been marked with a sensitivity label as part of your organizations information protection policies.

In this task, your HR department has requested a sensitivity label to apply to HR employee documents. You will create a sensitivity label for Internal documents and a sublabel for the HR department.

1.  In **Microsoft Edge**, navigate to +++**https://compliance.microsoft.com+++** and log into the Microsoft Purview portal as your created user account.
2.  In the Microsoft Purview portal, on the left navigation pane, expand **Information protection** then select **Labels**.
3.  On the **Labels** page select **+ Create a label**.
4.  The **New sensitivity label** wizard will start. On the **Name and create a tooltip for your label** page for the **Name**, **Description for admins** and **Description for users**, enter the following information:
    1.  **Name**: Internal
    2.  **Display name**: Internal
    3.  **Description for users**: Internal sensitivity label.
    4.  **Description for admins**: Internal sensitivity label for Contoso.
5.  Select **Next**.
6.  On the **Define the scope for this label** page, select **Items** and select **Files** and **Emails**. If any other options on this page are selected, deselect those options.
7.  Select **Next**.
8.  On the **Choose protection settings for labeled items** page, select **Next**.
9.  On the **Auto-labeling for files and emails** page, select **Next**.
10. On the **Define protection settings for groups and sites** page, select **Next**.
11. On the **Auto-labeling for schematized data assets (preview)** page, select **Next**.
12. On the **Review your settings and finish** page, select **Create label**.
13. Once the label has been created **Your sensitivity label was created** page will be displayed.
14. Select **Don't create a policy yet** and then select **Done**.
15. On the Information protection page, highlight (without selecting) the newly created **Internal** label and select the vertical **...**
16. Select the **+ Create sublabel** from the drop-down menu.
17. The **New sensitivity label** wizard will start. On the **Name and create a tooltip for your label** page for the **Name**, **Display Name**, **Description for admins** and **Description for users**, enter the following information:
    1.  **Name**: Employee data (HR)
    2.  **Display name**: Employee data (HR)
    3.  **Description for users**: This HR label is the default label for all specified documents in the HR Department.
    4.  **Description for admins**: This label is created in consultation with Ms. Jones (Head of HR department). Contact her when you want to change settings of the label.
18. Select **Next**.
19. On the **Define the scope for this label** page, select the option **Items** and select **Files** and **Emails**.
20. Select **Next**.
21. On the **Choose protection settings for labeled items** page, select the **Apply or remove encryption** option.
22. Select **Next**.
23. On the **Encryption** page select **Configure encryption settings**.
24. Enter the following information into the encryption settings:
    1.  **Assign permissions now or let users decide?**: Assign permissions now
    2.  **User access to content expires**: Never
    3.  **Allow offline access**: Only for a number of days
    4.  **Users have offline access to the content for this many days**: 15
25. Select the **Assign permissions** link,
26. On the Assign permissions side menu, select the **+ Add any authenticated users**.
27. Select **Save**.
28. On the **Encryption** page, select **Next**.
29. On the **Auto-labeling for files and emails** page, select **Next**.
30. On the **Define protection settings for groups and sites** page, select **Next**.
31. On the **Auto-labeling for schematized data assets (preview)** page, select **Next**.
32. On the **Review your settings and finish** page, select **Create label**.
33. The label will be created and when complete a message will display **Your sensitivity label was created**.
34. Select **Don't create a policy yet** and then select **Done**.

You have successfully created a sensitivity label for your organization’s internal policies and a sensitivity sublabel for the Human Resources (HR) department.

## Task 6 – Publish Sensitivity Labels

You will now publish the Internal and HR sensitivity label so that the published sensitivity labels will be available for the HR users to apply to their HR documents.

1.  In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to +++**https://compliance.microsoft.com+++**.
2.  In the Microsoft Purview portal, on the left navigation pane, expand **Information protection** then select **Labels**.
3.  On the Labels page select **Publish label**.
4.  The publish sensitivity labels wizard will start.
5.  On the **Choose sensitivity labels to publish** page, select the **Choose sensitivity labels to publish** link.
6.  The **Sensitivity labels to publish** pane will appear on the right.
7.  Select the **Internal** and **Internal/Employee Data (HR)** checkboxes.
8.  Select **Add**.
9.  On the **Choose sensitivity labels to publish** page, select **Next**.
10. On the **Assign admin units (preview)** page, select **Next**
11. On the **Publish to users and groups** page, select **Next**.
12. On the **Policy settings** page, select **Next**.
13. On the **Default settings for documents** select **Next**.
14. On the **Default settings for emails** select **Next**.
15. On the **Default settings for meetings and calendar events** select **Next**.
16. On the **Default settings for Power BI Content** select **Next**.
17. On the **Name your policy** page, enter the following information:
    1.  **Name**: Internal HR employee data
    2.  **Enter a description for your sensitivity label policy**: This HR label is to be applied to internal HR employee data.
18. Select **Next**.
19. On the **Review and finish** page, select **Submit**.
20. On the **New policy created**, select **Done** to finish publishing your label policy.

You have successfully published the Internal and HR sensitivity labels. Note that it can take up to 24 hours for changes to replicate to all users and services.

## Task 7 – Configure Auto Labeling

Auto labeling is important in Microsoft Purview because it helps you to classify and protect your data assets automatically, without relying on manual intervention or user training. Auto labeling can help you to:

-   Apply consistent and accurate sensitivity labels to your data based on the content and context of the data.
-   Enforce data protection policies and actions based on the sensitivity labels, such as encryption, access control, retention, and deletion.
-   Track and audit the usage and activity of your sensitive data across different sources and locations.
-   Comply with data privacy and security regulations and standards, such as GDPR, HIPAA, PCI DSS, etc.

You can use auto labeling in Microsoft Purview to label files and database columns in the data map, as well as files and emails in SharePoint, OneDrive, and Exchange. You can create auto labeling rules for each sensitivity label, defining which classification or sensitive information type constitutes a label.

In this task, you will create a Sensitivity Label that will auto label documents and emails found to contain information related to the European General Data Protection Regulation (GPDR).

1.  In **Microsoft Edge**, navigate to +++**https://compliance.microsoft.com+++** and log into the Microsoft Purview portal as **you created user account**.
2.  In the Microsoft Purview portal, on the left navigation pane, expand **Information protection** and then select **Labels**.
3.  On the Labels page, highlight (without selecting) the existing **Internal** label, and select the three dots.
4.  Select the **+ Create sublabel** menu item.
5.  The **New sensitivity label** wizard will start. On the **Name and create a tooltip for your label** page, enter the following information:
    1.  **Name**: GDPR Germany
    2.  **Display name**: GDPR Germany
    3.  **Description for users**: This document or email contains data related to the European General Data Protection Regulation (GPDR) for the region Germany.
    4.  **Description for admins**: This label is auto applied to German GDPR documents.
6.  Select **Next**.
7.  On the **Define the scope for this label** page, select the option **Items** and select **Files** and **Emails**.
8.  Select **Next**.
9.  On the **Choose protection settings for labeled items** page, select **Next**.
10. On the **Auto-labeling for files and emails** page, set the **Auto-labeling for files and emails** to enabled.
11. In the **Detect content that matches these conditions** section, select **+Add condition** then select **Content contains**.
12. In **Content contains** section select the **Add** text then select **Sensitive info types**.
13. A **Sensitive info types** panel will be displayed on the right.
14. In the **Search for sensitive info types** search panel, enter the following information:
15. German
16. Press the enter button, the results will display sensitivity info types related to Germany.
17. Press the **Select all** check box.
18. Select **Add**.
19. Select **Next**.
20. On the **Define protection settings for groups and sites** page, select **Next**.
21. On the **Auto-labeling for schematized data assets (preview)** page, select **Next**.
22. On the **Review your settings and finish** page, select **Create label**.
23. The label will be created and when complete a message will display: **Your sensitivity label was created**.
24. Select **Done**.
25. Once the label has been created the **Your sensitivity label was created** page will be displayed.
26. Select **Don't create a policy yet** and then select **Done**.
27. On the **Labels** page, select **Publish label**.
28. The Publish sensitivity labels wizard will start.
29. On the **Choose sensitivity labels to publish** page, select the **Choose sensitivity labels to publish** link.
30. A side bar called **Sensitivity labels to publish** will appear on the right.
31. Select the **Internal** and **Internal/GDPR Germany** checkbox.
32. Select **Add**.
33. On the **Choose sensitivity labels to publish** page, select **Next**.
34. On the **Assign admin units (preview)** page, select **Next**.
35. On the **Publish to users and groups** page, select **Next**.
36. On the **Policy settings** page, select **Next**.
37. On the **Default settings for documents​** page, select **Next**.
38. On the **Default settings for emails** page, select **Next**.
39. On the **Default settings for meetings and calendar events** page, select **Next**.
40. On the **Default settings for Power BI content** page, select **Next**.
41. On the **Name your policy** page, enter the following information:
    1.  **Name**: GDPR Germany policy
    2.  **Enter a description for your sensitivity label policy**: This auto apply sensitivity labels policy is for the GDPR region of Germany.
42. Select **Next**.
43. On the **Review and finish** page, select **Submit**.
44. The policy will be created and when complete a message will display, **New policy created**.
45. Select **Done**.

You have successfully created and published an auto apply sensitivity label for GDPR documents in the region Germany.

Be aware that it can take up to 24 hours for auto applied sensitivity labels to be applied, this duration will be longer when applied to more than 25,000 documents (that is, the daily limit).

You are **your created user account**, the newly hired Compliance Administrator for Contoso Ltd. tasked to configure the company's Microsoft 365 tenant for data loss prevention. Contoso Ltd. is a company that offers driving instruction in the United States, and you need to make sure that sensitive customer information does not leave the organization.

## Task 8 – Create a DLP policy

A **Data Loss Prevention (DLP) policy** in Microsoft Purview is a set of rules that define how to identify, monitor, and protect sensitive data across different platforms and devices. DLP is a discipline that helps prevent the accidental or intentional sharing of sensitive information that could cause harm to your organization or customers. A DLP policy can help you to:

-   Detect sensitive data based on the content and context of the data, using built-in or custom sensitive information types, classification labels, or trainable classifiers.
-   Apply actions to protect sensitive data, such as blocking access, encrypting, notifying users, generating alerts, or creating reports.
-   Enforce data protection policies consistently across Microsoft 365 services such as Teams, Exchange, SharePoint, and OneDrive accounts, as well as Windows 10 and Windows 11 devices.
-   Comply with data privacy and security regulations and standards, such as GDPR, HIPAA, PCI DSS, etc.

You can create and manage DLP policies in the Microsoft Purview compliance portal, using a user-friendly interface that guides you through the policy creation process. You can also use PowerShell cmdlets or Graph APIs to create and manage DLP policies programmatically.

In this exercise, you will create a Data Loss Prevention policy in the Microsoft Purview portal to protect sensitive data from being shared by users. The DLP Policy that you create will inform your users if they want to share content that contains Credit Card information and allow them to provide a justification for sending this information. The policy will be implemented because you do not want the block action to affect your users yet.

1.  In **Microsoft Edge**, navigate to +++**https://compliance.microsoft.com+++** and log into the Microsoft Purview portal as your user account.
2.  If the **Stay signed in?** dialog box appears, select the **Don’t show this again** checkbox and then select **No**.
3.  In the **Microsoft Purview** portal, in the left navigation pane, expand **Data loss prevention** then select **Policies**.
4.  On the **Policies** page select **+Create policy** to start the wizard for creating a new data loss prevention policy.
5.  On the **Start with a template or create a custom policy** page, scroll down and select **Custom** under **Categories** and **Custom policy** under **Templates**. By default, both options should already be selected, select **Next**.
6.  On the **Name your DLP policy** page enter:
    1.  **Name**: Credit Card DLP Policy
    2.  **Description**: Protect credit card numbers from being shared
7.  Select **Next**.
8.  On the **Assign admin units (preview)** page select **Next**.
9.  On the **Choose locations to apply the policy** page, enable the **Teams chat and channel messages** option only and select **Next**.
10. On the **Define policy settings** page, select **Create or customize advanced DLP rules** and select **Next**.
11. On the **Customize advanced DLP rules** page, select **+ Create rule**.
12. On the **Create rule** flyout page, type *Credit card information* in the **Name** field.
13. Under **Conditions**, select **+ Add Condition** and then select **Content contains** from the dropdown menu.
14. In the new **Content contains** area, select **Add** and select **Sensitive info types** from the dropdown menu.
15. On the **Sensitive info types** page, select **Credit Card Number** and select **Add**.
16. On the **Create rule** page, select **+ Add condition** and select **Content is shared from Microsoft 365** from the dropdown menu.
17. In the new **Content is shared from Microsoft 365** section, select the **only with people inside my organization** option.
18. On the **Create rule** page, select **+ Add an action**. Under **Use actions to protect content when the conditions are met.** expand **Restrict access or encrypt the content in Microsoft 365 locations** and select **Block everyone.**
19. On the **Create rule** page, in the **User notifications** section, select the switch to **On** to enable user notifications.
20. Select the check box to enable **Notify users in Office 365 service with a policy tip**.
21. Under **User overrides** select the checkbox to **Allow overrides from M365 services. Allows users in Exchange, SharePoint, OneDrive and Teams to override policy restrictions.**
22. Check the checkbox to **Require a business justification to override**.
23. In the **Incident reports** section, in the **Use this severity level in admin alerts and reports** dropdown, select **Low**.
24. On the **Create rule** page select **Save** then select **Next**.
25. On the **Policy** page select **Test it out first** and select **Show policy tips while in test mode**.
26. On the **Review your policy and create it** page review your settings then select **Submit**
27. On the **New policy created** page select **Done**.

You have now created a DLP policy that scans Credit Card numbers in Microsoft Teams chats and channels and allows users to provide a business justification to override the policy.

## Task 9 - Modify a DLP policy

In this task, you will Modify the existing DLP policy you created in the previous step to also scan e-mails for Credit Card information and inform users if they want to share this content in an e-mail.

1.  In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. If so, select it and proceed to the next step. If you closed it, then in a new tab, navigate to +++**https://compliance.microsoft.com+++**.
2.  In the **Microsoft Purview** portal, in the left navigation pane, expand **Data loss prevention** then select **Policies**.
3.  On the **Policies** page select the checkbox next to the recently created **Credit Card DLP Policy** and then select **Edit policy** (pencil icon) to open the policy wizard.
4.  On the **Name your DLP policy** page, select **Next**.
5.  On the **Assign admin units (preview)** page select **Next**.
6.  On the **Choose locations to apply the policy** page, enable the **Exchange email** option and then select **Next** until you reach the **Review your policy and create it** page.
7.  Select **Submit** to apply the change you made to the policy.
8.  Once the policy is updated select **Done**.

You have now modified an existing DLP policy and changed the locations it scans for content.

## Task 10 - Enable file monitoring in Microsoft 365 Defender

You want to use file policies in Microsoft 365 Defender to protect files in your OneDrive and SharePoint Online locations. Before you can create a file policy, you need to enable file monitoring so Microsoft 365 Defender can scan files in your organization.

It is important to enable file monitoring in Microsoft Defender because it helps you to:

-   Detect and protect sensitive data across different platforms and devices, using sensitivity labels, sensitive information types, or trainable classifiers.
-   Apply data protection policies and actions based on the sensitivity labels, such as encryption, access control, retention, and deletion.
-   Track and audit the usage and activity of your sensitive data across different sources and locations.
-   Comply with data privacy and security regulations and standards, such as GDPR, HIPAA, PCI DSS, etc.

To do this:

1.  In **Microsoft Edge**, the Microsoft Purview portal tab should still be open. Select the **Profile picture** of your created user account in the top right and select **Sign out**, then close the browser.
2.  Open **Microsoft Edge** and navigate to +++**https://security.microsoft.com+++** and log into the Microsoft 365 Defender portal as **M365 Administrator** ID provided by your lab hosting provider.
3.  On the left navigation pane, scroll down then select **Settings**.
4.  On the **Settings** page select **Cloud Apps**.
5.  In the left pane within the **Cloud apps** window, scroll down to the **Information Protection** section, then select **Files**.
6.  Select the **Enable file monitoring** checkbox then select **Save** if it is not already marked.

You successfully enabled file monitoring in Microsoft 365 Defender and can now scan files for sensitive content using file policies.

## Task 11 - Create a file policy for Microsoft 365 Defender

With File Monitoring now enabled, you want to create a file policy in Microsoft 365 Defender to scan files in OneDrive and SharePoint Online and automatically quarantine files containing credit card information if they are shared.

1.  In **Microsoft Edge**, the Microsoft Defender for Cloud Apps portal tab should still be open. Select the **Profile picture** of the M365 Admin in the top right and select **Sign out** next to the cogwheel, then close the browser.
2.  Open **Microsoft Edge** and navigate to +++**https://security.microsoft.com+++** and log into the Microsoft 365 Defender portal as your created user account.
3.  In the **Microsoft 365 Defender** portal, in the left navigation, scroll down to the **Cloud apps** section, then select **Files**.
4.  On the **Files** page select **+ New policy from search**.
5.  On the **Create file policy** page, leave the **Policy template** selection as **No template**.
6.  Enter this information on the **Create file policy** page
    1.  **Policy name**: Credit Card Information for files
    2.  **Description**: Protect credit card numbers from being shared in files
7.  Keep the **Policy Severity** on **Low** (one lighted icon) and make sure the **Category** is set to **DLP**. For a file policy, this should be the default.
8.  In the **Files matching all of the following** area, expand the dropdown menu **Public (Internet), External, Public** and add **Internal**.
9.  In the **Inspection Method** dropdown menu, select **Data Classification Service**.
10. In the **Choose inspection type...** dropdown menu, select **Sensitive information type...**.
11. On the **Select a sensitive information type** dialog, select **Credit Card Number**, then select **Done** in the upper right corner.
12. Under **Alerts**, check the **Create an alert for each matching file** checkbox and review your options. Keep the settings as the default by selecting **Save as default settings**.
13. In the **Governance actions** section, expand **Microsoft OneDrive for Business** and select **Put in user quarantine**.
14. In the **Governance actions** section, expand **Microsoft SharePoint Online** and select the checkbox for **Put in user quarantine**.
15. Select **Create** at the bottom of the page.

You have now created a file policy that will continuously scan files saved in OneDrive and SharePoint for credit card information and quarantine them if they are shared inside your organization.

In this exercise, you will assume the role of Joni Sherman, a System Administrator for Contoso Ltd. Your organization is based in Texas and wants to implement retention policies to adhere to state laws, which stipulates that records may be deleted after three years without constituting an offense.

In order to adhere to this law your organization has created a retention plan to retain all items in the organization for three years.
