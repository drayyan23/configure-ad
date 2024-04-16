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

- Setup Resources in Azure
-Ensure Connectivity between the client and Domain Controller
-Install Active Directory
-Create an Admin and Normal User Account in AD
-Setup Remote Desktop for non-administrative users on Client-1
-Create a several additional users and attempt to log into client-1 with one of the users


<h2>Deployment and Configuration Steps</h2>

<p>
</p>
<p>
-To accomplish the task, start by creating a Domain Controller VM named "DC-1" on Windows Server 2022 through the cloud provider's management console. Note the automatically generated Resource Group and Virtual Network (Vnet). Set the NIC's private IP address for the Domain Controller to be static. Then, create a Client VM named "Client-1" using the same Resource Group and Vnet as "DC-1." Ensure both VMs are within the same Virtual Network, verifying connectivity either through Network Watcher or Vnet settings. This process establishes an interconnected environment where the Domain Controller and Client VM can effectively communicate and utilize domain services.</p>
<br />

<p>
</p>
<p>
-To ensure connectivity between the client machine (Client-1) and the Domain Controller (DC-1), first, log into Client-1 via Remote Desktop and initiate a perpetual ping to DC-1's private IP address. Then, enable ICMPv4 on the Domain Controller's local Windows Firewall. Finally, check back on Client-1 to confirm the successful ping response from DC-1, indicating successful communication between the two machines.</p>
<br />

<p>
</p>
<p>
-To install Active Directory, log into DC-1, install Active Directory Domain Services, and promote it as a Domain Controller, establishing a new forest with a domain name like "mydomain.com." After restarting, log back into DC-1 using the user account format "mydomain.com\labuser" to access the Active Directory environment.</p>
<br />

</p>
<p>
-To set up user accounts in Active Directory, first organize them by creating an "Employees" Organizational Unit (OU) and an "_ADMINS" OU using Active Directory Users and Computers (ADUC). Within "_EMPLOYEES," create a user profile for "Jane Doe" with the username "jane_admin" and assign her a password. Elevate her privileges by adding "jane_admin" to the "Domain Admins" Security Group. Then, log out or close the Remote Desktop connection to DC-1, and log back in using "mydomain.com\jane_admin" as the admin account. From there, "jane_admin" can be used for all administrative tasks within the Active Directory environment.
</p>
<br />
</p>
<p>
-To set up Remote Desktop for non-administrative users on Client-1 by logging in as "mydomain.com\jane_admin," accessing system properties, and allowing "domain users" access to remote desktop. This enables normal users to log in remotely. Typically, this is managed through Group Policy for efficient system-wide changes.</p>
<br />
</p>
<p>
-To create additional users, access Active Directory on DC-1, and create the desired user accounts. Then, try logging into Client-1 using one of the newly created accounts. After logging in as "jane_admin" on DC-1, open PowerShell_ise as an administrator and attempt to log into Client-1 using one of the user accounts created earlier.</p>
<br />
