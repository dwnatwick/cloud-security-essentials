Quickstart: Create a key vault using the Azure portal
Article
07/20/2023
5 contributors
In this article
Sign in to Azure
Create a vault
Clean up resources
Next steps
Azure Key Vault is a cloud service that provides a secure store for keys, secrets, and certificates. For more information on Key Vault, see About Azure Key Vault; for more information on what can be stored in a key vault, see About keys, secrets, and certificates.

If you don't have an Azure subscription, create a free account before you begin.

In this quickstart, you create a key vault with the Azure portal.

Sign in to Azure
Sign in to the Azure portal.

Create a vault
From the Azure portal menu, or from the Home page, select Create a resource.
In the Search box, enter Key Vault.
From the results list, choose Key Vault.
On the Key Vault section, choose Create.
On the Create key vault section provide the following information:
Name: A unique name is required. For this quickstart, we use Contoso-vault2.
Subscription: Choose a subscription.
Under Resource Group, choose Create new and enter a resource group name.
In the Location pull-down menu, choose a location.
Leave the other options to their defaults.
Select Create.
Take note of these two properties:

Vault Name: In the example, this is Contoso-Vault2. You'll use this name for other steps.
Vault URI: In the example, the Vault URI is https://contoso-vault2.vault.azure.net/. Applications that use your vault through its REST API must use this URI.
At this point, your Azure account is the only one authorized to perform operations on this new vault.

Output after Key Vault creation completes

Clean up resources
Other Key Vault quickstarts and tutorials build upon this quickstart. If you plan to continue on to work with subsequent quickstarts and tutorials, you may wish to leave these resources in place. When no longer needed, delete the resource group, which deletes the Key Vault and related resources. To delete the resource group through the portal:

Enter the name of your resource group in the Search box at the top of the portal. When you see the resource group used in this quickstart in the search results, select it.
Select Delete resource group.
In the TYPE THE RESOURCE GROUP NAME: box type in the name of the resource group and select Delete.

Tutorial: Encrypt and decrypt blobs using Azure Key Vault
Article
11/15/2022
17 contributors
In this article
Prerequisites
Assign a role to your Microsoft Entra user
Set up your project
Set environment variable
Show 7 more
In this tutorial, you learn how to use client-side encryption to encrypt and decrypt blobs using a key stored with Azure Key Vault.

Azure Blob Storage supports both service-side and client-side encryption. For most scenarios, Microsoft recommends using service-side encryption features for ease of use in protecting your data. To learn more about service-side encryption, see Azure Storage encryption for data at rest.

The Azure Blob Storage client library for .NET supports client-side data encryption within applications before uploading to Azure Storage, and decrypting data while downloading to the client. The library also supports integration with Azure Key Vault for key management.

This tutorial shows you how to:

Configure permissions for an Azure Key Vault resource
Create a console application to interact with resources using .NET client libraries
Add a key to a key vault
Configure client-side encryption options using a key stored in a key vault
Create a blob service client object with client-side encryption enabled
Upload an encrypted blob, then download and decrypt the blob
Prerequisites
Azure subscription - create an account for free
Azure storage account - create a storage account
Key vault - create one using Azure portal, Azure CLI, or PowerShell
Visual Studio 2022 installed

Assign a role to your Microsoft Entra user
When developing locally, make sure that the user account that is accessing the key vault has the correct permissions. You'll need the Key Vault Crypto Officer role to create a key and perform actions on keys in a key vault. You can assign Azure RBAC roles to a user using the Azure portal, Azure CLI, or Azure PowerShell. You can learn more about the available scopes for role assignments on the scope overview page.

In this scenario, you'll assign permissions to your user account, scoped to the key vault, to follow the Principle of Least Privilege. This practice gives users only the minimum permissions needed and creates more secure production environments.

The following example shows how to assign the Key Vault Crypto Officer role to your user account, which provides the access you'll need to complete this tutorial.

 Important

In most cases it will take a minute or two for the role assignment to propagate in Azure, but in rare cases it may take up to eight minutes. If you receive authentication errors when you first run your code, wait a few moments and try again.

Azure portal
Azure CLI
PowerShell
In the Azure portal, locate your key vault using the main search bar or left navigation.

On the key vault overview page, select Access control (IAM) from the left-hand menu.

On the Access control (IAM) page, select the Role assignments tab.

Select + Add from the top menu and then Add role assignment from the resulting drop-down menu.

A screenshot showing how to assign a role in Azure portal.

Use the search box to filter the results to the desired role. For this example, search for Key Vault Crypto Officer and select the matching result and then choose Next.

Under Assign access to, select User, group, or service principal, and then choose + Select members.

In the dialog, search for your Microsoft Entra username (usually your user@domain email address) and then choose Select at the bottom of the dialog.

Select Review + assign to go to the final page, and then Review + assign again to complete the process.
