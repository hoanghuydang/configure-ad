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

- Step 1: Setup Resources in Azure
- Step 2: Ensure Connectivity between the client and Domain Controller
- Step 3: Install Active Directory
- Step 4: Create an Admin and Normal User Account in AD
- Step 5: Join Client-1 to your domain (mydomain.com)
- Step 6: Setup Remote Desktop for non administrative users on Client-1
- Step 7: Create a bunch of additional users and attempt to log into Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/SiJd4NR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/ialiLSp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/aKldhIh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/wPTtIb4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 1: SETUP RESOURCES IN AZURE</h2>

  - Create the Domain Controller VM (Windows Server 2022) named "DC-1"
  - Create the Client VM (Windows 10) named Client-1. Use the same resource group and Vnet that get created at this time
  - Set the Domain Controller's NIC Private IP address to be static
  - Ensure that both VMs are in the same Vnet (you can check the topoplogy with Network Watcher)
</p>
<br />

<p>
<img src="https://i.imgur.com/lOf4eqZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/N5lYqkz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/w7qdfLQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 2: ENSURE CONNECTIVITY BETWEEN THE CLIENT AND DOMAIN CONTROLLER</h2>

  - Login to Client-1 and ping DC-1's Private IP Address with ping -t (perpetual ping)
  - Login to Domain Controller and enable ICMPv4 in on the local windows Firewall
  - Check back at Client-1 to see the ping succeed
</p>
<br />

<p>
<img src="https://i.imgur.com/ecPXY1o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/RP7E106.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 3: INSTALL ACTIVE DIRECTORY</h2>

  - Login to DC-1 and install Active Directory Domain Services
  - Promote as a DC: Setup a new forest as mydomain.com
  - Restart and log back into the DC-1
</p>
<br />

<p>
<img src="https://i.imgur.com/hlVvmcc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/bep6ATM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/49Sv6yP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/pZhhtKG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 4: CREATE AND ADMIN AND NORMAL USER ACCOUNT</h2>

  - In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called "Employees"
  - Create a new employee named "Bob Jones"
  - Create a new OU named "_ADMINS"
  - Create a new employee Jane Doe
  - Add jane_admin to the "Domain Admins" Security Group
  - Log Out/ close the connection to DC-1 and log back in as "mydomain.com\jane_admin"
  - User jane_admin as your admin account from now on
</p>
<br />

<p>
<img src="https://i.imgur.com/pobKdhf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/yUnl2eb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/pwpQ05i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/LATx53T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 5: JOIN CLIENT-1 TO YOUR DOMAIN</h2>

  - From the Azure Portal, set Client-1's DNS settings to the DC's Private IP address
  - From the Azure Portal, restart Client-1
  - Login to Client-1 as the original local admin and join it to the domain (computer will restart)
  - Login to the Domain Controller and verify Client-1 shows up in the ADUC
</p>
<br />

<p>
<img src="https://i.imgur.com/4QA7Zou.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 6: SETUP REMOTE DESKTOP FOR NON-ADMINISTRATIVE USERS ON CLIENT-1</h2>

  - Log into Client-1 as mydomain.com/jane_admin and open system properties
  - Click "Remote Desktop"
  - Allow "domain users" access to remote desktop
  - Log out of Client-1 and log back in as mydomain.com\ 'employee' to test it
  - You can now log into Client-1 as a normal, non administrative user now
  
</p>
<br />

<p>
<img src="https://i.imgur.com/0Njk5eE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/Ji3BWkP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/WugEFX1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/7cXUyud.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <p>
<img src="https://i.imgur.com/4XItpBF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  <img src="https://i.imgur.com/JXKsxqV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 7: CREATE A BUNCH OF ADDITIONAL USERS AND ATTEMPT TO LOG INTO CLIENT-1 WITH ONE OF THE USERS</h2>

  - Login to DC-1 as jane_admin
  - Open Powershell_ise as an administrator
  - Create a new File and paste the contents of the script into it
  - Run the script and observe the accounts in the appropriate OU
  - Attempt to log into Client-1 with one of the accounts
</p>
<br />
