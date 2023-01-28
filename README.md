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
<img src="https://i.imgur.com/u0JWmoq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
These are the 2 VM's that I used for this project. CLient-1 and DC(Domain Controlloer) 1. Now I will login in the CLient-1 VM with the RDP. 
</p>
<br />

<p>
<img src="https://i.imgur.com/4OUb7yS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I have to make sure the IP address won't change so I went into DC-1 VM connected it to the DNS server, so I made it static.
</p>
<br />

<p>
<img src="https://i.imgur.com/u9WqV0Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I am configuring the connectivity between Client 1and DC-1 to see if the connection works but pinging DC-1 DNS server. As you see it doesn’t connect. Therefore, I login into the DC-1 controller and gave access to Client by going into the firewall and enabling ICMP.
</p>
<br />

<p>
<img src="https://i.imgur.com/jVElZWx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is me configuring ICMP through the DC-1 firewall.
</p>
<br />

<p>
<img src="https://i.imgur.com/IjkmuBb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now once I try again, the ping is able to reach the other virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/l9LygcA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I installed active direcrtoy through the DC-1 VM by going into the server manager and click on add roles and this is how you would install active directory since you would have to choose Active Domain Services.
</p>
<br />

<p>
<img src="https://i.imgur.com/1sJ5uEv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
<img src="https://i.imgur.com/cz5aEym.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is how I would configure the users access and accouunt information.
</p>
<br />

<p>
<img src="https://i.imgur.com/iafISUv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is me adding the user to the proper domain group.
</p>
<br />

<p>
<img src="https://i.imgur.com/ygsL6tU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I logged into Client-1 to rename the PC so that all users on the DC-1 VM could log into it but I got an error because the DNS needs to be changed. So I neede to go back on Azure to change it manually. 
</p>
<br />

<p>
<img src="https://i.imgur.com/ezvM7fH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I have to make sure the IP address won't change so I went into Client-1 VM connected it to the DNS server. 
</p>
<br />

<p>
<img src="https://i.imgur.com/KssNRCW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once you get done manually doing everything on Azure, I logged back in to CLient-1 once more and it should work.
</p>
<br />

<p>
<img src="https://i.imgur.com/amD7AJM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This would be how to confirm that the DC-1 computer users should be able to connect to the Client-1 computer.
</p>
<br />

<p>
<img src="https://i.imgur.com/xUXGnX6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now I will be creating multiple users at once with a script for powershell ISE.
</p>
<br />

<p>
<img src="https://i.imgur.com/l8ohi03.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is the script and it will make 10,000 users, generate different names and it will make them all have the same Password.
</p>
<br />

<p>
<img src="https://i.imgur.com/KMi8sRg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
These are the different users that was created.
</p>
<br />

<p>
<img src="https://i.imgur.com/Ekb4E45.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is me testing to see if I can log into Client-1 with one of these accounts.
</p>
<br />

<p>
<img src="https://i.imgur.com/5W1I9tm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
As we can see, it was a success.
</p>
<br />
