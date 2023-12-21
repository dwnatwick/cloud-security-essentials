# Microsoft Entra ID

**Microsoft Entra ID** is a cloud-based identity and access management service that enables your employees to access external resources, such as Microsoft 365, the Azure portal, and thousands of other SaaS applications.

Microsoft Entra ID helps raise your organization's security posture by providing you with a comprehensive and multicloud identity and access management solution. With Microsoft Entra ID, you can:

-   Protect your users and applications from identity attacks and risks, such as phishing, password spray, and compromised credentials. You can use features such as multifactor authentication, passwordless sign-in, conditional access, identity protection, and privileged identity management to detect and prevent unauthorized access.
-   Manage your data and resources across your hybrid and multicloud environment, including on-premises, Azure, and other cloud platforms. You can use features such as single sign-on, application proxy, entitlement management, and access reviews to grant and monitor the right access to the right resources at the right time.
-   Comply with regulatory and organizational requirements for data security and privacy, such as GDPR, HIPAA, and NIST. You can use features such as terms of use, data classification, audit logs, and reports to ensure that your data is handled in accordance with the applicable policies and standards.

Microsoft Entra ID is based on open standards and interoperable with other Decentralized Identity solutions. It is also integrated with other Microsoft security solutions, such as Microsoft 365 Defender, Defender for Cloud, and Microsoft Sentinel. By using Microsoft Entra ID, you can elevate your security posture and protect your data against risks.

## Task 1 – Create a Microsoft Entra ID Account

You are a security administrator working for a manufacturing company that produces and sells various products, such as electronics, furniture, and clothing. Your company has a hybrid and multicloud environment, consisting of multiple data centers, cloud platforms, and applications. Your company also needs to comply with various regulations and standards, such as ISO 9001, NIST 800-53, and PCI DSS, to ensure the quality and security of your products and data.

You have been tasked with implementing a secure access solution using Microsoft Entra to help your company protect and verify all types of identities and secure, manage, and govern their access to any resource across your enterprise. You will also use Entra to simplify the user experience and reduce IT friction with intelligent real-time access controls.

In this next lab, you'll access Microsoft Entra ID (previously referred to as Azure Active Directory). Additionally, you'll create a user and configure the different settings, including adding licenses.

As a subscriber to Microsoft 365, you're already using Microsoft Entra ID (previously referred to as Azure AD) to login to this lab environment. However, in this task, you’ll learn how to create a new user in Microsoft Entra ID, assign a license, and explore some of services that can be managed at the user level. Even if you’re already comfortable creating user accounts, you’ll create one here to be used for some of the additional lab tasks.

1.  Open the Microsoft Edge browser. In the address bar, enter +++**entra.microsoft.com+++** and sign in with the admin Microsoft 365 credentials provided on the Resources tab.
2.  From the left navigation pane, expand **Identity,** then **Users**, then select **All Users**. Notice that your tenant is already configured with users. The browser page to the right is the overview page of the Microsoft Entra admin center. Here you will see basic information about your Contoso tenant. If you scroll down the main window, you will also see information about alerts, my feed, feature highlights, and more.
3.  From the top of the page, select **+ New user** then from the drop-down box, select **Create new user**.
4.  You are now in the **basics** tab of creating new user page. Populate the fields as follows:
    1.  User principal name: create a user account using *Your first name and some random numbers to make it unique*

        **IMPORTANT: Remember this username. Open Notepad and copy and paste it there for reference.**

    2.  Mail nickname: leave the default, which is set to derive from user principal name.
    3.  Display name: **Your first name and a fake last name**
    4.  Password: uncheck the box that says auto-generate password and enter a temporary password that adheres to the password requirements and make note of it, as you will need it to complete the subsequent task.

        **IMPORTANT: Remember this password. Consider saving it to the same Notepad document you created just earlier for the username.**

    5.  Account enabled: Leave the checkmark to ensure the account is enabled.
    6.  At the bottom of the page, select **Next: Properties**.
5.  Here you will configure a few of the fields in the **Properties** tab.
    1.  First name: as before, *the account first name*
    2.  Last name: as before, *the account last name*
    3.  User types: Leave the default to **Member** but note that from the drop-down you have the option to select guest.

        Leave the rest of the fields as default and scroll down to the last section titled Usage location

    4.  Usage location: Choose the country/region where you are located. Note that to get to the usage location field, you will need to scroll down on the page as it is the last field on the page. **NOTE**: if you don't do this, you will not be able to assign a license in a subsequent step.
    5.  Select **Next: Assignments**.
