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
- Setting up security rules for login attempts
- Enabling and disabling accounts
- Observing logs

<h2>Setup Remote Desktop for non-administrative users on Client-1</h2>
<h4>Log into the Client-1 virtual machine through remote desktop</h4>
<img src="https://i.imgur.com/3zL5Gnm.png">

<h4>Within the Client-1 virtual machine, right click Windows start and click "Systems" for systems properties. In the open tab click "Remote"</h4>
<img src="https://i.imgur.com/mU87RXd.png">

<h4>Scroll down in the remote desktop tab and click "Select users that can remotely access this pc". Next click "Add" in the next tab that opens up type "Domain Users". Once this is all finished simply click okay</h4>
<img src="https://i.imgur.com/QcB6ztB.png">

<h4>Overview: These steps will allow us to login into Client-1 with any non-administrative account that is created. In a general setting, enabling non-adminstrative users to access a client like this one will make organizational tasks that require the use of virtual machines for testing much easier. </h4>



<h2>Creating additional users through the domain controller and using the accounts to login</h2>
<h4>Sign into Domain Controller virtual machine.</h4>
<img src="https://i.imgur.com/oCcMxaZ.png">

<h4>In the Windows desktop search bar type "Windows Powershell ISE". Then right click the application and open it as an administrator.</h4>
<img src="https://i.imgur.com/86QYpMB.png">

<img src="https://i.imgur.com/A1j7Fdd.png">

<h4></h4>
<img src="https://i.imgur.com/ChCpV3M.png">

<h4>Paste a script that automatically creates accounts</h4>
<img src="https://i.imgur.com/6tAp6eU.png">

<h4>Click start above and observe the creation of the non-adminstrative accounts. (In this script we used$PASSWORD_FOR_USERS  = "Password1" to automatically assign each account with the same password.)</h4>
<img src="https://i.imgur.com/XpGdK8Y.png">

<h4>Select an account that has been automatically generated and use the credentials to log into our Client-1 virtual machine.</h4>
<img src="https://i.imgur.com/NSLJvQR.png">
<img src="https://i.imgur.com/JEmOVMZ.png">
<img src="https://i.imgur.com/44lK1LF.png">
<h3>Overview: We have successfully completed the administrative role of creating accounts and testing it's functionality by logging in. From this point we can expand our tasks and go as far as enforcing security features</h3>

<h2>Group Policy and Managing accounts</h2>
<h4>Configure Group Policy to lock out account after 5 attempts</h4>
<h4>
  Open the following 
  Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy
  Double click "Account Lockout Policy" and type 5 minutes so account will be locked out after several failed attempts
</h4>

<img src="https://i.imgur.com/G1SAg4g.png">
<img src="https://i.imgur.com/smMDH3V.png">
<h4>Put the wrong password in for Client-1 and purposely lock yourself out to test the security rule. Then go into the domain controller and observe that the account is locked in "Active Directory Users and Computers". (The unchecked box indicates the account has been locked.)</h4>
<img src="https://i.imgur.com/y80T4cE.png">
<img src="https://i.imgur.com/ir8knbg.png">

<h4>Click the unchecked box to reset the security rule</h4>
<img src="https://i.imgur.com/pkvhXbm.png">

<h4>We also have the option to reset the password for the user. We can simply do this by clicking the username we are using within "Active Directory Users and Computers"</h4>
<img src="https://i.imgur.com/gztauRX.png">
<img src="https://i.imgur.com/xaZHsdL.png">
<h4>Log into Client-1 to make sure that the account has successfully been enabled for login.</h4>
<img src="https://i.imgur.com/IxXnLZI.png">
<img src="https://i.imgur.com/q8dVRCQ.png">

<h2>View account security logs</h2>
<h4>In the search bar search "eventvwr.msc (This will be done in Client-1 but will be granted admin access to view logs)</h4>
<img src="https://i.imgur.com/sgeYIMO.png">
<h4>Login with our administrative account</h4>
<img src="https://i.imgur.com/OvutfAv.png">
<h4>Click "Windows Logs" and then "Click Security" to view the accounts behavior.
    Below we can examine a list of 5 failed login attempts indicated by the lock icon within the red box</h2>
<img src="https://i.imgur.com/Df1RopB.png">

<h2>File Permissions</h2>
