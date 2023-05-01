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
<img src="https://i.imgur.com/gBXRCE6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/urKNKym.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/zVt30eL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
<p>
Login to DC-1 and install Active Directory Domain Services. Promote DC-1 as a Domain Controler: Setup a new forest as mydomain.com (can be anything, just remember what it is). DC-1 virtual machine will restart itself. Log back into DC-1 as user: mydomain.com\<created username>. 
</p>
<br />

<p>
<img src="https://i.imgur.com/ThlWkQE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/B5lpE9Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/TYJrf84.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BQcDJ5p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/3q7meKg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/IVz6ESU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Shlkl1D.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/aUQo30V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mlrrc3o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/RlNr1ot.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/M41pp4N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/A0nFo1Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/p7EzzGe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4dSEvXN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/VGG2zFt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
<p>
Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall. The two inbound ICMPv4 rules must be Right clicked then enabled. Check back at Client-1 to see the ping succeed.
</p>
<br />

<p>
<img src="https://i.imgur.com/5KiKrs0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/HopAwRZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/2VMhyRH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/zhCwH63.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
<p>
Create an Admin and Normal User Account in Active Directory. In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”. Create a new OU named “_ADMINS”. Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”. Add jane_admin to the “Domain Admins” Security Group. 
</p>
<br />  


<p>
<img src="https://i.imgur.com/uJWvsTl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/p0aFMmG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/kXIsx6L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ZtpqkTh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ygKQbr9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/lp6r77k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/LNI7p4G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/hfx4C6l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/TZKCi7i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/g9GQqci.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/37ZXHA6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  
<p>
Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin”
</p>
<br />


<p>
<img src="https://i.imgur.com/QsWYCsD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/o2LjAjm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/pOCdrlP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/k3wYCro.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/8aceW2W.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>


<p>
Join Client-1 to your domain (mydomain.com). From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address. From the Azure Portal, restart Client-1. Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart). Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain. Create a new OU named “_CLIENTS” and drag Client-1 into there.
</p>
<br />

<p>
<img src="https://i.imgur.com/9vAwqzZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Ls1wg2Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/KNh8zu6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/YSLWkCy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/UtskkmZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1aHOB5J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/EABVzXU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jZgUz9K.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ylOSihF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CdwBe94.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/32CCg7S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/6EHqhHG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4n80AlK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/pgwBiAx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/T04Ht37.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XwmpO5c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/gKtlkjU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DQ08I69.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

  
<p>
Setup Remote Desktop for non-administrative users on Client-1. Log into Client-1 as mydomain.com\jane_admin and open system properties. Click “Remote Desktop”. Allow “domain users” access to remote desktop. You can now log into Client-1 as a normal, non-administrative user now.
</p>

<p>
<img src="https://i.imgur.com/Ok3Uu1J.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/01Fh7OW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/QYjj4Nn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/DqPupD1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/QWnUNC9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5UfsbNb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4ZzurGq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/lJQH275.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
Create a number of additional users using a PowerShell script and attempt to log into client-1 with one of the users. Login to DC-1 as jane_admin. Open PowerShell_ise as an administrator. Create a new File and paste the contents of the script into it. Run the script and observe the accounts being created. When finished, open Active Directory Users and Computers and observe the accounts in the appropriate Organizational Unit. Attempt to log into Client-1 with one of the accounts (take note of the password in the script)
</p>
<br />


<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
