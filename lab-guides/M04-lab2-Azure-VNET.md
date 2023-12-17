Quickstart: Use the Azure portal to create a virtual network
Article
06/08/2023
14 contributors
In this article
Prerequisites
Sign in to Azure
Create a virtual network and bastion host
Create virtual machines
Show 4 more
This quickstart shows you how to create a virtual network by using the Azure portal. You then create two virtual machines (VMs) in the network, deploy Azure Bastion to securely connect to the VMs from the internet, and communicate privately between the VMs.

A virtual network is the fundamental building block for private networks in Azure. Azure Virtual Network enables Azure resources like VMs to securely communicate with each other and the internet.

Diagram of resources created in virtual network quickstart.

Prerequisites
An Azure account with an active subscription. You can create an account for free.
Sign in to Azure
Sign in to the Azure portal with your Azure account.

Create a virtual network and bastion host
The following procedure creates a virtual network with a resource subnet, an Azure Bastion subnet, and an Azure Bastion host.

In the portal, search for and select Virtual networks.

On the Virtual networks page, select + Create.

On the Basics tab of Create virtual network, enter or select the following information:

Setting	Value
Project details	
Subscription	Select your subscription.
Resource group	Select Create new.
Enter test-rg in Name.
Select OK.
Instance details	
Name	Enter vnet-1.
Region	Select East US 2.
Screenshot of Basics tab of Create virtual network in the Azure portal

Select Next to proceed to the Security tab.

Select Enable Bastion in the Azure Bastion section of the Security tab.

Azure Bastion uses your browser to connect to VMs in your virtual network over secure shell (SSH) or remote desktop protocol (RDP) by using their private IP addresses. The VMs don't need public IP addresses, client software, or special configuration. For more information about Azure Bastion, see Azure Bastion

 Note

Hourly pricing starts from the moment that Bastion is deployed, regardless of outbound data usage. For more information, see Pricing and SKUs.

If you're deploying Bastion as part of a tutorial or test, we recommend that you delete this resource after you finish using it.

Enter or select the following information in Azure Bastion:

Setting	Value
Azure Bastion host name	Enter bastion.
Azure Bastion public IP address	Select Create a public IP address.
Enter public-ip in Name.
Select OK.
Screenshot of enable bastion host in Create virtual network in the Azure portal.

Select Next to proceed to the IP Addresses tab.

In the address space box in Subnets, select the default subnet.

In Edit subnet, enter or select the following information:

Setting	Value
Subnet details	
Subnet template	Leave the default Default.
Name	Enter subnet-1.
Starting address	Leave the default of 10.0.0.0.
Subnet size	Leave the default of /24(256 addresses).
Screenshot of default subnet rename and configuration.

Select Save.

Select Review + create at the bottom of the screen, and when validation passes, select Create.

Create virtual machines
The following procedure creates two virtual machines (VMs) named vm-1 and vm-2 in the virtual network.

In the portal, search for and select Virtual machines.

In Virtual machines, select + Create, then Azure virtual machine.

On the Basics tab of Create a virtual machine, enter or select the following information:

Setting	Value
Project details	
Subscription	Select your subscription.
Resource group	Select test-rg.
Instance details	
Virtual machine name	Enter vm-1.
Region	Select East US 2.
Availability options	Select No infrastructure redundancy required.
Security type	Leave the default of Standard.
Image	Select Ubuntu Server 22.04 LTS - x64 Gen2.
VM architecture	Leave the default of x64.
Size	Select a size.
Administrator account	
Authentication type	Select Password.
Username	Enter azureuser.
Password	Enter a password.
Confirm password	Reenter the password.
Inbound port rules	
Public inbound ports	Select None.
Select the Networking tab at the top of the page.

Enter or select the following information in the Networking tab:

Setting	Value
Network interface	
Virtual network	Select vnet-1.
Subnet	Select subnet-1 (10.0.0.0/24).
Public IP	Select None.
NIC network security group	Select Advanced.
Configure network security group	Select Create new.
Enter nsg-1 for the name.
Leave the rest at the defaults and select OK.
Leave the rest of the settings at the defaults and select Review + create.

