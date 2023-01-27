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

- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Cient-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/wyQGdkd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
These are the 2 VM's that I used for this project. CLient-1 and DC(Domain Controlloer) 1. Now I will login in the CLient-1 VM with the RDP. 
</p>
<br />

<p>
<img src="https://i.imgur.com/HXPMZyD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I am configuring the connectivity between Client 1and DC-1 to see if the connection works but pinging DC-1 DNS server. As you see it doesn’t connect. Therefore, I login into the DC-1 controller and gave access to Client by going into the firewall and enabling ICMP.
</p>
<br />

<p>
<img src="https://i.imgur.com/tWJxIOW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now once I try again, the ping is able to reach the other virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/0UzWPHj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I installed active direcrtoy through the DC-1 VM by going into the server manager and click on add roles and this is how you would install active directory since you would have to choose Active Domain Services.
</p>
<br />

<p>
<img src="https://i.imgur.com/A5uls5v.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After you install it the first time, you will have to finally you have to do the deloymwnt configurations for it to work properly.
</p>
<br />

<p>
<img src="https://i.imgur.com/BqIG3KD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After Active Directoy is installed completely, you would go to Active Directory Users and Computers to get started.
</p>
<br />

<p>
<img src="https://i.imgur.com/PeLUPg7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is where you would configure different organizational groups, like for example I created the _EMPLOYEES and _ADMIN groups and with them I can create different users that can have access to certain things if needed. 
</p>
<br />

<p>
<img src="https://i.imgur.com/mx6S4Vy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is me configuring a new users under a OU(Organizational Unit).
</p>
<br />

<p>
<img src=" https://i.imgur.com/cz5aEym.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is how I would configure the users access and accouunt information.
</p>
<br />

<p>
<img src="https://i.imgur.com/iafISUv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
g
</p>
<br />

<p>
<img src="blob:https://imgur.com/7a9e39b0-c615-4514-9b62-b10353fadb13" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next I had to confiure that the both computers was to connect to each others domain service for other accounts can use it.  
</p>
<br />

<p>
<img src="https://i.imgur.com/rjY7YIK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This would be how to confirm that the DC-1 computer users should be able to connecet to the Client-1 computer. 
</p>
<br />

<p>
<img src="https://i.imgur.com/wquwVGb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I will be creating multiple users at once with a script for powershell ISE.
</p>
<br />

<p>
<img src="https://i.imgur.com/UYsmGvw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is the script and it will make 1000 users, generate differents names and it will make them all have the same Password.
</p>
<br />

<p>
<img src="https://i.imgur.com/YyO8PhT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
These are the different users that was cretaed.
</p>
<br />

<p>
<img src="https://i.imgur.com/26B6OTD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is me testing to see if i can log into Client-1 with one of these accounts
</p>
<br />

<p>
<img src="https://i.imgur.com/cqMQ2JZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
As we can see, it was a sucess. 
</p>
<br />
