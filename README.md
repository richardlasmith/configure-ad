<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


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
Open Azure, Search VM, Create a new VM, then create a new Resource Group. Name the resource group AD-Lab (Active Directory). Name the Virtual Machine, "DC-1 (Domain Controller), and the region should be in the exact location as Client-1. For image, use Windows Server 2022 and two vcpu for processing speed and performance. Create a user name and PW for DC-1. Create the second VM using the name client-1. 
</p>
<br />

<p>
<img src="https://i.imgur.com/PrcZCvL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set the Domain Controller NIC Private IP Address to be Static. Do this by going to DC-1/ Networking/ IP Configuration/ Change from Dynamic to Static. This means the IP Address will never change. Make sure both DC-1 and Client-1 are in the same DC-1-vent/default
</p>
<br />

<p>
<img src="https://i.imgur.com/DtRfuwC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/dLyLmCB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ensure connectivity between the Client VM and Domain Controller. Log into client-1 with Remote Desktop and ping DC-1's Private IP address with ping -t<ip address> perpetual ping). Then log into the Domain Controller and enable ICNMPv4 on the local windows Firewall. Check back at client-1 to see the ping succeed. Open DC-1 and configure Firewall to allow successful ping. Go to start type, wf. msc, inbound rules, sort by protocol, find ICMP4, and enable. 
</p>
<br />

<p>
<img src="https://i.imgur.com/OodVW11.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Active Directory on DC-1. Go to Add roles and features/ Active Directory Domain Services. Once installation is completed, click the yellow caution flag and promotion to the domain controller on the top right, add a new forest (Name domain) mydomain.com, and create a password. 
</p>
<br />

<p>
<img src="https://i.imgur.com/eGNTTzJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that DC-1 VM has re-started, Create a couple of Organizational Units (folder). (1) called employees, (2) called admin. We will now create an Admin user called Jane Doe. Set a password and uncheck the create new PW at login. 
</p>
<br />

<p>
<img src="https://i.imgur.com/mCgq8UK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Assign Jane Doe to the Security Group Domain Admin group. 
</p>
<br />

<p>
<img src="https://i.imgur.com/DxwSlos.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/neBpcNA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log out of labuser and re-log back in with Jane_Admin.
</p>
<br />

<p>
<img src="https://i.imgur.com/LIIj3mZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/heeIW2Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/CzlBtHG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Join Client-1 to Domain. Set the client-1 DNS setting to the DC's private IP address, and log into client-1 with Jane_admin. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Xe2xnCz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set up so all domain users are able to remote log in Client-1.  Client-1 / System properties/ Remote Desktop / Select users that can remotely log in / Add Domain Users (Built in Group).
</p>
<br />

<p>
<img src="https://i.imgur.com/SQPTV6s.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a bunch of additional users and attempt to log into client-1 with one of the users --->Login to DC-1 as jane_admin --->Open PowerShell_ise as an administrator. Create a new File and paste the contents of the script into it (https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1) --->Run the script and observe the accounts being created. When finished, open ADUC and observe the accounts in the appropriate OU attempt to log into Client-1 with one of the accounts (take note of the password in the script). 

</p>
<br />

<p>
<img src="https://i.imgur.com/9TAvaBf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
<img src="https://i.imgur.com/xLuF0Jm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Attempt to log into Client-1 with one of the accounts (take note of the password in the script)
</p>
<br />

ACTIVE DIRECTORY LAB IS FINISHED!
