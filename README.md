<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

• Microsoft Azure (Virtual Machines/Compute)

• Remote Desktop

• Active Directory Domain Services

• PowerShell

<h2>Operating Systems Used </h2>

• Windows Server 2022

• Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

• Login into Domain controller and Install Active Directory

• Create an Admin and Normal User Account in AD

• Join Client-1 to your domain (mydomain.com)

• Setup Remote Desktop for non-administrative users on Client-1

• Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Service Manager from start window -> Add roles and features -> Click Next, Click Next again, ensure operating system of the domain controller is selected -> Check Active Directory Domain Services box -> Add features -> Next -> Next -> Next -> Next -> Restart is reuqired box pops up -> Select Yes -> Install complete.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Close out roles and features -> Look at the top right at yellow flag(Yellow flag isnt appeared becasue I have done this step already) -> (Acting as if Yellow flag did appear, you'd Click on it and select Promote the Server to a Domain Controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that Active Directory is installed we are going to configure it to become a Domain Controller within a new forest in our Domain.
Go back to Domain Controller -> After aobve steps of clicking on "Promote this server to a domain controller" -> Click on it -> Add a new forest -> Type in the domain name -> Next -> Next -> Ensure Create DNS delegation is unchecked -> Next -> Next -> Install and wait for the new forest to be installed for the computer to turn into a Domain controller completely -> Automatically restarts -> Login again into Domain Controller using the domain \ domain controller name 
</p>
<br />
