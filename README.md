
<p align="center">
<img src="https://i.imgur.com/EBAA5E3.jpg" height="50%" width="50%" alt="DNS logo"/>
</p>

<h1>Building Intuition for DNS</h1>
This lab will help us understand the use of DNS and give a good knowledge about DNS functionality.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10/Server 2022</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Tutorial Steps</h2>
<p>
</p>
<p>
We will initially examine the server's DNS A-Records. Hostname to IP address mappings are stored in an A record. On DC-1, an A record for "mainframe" will be set up, pointing to DC-1's private IP address. Without creating the DNS record, pinging the mainframe will not be successful. Client-1 checks the DNS cache, its local host file, and the DNS server when we ping "mainframe." Go to AD->Tools->DNS->DC-1->Forward lookup zones->mydomain.com and right click to create a new A record with the name mainframe.  Hostname to IP address mapping is known as an A record. We will receive a response if we return to the client machine and ping the mainframe.
</p>
<br />


<p>
<img src="https://i.imgur.com/q5Zk8hE.png" height="80%" width="80%" alt="Creating an A record"/>  
  
<img src="https://i.imgur.com/pR5kPLF.png" height="80%" width="80%" alt="Creating an A record"/>
<img src="https://i.imgur.com/WuhAQzQ.png" height="80%" width="80%" alt="Creating an A record"/>
<img src="https://i.imgur.com/pNPRR0A.png" height="80%" width="80%" alt="Creating an A record"/> 
</p>

<p>


</p>
<img src="https://i.imgur.com/HDMDNVl.png" height="80%" width="80%" alt="Ping mainframe"/>
<p>

<p>
As soon as we switch the record address of "mainframe" to 8.8.8.8, the client machine will continue to ping the previous address even if we changed it. Why? Because we need to flsuh the dns before it can show the new IP Address, to do so use the command ipconfig /flushdns which will flush the DNS. The DNS cache will be cleared, and the new record's address will appear when we try to ping the mainframe again.
  
</p>
<p>
<img src="https://i.imgur.com/tIgsNxy.png" height="80%" width="80%" alt="Changing mainframe IP Address"/>
</p>
<img src="https://i.imgur.com/H7oEZY8.png" height="80%" width="80%" alt="Ping mainframe again"/>
<p>

<p>
Last but not least, we'll set up a CNAME record to direct the host "search" to "www.google.com." Ping won't be able to locate the host if we use the "search" option. To construct the CNAME record "search," we must return to the DNS tool on DC-1. When we ping "search" after creating the CNAME record, it resolves to www.google.com.
  
</p>
<p>
<img src="https://i.imgur.com/P0i6zi7.png" height="80%" width="80%" alt="Creating a CNAME  
<img src="https://i.imgur.com/fDJl47K.png" height="80%" width="80%" alt="Creating a CNAME"/>
</p>
<p>
<img src="https://i.imgur.com/KEdUGck.png" height="80%" width="80%" alt="search CNAME record 
<p>  


<p>
<img src="https://i.imgur.com/KEdUGck.png" height="80%" width="80%" alt="search CNAME record"/>
</p>
<p>
<img src="https://i.imgur.com/oQe0ZI0.png" height="80%" width="80%" alt="Ping search"/>
</p>




  
