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
<img src="https://i.imgur.com/X0ohokt.png" height="80%" width="80%" alt="Allow Remote Desktop"/>
<br />
<br />
<img src="https://i.imgur.com/ELeyi42.png" height="80%" width="80%" alt="Save create-users File"/>
<br />
<br />
<img src="https://i.imgur.com/XGrZspm.png" height="80%" width="80%" alt="Run User Creation Script and Observe"/>
<br />
<br />
<img src="https://i.imgur.com/5hkjG5S.png" height="80%" width="80%" alt="Login as Newly Created User and Observe C: Drive"/>
<br />
<br />
<img src="https://i.imgur.com/FA49WVm.png" height="80%" width="80%" alt="Open Group Policy Management"/>
<br />
<br />
<img src="https://i.imgur.com/NVt7ofm.png" height="80%" width="80%" alt="Edit Domain Policy"/>
<br />
<br />
<img src="https://i.imgur.com/Axzf8xN.png" height="80%" width="80%" alt="Edit Account Lockout Policy"/>
<br />
<br />
<img src="https://i.imgur.com/T2A3jqb.png" height="80%" width="80%" alt="Add Lockout Threshold"/>
<br />
<br />
<img src="https://i.imgur.com/MM3GNgz.png" height="80%" width="80%" alt="Force Policy Update"/>
<br />
<br />
<img src="https://i.imgur.com/BYRWJAQ.png" height="80%" width="80%" alt="Force Account Lockout"/>
<br />
<br />
<img src="https://i.imgur.com/M57JTAW.png" height="80%" width="80%" alt="Unlock User Account"/>
<br />
<br />
<img src="https://i.imgur.com/CsFNULI.png" height="80%" width="80%" alt="Disable User Account"/>
<br />
<br />
<img src="https://i.imgur.com/CTbGrdi.png" height="80%" width="80%" alt="Disable User Account Confirmation"/>
<br />
<br />
<img src="https://i.imgur.com/pIeP4W2.png" height="80%" width="80%" alt="Observe Login Attempt By Disabled Account"/>
<br />
<br />
<img src="https://i.imgur.com/us5uBSs.png" height="80%" width="80%" alt="Enable User Account"/>
<br />
<br />
  <img src="https://i.imgur.com/Achx46i.png" height="80%" width="80%" alt="Observe Security Events as Non-admin"/>
<br />
<br />
<img src="https://i.imgur.com/8O14XAM.png" height="80%" width="80%" alt="Login to Event Viewer as Admin"/>
<br />
<br />
<img src="https://i.imgur.com/zmRxb92.png" height="80%" width="80%" alt="Observe Failed Login Attempts"/>
<br />
