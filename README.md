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
<img src="https://i.imgur.com/aMWcNRA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
</h2>STEP 2: ENSURE CONNECTIVITY BETWEEN THE CLIENT AND DOMAIN CONTOLLER</h2>

  - Login to Client-1 and ping DC-1's Private IP Address with ping -t (perpetual ping)
  - Login to Domain Controller and enable ICMPv4 in on the local windows Firewall
  - Check back at Client-1 to see the ping succeed
</p>
<br />

<p>
<img src="https://i.imgur.com/YKpMsef.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 3: INSTALL ACTIVE DIRECTORY</h2>

  - Google and Download VC_redist.8.exe
</p>
<br />

<p>
<img src="https://i.imgur.com/YKpMsef.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 4: CREATE AND ADMIN AND NORMAL USER ACCOUNT</h2>

  - Google and Download VC_redist.8.exe
</p>
<br />

<p>
<img src="https://i.imgur.com/YKpMsef.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 5: JOIN CLIENT-1 TO YOUR DOMAIN</h2>

  - Google and Download VC_redist.8.exe
</p>
<br />

<p>
<img src="https://i.imgur.com/YKpMsef.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 6: SETUP REMOTE DESKTOP FOR NON-ADMINISTRATIVE USERS ON CLIENT-1</h2>

  - Google and Download VC_redist.8.exe
</p>
<br />

<p>
<img src="https://i.imgur.com/YKpMsef.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
</h2>STEP 7: CREATE A BUNCH OF ADDITIONAL USERS AND ATTEMPT TO LOG INTO CLIENT-1 WITH ONE OF THE USERS</h2>

  - Google and Download VC_redist.8.exe
</p>
<br />
