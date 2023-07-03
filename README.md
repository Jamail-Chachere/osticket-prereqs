<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### 
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>



<h2>Installation Steps</h2>

<p>
<img src="https://imgur.com/a/gdhlZ1U.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<img src=https://i.imgur.com/sA5R5o5.png>



  - Create a Resource Group in Azure
- Create an Azure Virtual Machine Windows 10. With 4 vCPUs
-Name: *choose your VM name*
-Username: *choose your username
-Password: *choose your password* 
<p>


  
<img src=https://i.imgur.com/yT3Dhv8.png>


<p>
Install / Enable IIS in Windows WITH
CGI and Common HTTP Features
Folder path: Internet Information Services -> World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
AND IIS Management Console
Folder path: Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console
</p>
<br />

<p>
<img src="https://i.imgur.com/yqAOOaC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
download and install the Rewrite Module (rewrite_amd64_en-US.msi)

</p>
<br />
Create the directory C:\PHP
<p>

</p>
<p>
download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP
</p>
<br />
download and install VC_redist.x86.exe.
</p>
<br />
download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
-Typical Setup ->
-Launch Configuration Wizard (after install) ->
-Standard Configuration ->
-*choose your password* 

</p>
<br />
Open IIS as an Admin
</p>
<br />
<img src="https://i.imgur.com/VR31cN2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Register PHP from within IIS
</p>
<br />
Reload IIS (Open IIS, Stop and Start the server)
</p>
<br />
Install osTicket v1.15.8
Extract and copy “upload” folder to c:\inetpub\wwwroot
Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
</p>
<br />

Reload IIS (Open IIS, Stop and Start the server)
</p>
<br />
Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
</p>
<br />
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes

</p>
<br />
Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

</p>
<br />
Right click on ost-config.php, Properties -> Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

</p>
<br />
Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

</p>
<br />
From the Installation Files, download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/*insert password*
Connect to the session
Create a database called “osTicket”
</p>
<br />
Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”
</p>
<br />
Everything is configured correctly now!
</p>
<br />
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

Clean up these files:
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