6.  You are now on the **Assignments** tab where you add a group assignment and view the available options for adding a role.
    1.  Select **Add group**.
    2.  The window that opens shows all the available groups.
    3.  Notice the list of available groups. From the list, select **Contoso**. From the bottom of the page, select the **Select** button. It may take a few seconds, but you should see the operations group show up on the assignments page.
    4.  From the top of the page, select **Add role**. A window opens that shows all the available directory roles. View the available options, but don't add any new roles. Close this page by selecting the **X** on the top right corner of the directory roles page.
    5.  From the bottom of the page, select **Review + create**. A summary of the settings will be displayed. From the bottom of the page, select **Create**.
7.  You are returned to the user’s page. After a few seconds, the new account will be listed. You may need to select the **refresh** icon on the top of the page.
8.  From the user list, select the user you created. The **Overview** page opens.
9.  The left navigation panel shows the various options that can be configured for the user. View the available options.
10. From the left navigation panel, select **Licenses**. Notice that there are no license assignments found for this user. NOTE: Licenses can only be assigned if a usage location is configured. If you did not set the usage location, go back to that step in the previous task.
    1.  To add a license, select **+ Assignments** from the top of the main window.
    2.  Under **Select licenses**, select **Enterprise Mobility + Security E5**, **Office 365 E5** and **Windows 10/11 Enterprise E3** then select the **Save** button on the bottom of the screen. A notification on the top right corner of the screen should show that license assignments succeeded.
    3.  Select the **X** on the top right of the screen to close the License assignments window.
    4.  Select the **Refresh icon** at the top of the page to confirm the license assignments.
11. Return to the Microsoft Entra admin center by selecting **Home** from the left navigation panel or from the top-left of the screen (the breadcrumb - Home \> Users \> *your username*), above where it says your user account \| Licenses.
12. You have successfully created and configured a user in Microsoft Entra ID.
13. Sign out of all the open browser tabs. Sign out by selecting the user icon next to the email address on the top right corner of the screen then selecting **Sign out**. Close all the browser windows.

## Task 2 – Sign in with the new account

In this task, you'll sign in as your user account, for the first time.

1.  Open Microsoft Edge.
2.  In the address bar, enter +++**https://login.microsoft.com+++**.
3.  Sign in with your created user account
4.  Enter the temporary password you set in the previous task.
5.  You are now prompted to Update your password. In the Current password field, enter the temporary password from the previous task.
6.  In the New password field, enter a new password, confirm the password, then select **Sign in**. Make note of your new password (*update the Notepad document you created earlier*) as you will need it for subsequent lab exercises.
7.  You should now be successfully signed-in to Microsoft 365.
8.  Sign out by selecting the icon on the top right corner of the Microsoft 365 window that is shown as a circle with the letters that represent your initials (next to the question mark icon), then selecting **Sign out**, then close the browser.

## Task 3 - Enable passwordless phone sign-in authentication methods

Passwords are a primary attack vector. Bad actors use social engineering, phishing, and spray attacks to compromise passwords. A passwordless authentication strategy mitigates the risk of these attacks.

The Microsoft Entra admin center has a passwordless methods wizard that will help you to select the appropriate method for each of your audiences. You need administrator rights to access this wizard.

Microsoft Entra ID lets you choose which authentication methods can be used during the sign-in process. Users then register for the methods they'd like to use. The Microsoft Authenticator authentication method policy manages both the traditional push MFA method and the passwordless authentication method.

To enable the authentication method for passwordless phone sign-in, complete the following steps:

