<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Creating Users with Powershell, Configuring Group Policy, and Managing Accounts Within Active Directroy in Azure.</h1>
This tutorial will focus on further configuring Active Directory to simulate a real world environment by creating a bulk of users, editing group policies, managing accounts, and observing logs within Event Viewer.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Remote Desktop
- Active Directory
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server
- Windows 10 Pro

<h2>Active Directory Configuration</h2>

<p>
Remote Desktop into the Client VM as our janeadmin account. Right-click Start -> System then under 'Related settings' click Remote Desktop. Now click 'Select users that can remotely access this PC' -> Add -> Type 'Domain Users' -> Check Names -> OK -> OK. <br/>
<img src="https://i.imgur.com/X0ohokt.png" height="80%" width="80%" alt="Allow Remote Desktop"/>
<br />
<br />
Remote Desktop into the DC VM as our janeadmin account. Now, use Windows search to find and open PowerShell ISE as administrator. Start a new script then use CTRL+S to save the file as 'create-users'. <br/>
<img src="https://i.imgur.com/ELeyi42.png" height="80%" width="80%" alt="Save create-users File"/>
<br />
<br />
We will now copy and paste this <a href= https://github.com/joshmadakor1/AD_PS/blob/master/Generate-Names-Create-Users.ps1>script</a> into PowerShell to automate user creation. Click the green play button to begin running the script. We can now observe the users being created in the _EMPLOYEES OU within Active Directory Users and Computers. Take note of one of the random usernames and remember every account has the same password: 'Password1'<br/>
<img src="https://i.imgur.com/XGrZspm.png" height="80%" width="80%" alt="Run User Creation Script and Observe"/>
<br />
<br />
Remote Desktop into the Client VM as the newly created user then open File Explorer -> This PC -> Windows (C:) -> Users and observe the created folder for this user; this will happen for every new user login. Feel free to now close this Remote connection. <br/>
<img src="https://i.imgur.com/5hkjG5S.png" height="80%" width="80%" alt="Login as Newly Created User and Observe C: Drive"/>
<br />
<br />
Remote Desktop into the DC VM and right-click Start -> Run -> type gpmc.msc to open Group Policy Management. <br/>
<img src="https://i.imgur.com/FA49WVm.png" height="80%" width="80%" alt="Open Group Policy Management"/>
<br />
<br />
Expand the dropdown Forest: mydomain.com -> Domains -> mydomain.com then righ-click the Default Domain Policy and edit <br/>
<img src="https://i.imgur.com/NVt7ofm.png" height="80%" width="80%" alt="Edit Domain Policy"/>
<br />
<br />
Expand the dropdown Policies -> Windows Settings -> Security Settings -> Account Policies -> Account Lockout Policy <br/>
<img src="https://i.imgur.com/Axzf8xN.png" height="80%" width="80%" alt="Edit Account Lockout Policy"/>
<br />
<br />
Access the Account lockout threshold set lockout after 5 invalid attempts then click Apply. <br/>
<img src="https://i.imgur.com/T2A3jqb.png" height="80%" width="80%" alt="Add Lockout Threshold"/>
<br />
<br />
Remote Desktop into the Client VM as our admin account then use Windows search to find and open Command Prompt. Run the command 'gpupdate /force' to force the group policy update. Now log out of the Client VM. <br/>
<img src="https://i.imgur.com/MM3GNgz.png" height="80%" width="80%" alt="Force Policy Update"/>
<br />
<br />\
Attempt to login on the Client VM as the random user from earlier with a wrong password 5 times or until the lockout error message appears 
<img src="https://i.imgur.com/BYRWJAQ.png" height="80%" width="80%" alt="Force Account Lockout"/>
<br />
<br />
Now back in the DC VM open Active Directory Users and Computers. Find the locked out employee within _EMPLOYEES and access their Properties -> Account -> Check 'Unlock Account' -> Apply. The user should now be unlocked and able to login with no issues.  <br/>
<img src="https://i.imgur.com/M57JTAW.png" height="80%" width="80%" alt="Unlock User Account"/>
<br />
<br />
Right-click on the user we just unlocked and click 'Disable Account' <br/>
<img src="https://i.imgur.com/CsFNULI.png" height="80%" width="80%" alt="Disable User Account"/>
<img src="https://i.imgur.com/CTbGrdi.png" height="80%" width="80%" alt="Disable User Account Confirmation"/>
<br />
<br />
Try logging into the Client VM with the disabled account credentials and observe the error <br/>
<img src="https://i.imgur.com/pIeP4W2.png" height="80%" width="80%" alt="Observe Login Attempt By Disabled Account"/>
<br />
<br />
Now we will re-enable the account then use it to login to the Client VM.  <br/>
<img src="https://i.imgur.com/us5uBSs.png" height="80%" width="80%" alt="Enable User Account"/>
<br />
<br />
Use Windows search to find and open Event Viewer. Navigate to Windows Logs -> Security. As you can see our non-aministrative user cannot access these logs. <br/>
<img src="https://i.imgur.com/Achx46i.png" height="80%" width="80%" alt="Observe Security Events as Non-admin"/>
<br />
<br />
Close Event Viewer then re-open it this time running as an administrator and using the credentials to our admin user. Navigate back to the Security Logs and observe the failed logins from earlier. <br/>
<img src="https://i.imgur.com/8O14XAM.png" height="80%" width="80%" alt="Login to Event Viewer as Admin"/>
<img src="https://i.imgur.com/zmRxb92.png" height="80%" width="80%" alt="Observe Failed Login Attempts"/>
<br />
