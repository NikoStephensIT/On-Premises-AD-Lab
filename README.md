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

</br>

<h4>Setup Resources in Azure</h4>
<p>
To get started, we are going to need to set up our reources in Microsoft Azure. We are going to create a Virtual Machine(VM) and name it "DC-1". This is going to serve as our Domain Controller , eventually we will be downloading our active directory onto this machine. We will be setting up another VM to act as our client next, but while in the DC-1 creation menu, make sure to remember the 'Region' we put our machine in, as we will need to add the client machine to the same region. For 'Image' we'll choose Windows Server 2022.
</p>

<p>
After setting up DC-1, we will need to navigate to the Networking tab under Settings, and click on "Network Interface" 
</p>

<img src="https://i.imgur.com/uCiAXHR.png"/>

<p>
From the Network Interface menu, we will go to the IP Configurations menu and change our DC-1's private IP address from Dynamic to Static.
</p>
<img src="https://i.imgur.com/uCiAXHR.png"/>
<p>
Now we can create our client VM, named "Client-1" using the same resource group and Vnet as our DC-1 machine. Ensure that both VMs are in the same Vnet using Network Watcher. 
</p>
</br>
<h4>Ensure Connectivity between the client and Domain Controller</h4>
<p>
  Login to Client-1 with Remote Desktop and open the Command Terminal by typing cmd into the Windows search bar on the bottom left of the home screen. In the comand terminal we're going to use the "ping -t <ip address>" command to perpetually ping DC-1's private IP address. DC-1s private IP address can be found and copied directly within the DC-1 VM menu in Azure. At first, we're going to notice this does not work. 
<p>
  This is because we still need to enable ICMPv4 on DC-1's local Windows firewall. This can be done by navigating to wf.msc in the Windows search bar, which is the Windows Defender Firewall with Advanced Security. On the leftside dropdown menu you will see an "Inbound Rules" option, select this one. Sort by protocol, and look for ICMPv4. For the two ICMPv4 protocol with the root name of "Core Networking Diagnostics" we will be left clicking and enabling these rules. 
</p>
<img src="https://i.imgur.com/NZGePI0.png"/>
<p>
  Go back to your Client-1 command terminal and confirm that the ping is going through.
</p>
<img src="https://i.imgur.com/N8f8Oii.png"/>
<p>



