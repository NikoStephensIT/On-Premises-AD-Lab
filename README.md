<p>
<p align="center">
<img src="https://i.imgur.com/YcxQqs2.png"/>
</p>

<h1>Configuring On-premises Active Directory within Azure VMs</h1>

This tutorial outlines the configuration of on-premises Active Directory within Azure Virtual Machines. 

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Powershell

<h2>Operating Systems Used</h2>

- Windows Server 2022
- Windows 10 (21H2)

<p>
To get started, we are going to need to set up our reources in Microsoft Azure. We are going to create a Virtual Machine(VM) and name it "DC-1". This is going to serve as our Domain Controller , eventually we will be downloading our active directory onto this machine. We will be setting up another VM to act as our client next, but while in the DC-1 creation menu, make sure to remember the 'Region' we put our machine in, as we will need to add the client machine to the same region. For 'Image' we'll choose Windows Server 2022.
</p>

<p>
After setting up DC-1, we will need to navigate to the Networking tab under Settings, and click on "Network Interface" 
</p>

<img src="https://i.imgur.com/8LDya1a.png"/>

<p>
From the Network Interface menu, we will go to the IP Configurations menu and change our DC-1's private IP address from Dynamic to Static.
</p>
<img src="https://i.imgur.com/4aeatef.png"/>
<p>
Now we can create our client VM, named "Client-1" using the same resource group and Vnet as our DC-1 machine. Ensure that both VMs are in the same Vnet using Network Watcher. 
</p>

<p>

</p>

<p>

</p>

<p>

</p>

<p>