1.  Sign in to the Microsoft Entra admin center (++++https://entra.microsoft.com/++++) as at least an Authentication Policy Administrator.
2.  Browse to **Protection \> Authentication methods \> Policies**.
3.  Under Microsoft Authenticator, choose the following options:
    1.  **Enable** - Yes or No
    2.  **Target** - All users or Select users
4.  Each added group or user is enabled by default to use Microsoft Authenticator in both passwordless and push notification modes ("Any" mode). To change the mode, for each row for Authentication mode - choose Any, or Passwordless. Choosing Push prevents the use of the passwordless phone sign-in credential.
5.  To apply the new policy, click **Save**.

## Task 4 – Configuration of SSPR

**Entra Self-service Password Reset (SSPR)** is a feature that allows users to reset their passwords or unlock their accounts without contacting an administrator or help desk. It is a cloud-based service that is integrated with Microsoft Entra ID and based on open standards. Entra SSPR provides a user-friendly registration and password reset process that can be accessed from any device or location. Entra SSPR also supports password writeback, which enables users to manage their on-premises passwords through the cloud. Entra SSPR can reduce IT support costs and improve user productivity and security.

In the next lab, you, as an admin, will walk through the process of adding a user to the SSPR security group, which is already set up in your Microsoft 365 tenant. With SSPR enabled, you'll then assume the role of a user and go through the process of registering for SSPR and resetting your password. Lastly, you as the admin, will be able to view audit logs and usage data & insights for SSPR.

In this task you, as the admin, will walk through some of the available configuration settings for SSPR.

1.  Open the Microsoft Edge browser. In the address bar, enter +++**https://entra.microsoft.com+++** and sign in with the admin Microsoft 365 admin credentials provided on the Resources tab.
2.  From the left navigation pane, expand the option for **Protection**, then select **Password reset**.
3.  The properties for self-service password reset are displayed. Select the information icon next to where it says **Self services password reset enabled** to view what the description. Ensure that you’ve chosen the **Selected** option and it is highlighted. Now put your cursor over the information icon next to where it says **Select group** and note that it says, "Defines the group of users who are allowed to reset their own passwords." You must include users in the group, you can’t individually select users.
4.  Select the **No groups selected** link. This opens the **Default password reset policy** window.
5.  Select the **Contoso** group, then click **Select** button at the bottom of the screen.
6.  Once back at the **Password reset \| Properties** screen, click the **Save** button just about the **Self-service password reset enabled** message.
7.  From the left navigation panel of Password reset, select **Authentication Methods**.
8.  In the Number of methods required to rest, select **1**. Note the information box on the screen.
9.  Notice the different methods available to users. **Email** and **Mobile phone (SMS only)** should already be checked; if not, select them.
10. From the left navigation panel of Password reset, select **Registration**.
11. Ensure the setting to Require users to register when signing in is set to **Yes**. Leave the Number of days before users are asked to reconfirm their authentication information, to the default of 180. Take note of the information box on the page.
12. From the left navigation panel of Password reset, select **Notifications**.
13. Ensure the setting to Notify users on password resets is set to **Yes**. Leave the setting for Notify all admins when other admins reset their password to No.
14. Note how the Password reset navigation pane also includes options to view audit logs and Usage & insights.
15. Close the password reset window by selecting **X** on the top-right corner of the window. This returns you to the Microsoft Entra admin center.
16. Keep the Microsoft Entra window open.

## Task 5 – Managing the SSPR Security Group

Managing the SSPR Security Group in Microsoft Entra is important because it determines which users are eligible to use the self-service password reset feature. By selecting the appropriate group, you can control who can register and reset their passwords without contacting an administrator or help desk. You can also use nested groups to enable SSPR for a subset of users within a larger group. For example, you can create a test group for SSPR and add it as a member of another group that contains all your users. This way, you can test the SSPR functionality and user experience before rolling it out to everyone. You can also use the SSPR Security Group to monitor the registration and reset activity of your users and ensure compliance with your security policies.

In this task you, as the admin, will add the user you created in the previous lab exercise to the Contoso security group.

1.  Open the browser tab for the home page of the Microsoft Entra Admin center +++**entra.microsoft.com+++**. If needed, expand **Identity**.
2.  From the left navigation panel, under "Identity", expand **Groups** then select **All groups**.
3.  A list of existing groups is displayed. Select the **Contoso** security group. It will take you to the configuration option for this group.
4.  From the left navigation pane, select **Members**.
5.  From the top of the page, select **+ Add members**.
6.  In the Search box, enter **your created username**. Once the user, **your created username**, appears below the search box, select it then press **Select** from the bottom of the page. You'll be returned to the member’s page. Select **Refresh** from the top of the page. After a few seconds (you may have to hit Refresh a couple times) you should now see **your created username** listed as a member in the Contoso security group.
7.  Sign out from all the browser tabs by clicking on the user icon next to the email address on the top right corner of the screen. Then close all the browser windows.

## Task 6 – Auditing Password Reset

Viewing the audit logs and usage & insights in Entra ID is important for several reasons. Some of them are:

-   You can monitor the activity and health of your identity and access management system, such as who made what changes, when, and where.
-   You can troubleshoot issues and errors related to sign-ins, applications, groups, users, and licenses.
-   You can analyze the usage patterns and trends of your applications and authentication methods, such as which applications are most popular, which methods are most secure, and which ones need improvement.
-   You can comply with regulatory and organizational requirements for data retention and reporting.
-   You can leverage the data from the logs to optimize your identity and access strategy and improve your user experience.

In this task you, as the administrator, will briefly view the Audit logs and the Usage & Insights data associated with password reset.

1.  Open Microsoft Edge.
2.  In the address bar, enter +++**https://entra.microsoft.com+++** and sign in with the Microsoft 365 admin credentials provided on the Resources tab. If prompted for more information to login or to install Microsoft Authenticator, choose **Skip Setup**.
3.  You are in Microsoft Entra admin center. From the left navigation pane, expand the option for **Protection**, then select **Password reset**.
4.  From the left navigation pane, select **Audit logs**. Notice the information available and the available filters. Also note that you can download logs.
5.  Select **Download**. Note that you can format the download as CSV or JSON. Close the window by selecting the **X** on the top right corner of the screen.
6.  From the left navigation pane, select **Usage & insights**.
7.  Notice the information available that pertains to Registration. Note that it may take time to refresh this data, even after you do a refresh, so it may not yet reflect the registration or usage data from the previous task.
8.  From the top of the page select **Usage** to view the number of Self-service password resets and account unlocks by method. Note that it may take time to refresh this data, even after you do a refresh, so it may not yet reflect the usage data from the previous task.
9.  Close the open browser tabs.

In the next lab, you'll explore conditional access MFA, from the perspective of an admin and a user. As the admin, we will create a policy that will require a user to go through multi-factor authentication when accessing a cloud based Microsoft Azure Management application. From a user perspective, you'll see the impact of the conditional access policy, including the process to register for MFA.

## Task 7 – Reset a Password

In this task you, as the admin, will reset the password for **your created username**. This step is needed so you can initially sign in as the user in subsequent tasks.

1.  Open Microsoft Edge. In the address bar, enter +++**https://entra.microsoft.com+++**, and sign in with your admin credentials.
2.  From the left navigation pane, expand **Identity**, expand **Users**, then select **All users**.
3.  Select **your created username** from the list of users.
4.  Select **Reset password** from the top of the page.
5.  When the password reset window opens, select **Reset Password**. IMPORTANT, make a note of the new password (place this new password in the Notepad document you started earlier), as you'll need it in a subsequent task, to be able to sign in as the user.
6.  Close the password reset window by selecting the **X** at the top right corner of the page, then close out of the **your created username** window by selecting the **X** at the top right corner of the page.
7.  From the left navigation panel, select **Home** to return to the Microsoft Entra admin center.
8.  Keep this window open.

## Task 8 – Creating Conditional Access Policies

A conditional access policy in Entra ID is important because it allows you to apply the right access controls when needed to keep your organization secure. A conditional access policy is an if-then statement that evaluates various signals, such as user, device, location, application, and risk, and enforces organizational policies based on the conditions and access controls you specify. For example, you can create a policy that requires multifactor authentication for users who access sensitive applications from outside your trusted network. Conditional access policies can help you achieve the following goals:

-   Empower users to be productive wherever and whenever they need to work.
-   Protect your organization's assets from unauthorized access and potential security breaches.
-   Comply with regulatory and organizational requirements for data retention and reporting.
-   Optimize your identity and access strategy and improve your user experience.

**HOWEVER, PLEASE NOTE:** Security Defaults provide baseline protection for a tenant out of the box (require MFA for all users including Admins, block legacy auth) but its functionality is superseded by conditional access. Conditional Access policies are a way for organizations to customize access based on the needs and/or organizational policies and it may not be necessary to create Conditional Access policies for your organization. Take great care to ensure it’s absolutely necessary and even then consider using the provided templates to start with instead of creating something entirely new.

Conditional Access templates provide a convenient method to deploy new policies aligned with Microsoft recommendations. These templates are designed to provide maximum protection aligned with commonly used policies across various customer types and locations.

In this task, let’s go through and review some popular Conditional Access Policy templates.

1.  Open the browser tab to the home page of the Microsoft Entra admin center. If you previously closed the browser tab, open Microsoft Edge and in the address bar enter +++**https://entra.microsoft.com+++** and sign in with the Microsoft 365 admin credentials provided by the ALH.
2.  From the left navigation pane, expand **Protection** then select **Conditional Access**.
3.  The Conditional access overview page is displayed. Here you will see tiles showing the Policy summary and general alerts. From the left navigation panel, select **Policies**.
4.  Any existing Conditional Access Policies are listed here. Select **+ New policy from template**.
5.  Here you’ll see several template categories. 16 Conditional Access policy templates are organized into the following categories: Secure foundation, Zero Trust, Remote Work, Protect Administrator, and Emerging threats.
6.  When finished reviewing the Conditional Access policy options, close the Templates window by clicking the **X** at the top right of the windows in the Entra admin center.
7.  Details about the provided templates can be found here: ++++https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-policy-common++++

## Task 9 – The Conditional Access What If tool

The **What If** tool in Conditional Access is powerful when trying to understand why a policy was or wasn't applied to a user in a specific circumstance or if a policy would apply in a known state.

1.  The **What If** tool is located in the **Microsoft Entra admin center \> Protection \> Conditional Access \> Policies \>** **What If**. (What If is in the center of the window in the top policy menu)
2.  The What If tool requires only a User or Workload identity to get started. The following additional information is optional but helps narrow the scope for specific cases:
-   Cloud apps, actions, or authentication context
-   IP address
-   Country/Region
-   Device platform
-   Client apps
-   Device state
-   Sign-in risk
-   User risk level
-   Service principal risk (Preview)
-   Filter for devices
1.  This information can be gathered from the user, their device, or the Microsoft Entra sign-in log
2.  For details, see: ++++https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/troubleshoot-conditional-access-what-if++++
