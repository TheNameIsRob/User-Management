# User-Management
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Mangaging different user tasks (Azure)</h1>
This tutorial emphasizes managing different user tasks such as creating users and creating rules catering to specific kinds of accounts..<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Steps</h2>

- Setting up Remote Dekstop for non-adminstrative users on Client-1
- Creating additional users through the domain controller and using the accounts to login.

<h2>Setup Remote Desktop for non-administrative users on Client-1</h2>
<h4>Log into the Client-1 virtual machine through remote desktop</h4>
<img src="https://i.imgur.com/3zL5Gnm.png">

<h4>Within the Client-1 virtual machine, right click Windows start and click "Systems" for systems properties. In the open tab click "Remote"</h4>
<img src="https://i.imgur.com/mU87RXd.png">
<h4>Scroll down in the remote desktop tab and click "Select users that can remotely access this pc". Next click "Add" in the next tab that opens up type "Domain Users". Once this is all finished simply click okay</h4>
<img src="https://i.imgur.com/QcB6ztB.png">

<h3>Overview:These steps will allow us to login into Client-1 with any non-administrative account that is created. In a general setting, enabling non-adminstrative users to access a client like this one will make organizational tasks that require the use of virtual machines for testing much easier. </h3>


