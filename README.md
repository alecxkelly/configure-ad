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

• Create a Domain Admin User within the Domain

• Join client-1 to the domain name (mydomain.com as example)

• Setup Remote Desktop for non-administrative users on client-1

• Create a bunch of additional users in Powershell 

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Establish the virtual machine in Microsoft Azure in order to do a remote desktop connection. By creating a Domain Controller and Client user this is how you are able to create the Active Directory database that allows the domain controller to be able to store information and give access to users to connect to certain resources within the network
</p>
<br />

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
Go back to Domain Controller -> After aobve steps of clicking on "Promote this server to a domain controller" -> Click on it -> Add a new forest -> Type in the domain name -> Next -> Next -> Ensure Create DNS delegation is unchecked -> Next -> Next -> Install and wait for the new forest to be installed for the computer to turn into a Domain controller completely -> Automatically restarts -> Login again into Domain Controller using the domain "\" domain controller name and or user name
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once restarted you will be logged back in, now as again as a domain controller -> Start -> Click Windows Adminastrative tools -> Click Active Directory Users and Computers
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create Organizational Unit (Here is how you create a user/s and or admins within an Organization) -> Create a new Organizational Unit for ADMINS by Right-Clicking domain name site -> New -> Organizational Unit(Add Organization Unit in the domain site) -> Click Ok -> now repeat these steps and create organazational unit for users named Employees 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now create a domain admin user within the domain by Right-Clicking ADMINS folder within domain name still in Active Directory Users and Computers folder -> New -> User -> Fill out using the users credentials -> Next -> Finish(the account isnt an admin yet, to make it fully active as an admin) -> We must now add the admin to the built-in "Security group" -> Back to Active Directory Users and Computers -> click on Admins -> Right-Click the admin user -> properties  -> Member of -> domain admins -> Check Names -> OK -> Apply -> OK(Now the account is an actual domain admin)   
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
Now to join Clients/Users to a domain name -> Login as the original local admin user in Client 1 and join into the domain(computer will restart -> Right-Click start menu -> System -> Rename this PC -> Change -> Ensure "Member of" Domain category is ticked -> add the domain name site -> OK -> add the Domain Controller using the domain admin credentials for Computer Name/Domain changes tab -> OK -> Restart -> Login to Domain Controller using an admin login to verify Client-1 shows up in ADUC(Active Directory Users and Computers)
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now to Setup a Remote Desktop for non administrative users on client-1 -> login to client-1 as admin/domain user -> Open system properties -> Click “Remote Desktop” -> Allow “domain users” access to remote desktop -> OK -> OK -> Now all domain users should be allowed to login to that computer
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now to create additional users as a domain admin -> login as a domain admin -> Right-Click on Powershell ISE and run as administrator -> PSh opens -> Run coded scrpit in Power Shell ISE -> Click RUN icon -> Users will be created in the PSh ISE 
</p>
<br />



