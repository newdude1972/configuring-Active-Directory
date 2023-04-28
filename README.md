# On-premises Active Directory Deployed in the Cloud (Azure)
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

- Create the Domain Controller Virtual Machine (Windows Server 2022)
- Create the Client Virtual Machine (Windows 10)
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in Active Directory
- Join Client-1 to your domain
- Setup Remote Desktop for non-administrative users on Client-1
- Create additional users using a PowerShell script and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>


<p>
Create the Domain Controller VM (Windows Server 2022). Set Domain Controller’s NIC Private IP address to be static. Create the Client VM (Windows 10). Ensure that both VMs are in the same Vnet.
</p>
<br />

<p>
<img src="https://i.imgur.com/KtMdiq7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/qlKYPkE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/L4gX7Gq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GAEGCNk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/AIlZR5o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/icc4coC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/J4dYiJu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>

<p>
Ensure Connectivity between the client and Domain Controller. Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping). Notice the connection failure.
</p>
<br />

<p>
<img src="https://i.imgur.com/w2IXlBk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/I14ujmQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XtLlvuy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4SJLvpN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
<p>
Login to DC-1 and install Active Directory Domain Services. Enable ICMPv4 on the local windows Firewall. Promote DC-1 as a Domain Controler: Setup a new forest as mydomain.com (can be anything, just remember what it is)
Check back at Client-1 to see the ping succeed.
</p>
<br />