Review the settings and select Create.

Repeat the previous steps to create a second virtual machine with the following settings:

Setting	Value
Virtual machine name	Enter vm-2.
Virtual network	Select vnet-1.
Subnet	Select subnet-1 (10.0.0.0/24)
Public IP	Select None.
NIC network security group	Select Advanced.
Configure network security group	Select nsg-1
 Note

Virtual machines in a virtual network with a bastion host don't need public IP addresses. Bastion provides the public IP, and the VMs use private IPs to communicate within the network. You can remove the public IPs from any VMs in bastion hosted virtual networks. For more information, see Dissociate a public IP address from an Azure VM.

 Note

Azure provides a default outbound access IP for VMs that either aren't assigned a public IP address or are in the back-end pool of an internal basic Azure load balancer. The default outbound access IP mechanism provides an outbound IP address that isn't configurable.

The default outbound access IP is disabled when one of the following events happens:

A public IP address is assigned to the VM.
The VM is placed in the back-end pool of a standard load balancer, with or without outbound rules.
An Azure Virtual Network NAT gateway resource is assigned to the subnet of the VM.
VMs that you create by using virtual machine scale sets in flexible orchestration mode don't have default outbound access.

For more information about outbound connections in Azure, see Default outbound access in Azure and Use Source Network Address Translation (SNAT) for outbound connections.

Connect to a virtual machine
In the portal, search for and select Virtual machines.

On the Virtual machines page, select vm-1.

In the Overview of vm-1, select Connect.

In the Connect to virtual machine page, select the Bastion tab.

Select Use Bastion.

Enter the username and password you created when you created the VM, and then select Connect.

Communicate between VMs
At the bash prompt for vm-1, enter ping -c 4 vm-2.

You get a reply similar to the following message:

Output

Copy
azureuser@vm-1:~$ ping -c 4 vm-2
PING vm-2.3bnkevn3313ujpr5l1kqop4n4d.cx.internal.cloudapp.net (10.0.0.5) 56(84) bytes of data.
64 bytes from vm-2.internal.cloudapp.net (10.0.0.5): icmp_seq=1 ttl=64 time=1.83 ms
64 bytes from vm-2.internal.cloudapp.net (10.0.0.5): icmp_seq=2 ttl=64 time=0.987 ms
64 bytes from vm-2.internal.cloudapp.net (10.0.0.5): icmp_seq=3 ttl=64 time=0.864 ms
64 bytes from vm-2.internal.cloudapp.net (10.0.0.5): icmp_seq=4 ttl=64 time=0.890 ms
Close the Bastion connection to VM1.

Repeat the steps in Connect to a virtual machine to connect to VM2.

At the bash prompt for vm-2, enter ping -c 4 vm-1.

You get a reply similar to the following message:

Output

Copy
azureuser@vm-2:~$ ping -c 4 vm-1
PING vm-1.3bnkevn3313ujpr5l1kqop4n4d.cx.internal.cloudapp.net (10.0.0.4) 56(84) bytes of data.
64 bytes from vm-1.internal.cloudapp.net (10.0.0.4): icmp_seq=1 ttl=64 time=0.695 ms
64 bytes from vm-1.internal.cloudapp.net (10.0.0.4): icmp_seq=2 ttl=64 time=0.896 ms
64 bytes from vm-1.internal.cloudapp.net (10.0.0.4): icmp_seq=3 ttl=64 time=3.43 ms
64 bytes from vm-1.internal.cloudapp.net (10.0.0.4): icmp_seq=4 ttl=64 time=0.780 ms
Close the Bastion connection to VM2.

Clean up resources
When you're done using the resources created, you can delete the resource group and all its resources.

In the Azure portal, search for and select Resource groups.

On the Resource groups page, select the test-rg resource group.

On the test-rg page, select Delete resource group.

Enter test-rg in Enter resource group name to confirm deletion and select Delete.
