<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- In Azure Create 2 VMs
- Ensure Connectivity Between the 2 VMs
- Install Active Directory 
- Create an Admin and Normal User Account in AD (Active Directory)
- Join Client-1 to your Domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with a user.


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/zdhQrNs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/dc9GXYK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Azure, Search VM, Create new VM, then create new Resource Group. Name the resource group AD-Lab (Active Directory). Name the Virtural Machine, "DC-1 (Domain Controller), region should be in the same location as Client-1. For image, use Windows Server 2022, and use 2 vcpu for processing speed and performance. Create a user name and pw for DC-1. Create the second VM using the name client-1. 
</p>
<br />

<p>
<img src="https://i.imgur.com/PrcZCvL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set the Domain Controller NIC Private IP Address to be Static. Do this by going to DC-1/ Networking/ IP Confguration/ Change from Dynamic to Static. This means the IP Address will never change. Make sure both DC-1 and Client-1 are in the same DC-1-vnet/default
</p>
<br />

<p>
<img src="https://i.imgur.com/DtRfuwC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/dLyLmCB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure connectivity between the Client VM and Domain Controller. Log into client-1 with Remote Desktop and ping DC-1's Private IP address with ping -t<ip address> perpetual ping). Then log into the Domain Controller and enable ICNMPv4 in on the local windows Firewall. Check back at client-1 to see the ping succeed. Open DC-1 and configure Firewall to allow successful ping. Go to start type, wf.msc, inbound rules, sort by protocol, find ICMP4 and enable. 
</p>
<br />

<p>
<img src="https://i.imgur.com/OodVW11.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Active Directory on DC-1. Go to Add roles and features/ Active Directory Domain Services, once installation is completed, on the top right, click the yellow caution flag and promtion to doamin controller, add a new forest (Name domain) mydomain.com, create password. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
