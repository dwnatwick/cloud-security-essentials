Sign up for an AWS account

If you do not have an AWS account, complete the following steps to create one.

To sign up for an AWS account
Open https://portal.aws.amazon.com/billing/signup.

Follow the online instructions.

Part of the sign-up procedure involves receiving a phone call and entering a verification code on the phone keypad.

When you sign up for an AWS account, an AWS account root user is created. The root user has access to all AWS services and resources in the account. As a security best practice, assign administrative access to an administrative user, and use only the root user to perform tasks that require root user access.

AWS sends you a confirmation email after the sign-up process is complete. At any time, you can view your current account activity and manage your account by going to https://aws.amazon.com/ and choosing My Account.

Create an administrative user

After you sign up for an AWS account, create an administrative user so that you don't use the root user for everyday tasks.

Secure your AWS account root user
Sign in to the AWS Management Console as the account owner by choosing Root user and entering your AWS account email address. On the next page, enter your password.

For help signing in by using root user, see Signing in as the root user in the AWS Sign-In User Guide.

Turn on multi-factor authentication (MFA) for your root user.

For instructions, see Enable a virtual MFA device for your AWS account root user (console) in the IAM User Guide.

Create an administrative user
For your daily administrative tasks, grant administrative access to an administrative user in AWS IAM Identity Center.

For instructions, see Getting started in the AWS IAM Identity Center User Guide.

Sign in as the administrative user
To sign in with your IAM Identity Center user, use the sign-in URL that was sent to your email address when you created the IAM Identity Center user.

For help signing in using an IAM Identity Center user, see Signing in to the AWS access portal in the AWS Sign-In User Guide.

Prepare for least-privilege permissions

Using least-privilege permissions is an IAM best practice recommendation. The concept of least-privilege permissions is to grant users the permissions required to perform a task and no additional permissions. As you get set up, consider how you are going to support least-privilege permissions. Both the root user and the administrator user have powerful permissions that aren't required for everyday tasks. While you are learning about AWS and testing out different services we recommend that you create at least one additional user in IAM Identity Center with lesser permissions that you can use in different scenarios. You can use IAM policies to define the actions that can be taken on specific resources under specific conditions and then connect to those resources with your lesser privileged account.

Step 1: Create a policy to enforce MFA sign-in

You begin by creating an IAM customer managed policy that denies all permissions except those required for IAM users to manage their own credentials and MFA devices.

Sign in to the AWS Management Console as a user with administrator credentials. To adhere to IAM best practices, don't sign in with your AWS account root user credentials.

Important
IAM best practices recommend that you require human users to use federation with an identity provider to access AWS using temporary credentials instead of using IAM users with long-term credentials.

Open the IAM console at https://console.aws.amazon.com/iam/.

In the navigation pane, choose Policies, and then choose Create policy.

Choose the JSON tab and copy the text from the following JSON policy document: AWS: Allows MFA-authenticated IAM users to manage their own credentials on the My security credentials page.

Paste the policy text into the JSON text box. Resolve any security warnings, errors, or general warnings generated during policy validation, and then choose Next.

Note
You can switch between the Visual editor and JSON options anytime. However, the policy above includes the NotAction element, which is not supported in the visual editor. For this policy, you will see a notification on the Visual editor tab. Return to JSON to continue working with this policy.

This example policy does not allow users to reset a password while signing in to the AWS Management Console for the first time. We recommend that you do not grant permissions to new users until after they sign in and reset their password.

On the Review and create page, type Force_MFA for the policy name. For the policy description, type This policy allows users to manage their own passwords and MFA devices but nothing else unless they authenticate with MFA. In the Tags area, you can optionally add tag key-value pairs to the customer managed policy. Review the permissions granted by your policy, and then choose Create policy to save your work.

The new policy appears in the list of managed policies and is ready to attach.

Step 2: Attach policies to your test user group

Next you attach two policies to the test IAM user group, which will be used to grant the MFA-protected permissions.

In the navigation pane, choose User groups.

In the search box, type EC2MFA, and then choose the group name (not the check box) in the list.

Choose the Permissions tab, choose Add permissions, and then choose Attach policies.

On the Attach permission policies to EC2MFA group page, in the search box, type EC2Full. Then select the check box next to AmazonEC2FullAccess in the list. Don't save your changes yet.

In the search box, type Force, and then select the check box next to Force_MFA in the list.

Choose Attach policies.

Step 3: Test your user's access

In this part of the tutorial, you sign in as the test user and verify that the policy works as intended.

Sign in to your AWS account as MFAUser with the password you assigned in the previous section. Use the URL: https://<alias or account ID number>.signin.aws.amazon.com/console

Choose EC2 to open the Amazon EC2 console and verify that the user has no permissions to do anything.

In the navigation bar on the upper right, choose the MFAUser user name, and then choose Security credentials.


            AWS Management Console Security credentials link
          
Now add an MFA device. In the Multi-factor Authentication (MFA) section, choose Assign MFA device.

Note
You might receive an error that you are not authorized to perform iam:DeleteVirtualMFADevice. This could happen if someone previously began assigning a virtual MFA device to this user and cancelled the process. To continue, you or another administrator must delete the user's existing unassigned virtual MFA device. For more information, see I am not authorized to perform: iam:DeleteVirtualMFADevice.

For this tutorial, we use a virtual (software-based) MFA device, such as the Google Authenticator app on a mobile phone. Choose Authenticator app, and then click Next.

IAM generates and displays configuration information for the virtual MFA device, including a QR code graphic. The graphic is a representation of the secret configuration key that is available for manual entry on devices that do not support QR codes.

Open your virtual MFA app. (For a list of apps that you can use for hosting virtual MFA devices, see Virtual MFA Applications.) If the virtual MFA app supports multiple accounts (multiple virtual MFA devices), choose the option to create a new account (a new virtual MFA device).

Determine whether the MFA app supports QR codes, and then do one of the following:

From the wizard, choose Show QR code. Then use the app to scan the QR code. For example, you might choose the camera icon or choose an option similar to Scan code, and then use the device's camera to scan the code.

In the Set up device wizard, choose Show secret key, and then type the secret key into your MFA app.

When you are finished, the virtual MFA device starts generating one-time passwords.

In the Set up device wizard, in the Enter the code from your authenticator app. box, type the one-time password that currently appears in the virtual MFA device. Choose Register MFA.

Important
Submit your request immediately after generating the code. If you generate the codes and then wait too long to submit the request, the MFA device is successfully associated with the user. However, the MFA device is out of sync. This happens because time-based one-time passwords (TOTP) expire after a short period of time. If this happens, you can resync the device.

The virtual MFA device is now ready to use with AWS.

Sign out of the console and then sign in as MFAUser again. This time AWS prompts you for an MFA code from your phone. When you get it, type the code in the box and then choose Submit.

Choose EC2 to open the Amazon EC2 console again. Note that this time you can see all the information and perform any actions you want. If you go to any other console as this user, you see access denied messages. The reason is that the policies in this tutorial grant access only to Amazon EC2.
