<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<p>
  
osTicket is an open-source support ticket system used for managing customer service, IT help desk, and technical support requests.<p>
osTicket lets organizations handle incoming support requests from multiple channels — like email, web forms, and phone — and converts them into trackable tickets in one centralized dashboard.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>osTicket Setup Checklist</h2>
Create an Azure Virtual Machine Windows 10, 4 vCPUs
Name: osticket-vm
Username: labuser
Password: osTicketPassword1!

Log into the VM with Remote Desktop

Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
We will use the files in this folder to install osTicket and some of the dependencies.

Install / Enable IIS in Windows WITH CGI
World Wide Web Services -> Application Development Features -> [X] CGI

From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)

Create the directory C:\PHP

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root
Password: root

Open IIS as an Admin

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”

Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”

Congratulations on installing osTicket!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php


<h2>Installation Steps</h2>

Create an Azure Virtual Machine Windows 10, 4 vCPUs Name: osticket-vm Username: labuser Password: osTicketPassword1!

<p><img width="1458" height="762" alt="image" src="https://github.com/user-attachments/assets/b406b3b6-e5e9-4f86-8cff-57195790a8f3" />
<hr style="width:100%;">
  
Select Image: Windows 10 Enterprise, Size: Standard 2 VCPUS
<img width="1433" height="835" alt="image" src="https://github.com/user-attachments/assets/ed666d58-116a-4cb6-8ae3-d0d73a915423" />
<hr style="width:100%;"></p>

Name: osticket-vm <p>
Username: labuser <p>
Password: osTicketPassword1!<p>
Don't forget to check the licensing agreement! <p></p>
Select next on Networking and Create. 

<img width="983" height="837" alt="image" src="https://github.com/user-attachments/assets/b9373084-5da8-43c1-a349-d4bf91a8ab5f" />
<hr style="width:100%;">

New virtual machine is created!

<img width="1439" height="676" alt="image" src="https://github.com/user-attachments/assets/625f7df3-c277-4e7b-b923-79666f32ef19" />
<hr style="width:100%;">

To connect to your virtual machine, "Download RDP File".

<img width="1532" height="805" alt="image" src="https://github.com/user-attachments/assets/c6b1f919-f36a-419a-b322-092f7e1cd39f" />
<hr style="width:100%;">

Remote Desktop Connect to your virtual machine by selecting the downloaded "osticket-vm" file.

<img width="1015" height="288" alt="image" src="https://github.com/user-attachments/assets/65701e42-8912-47fb-8a15-00580beddff5" />
<img width="572" height="498" alt="image" src="https://github.com/user-attachments/assets/598a3d18-2b07-4603-a128-01f1c4c13732" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c74033e9-0b70-46db-a0af-76506e470099" />
<hr style="width:100%;">

Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”
You can access the osTicket Installation Files.zip by pasting (https://docs.google.com/document/d/1DyjX8LeVU98LjhXO2t2K2F0aHywI2N9GD57T3taO5qo/edit?tab=t.0) in Microsoft Edge. 

<img width="1578" height="674" alt="image" src="https://github.com/user-attachments/assets/667ff472-29e3-4e0a-b597-4a3202b57ad5" />
<img width="1041" height="555" alt="image" src="https://github.com/user-attachments/assets/7f529a41-2985-4943-8bfe-34d20b736379" />
<hr style="width:100%;">

Install / Enable IIS in Windows WITH CGI<p>
World Wide Web Services -> Application Development Features -> [X] CGI<p>
Select IIS (Internet Information Service)  and CGI under (Worldwide Web Services > Application Development Features)

<img width="648" height="590" alt="image" src="https://github.com/user-attachments/assets/68ef48af-b3d4-42f2-b37c-59ad7f2620de" />
<hr style="width:100%;">

From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

<img width="876" height="602" alt="image" src="https://github.com/user-attachments/assets/400e2d9c-c13b-4784-a751-813cba2e8ae7" />
<hr style="width:100%;">

From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
<img width="892" height="674" alt="image" src="https://github.com/user-attachments/assets/a8a855c0-6cf6-402e-8663-f9902465f155" />
<hr style="width:100%;">

Create the directory C:\PHP<p>
Access the (C:) Drive under (File Explorer > This PC) and create a new folder titled "PHP"

<img width="1176" height="524" alt="image" src="https://github.com/user-attachments/assets/fb8dc028-cc95-4771-bee3-ea9a58b04630" />
<hr style="width:100%;">

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder

<img width="1512" height="938" alt="image" src="https://github.com/user-attachments/assets/ab528491-802d-4e68-a5ff-d80cceaafdb6" />
<hr style="width:100%;">

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

<img width="1104" height="776" alt="image" src="https://github.com/user-attachments/assets/c36abac2-7ad7-45c4-8732-330fc524f438" />
<hr style="width:100%;">

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
<b>Username: root
Password: root</b>

<img width="1012" height="850" alt="image" src="https://github.com/user-attachments/assets/db46052a-e26e-4938-b119-4e6a109f9c1a" />
<img width="738" height="614" alt="image" src="https://github.com/user-attachments/assets/9a26fd12-7f1e-4577-abc8-97ceb70111e7" />
<hr style="width:100%;">

Open IIS as an Admin<p>
Type IIS in the start menu and select "Run as Admin"

<img width="1040" height="753" alt="image" src="https://github.com/user-attachments/assets/c56876e8-290a-4e55-8c5e-5b194d36df5d" />
<hr style="width:100%;">

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)

<img width="1161" height="808" alt="image" src="https://github.com/user-attachments/assets/fb945658-2f79-4542-a314-24e2c0219c09" />
<hr style="width:100%;">

Reload IIS (Open IIS, Stop and Start the server)<p>
Select "Stop" and then "Start" to restart the server

<img width="1474" height="550" alt="image" src="https://github.com/user-attachments/assets/772df6b9-bd65-4a74-961b-8bb2f8126b0e" />
<hr style="width:100%;">

Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

<img width="1456" height="924" alt="image" src="https://github.com/user-attachments/assets/041aead1-d659-4640-bec6-a3a6966dd229" />
<hr style="width:100%;">

Reload IIS (Open IIS, Stop and Start the server)

<img width="1465" height="791" alt="image" src="https://github.com/user-attachments/assets/7f63821e-4e04-41ee-887a-620aced5cbd4" />
<hr style="width:100%;">

Go to sites -> Default -> osTicket
On the right, click “Browse *:80”

<img width="781" height="779" alt="image" src="https://github.com/user-attachments/assets/535a872c-c1c2-4061-bb68-3e5cc84ec06c" />
<hr style="width:100%;">

Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes

<img width="843" height="736" alt="image" src="https://github.com/user-attachments/assets/a42549f6-7dee-4e41-99f1-04ac0bfd3855"/>
<hr style="width:100%;">

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<img width="650" height="604" alt="image" src="https://github.com/user-attachments/assets/edaf8fbd-0b98-4603-8589-75fdf1b9ba3e" />
<hr style="width:100%;">

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

<img width="712" height="483" alt="image" src="https://github.com/user-attachments/assets/6858e7c8-b04b-4d08-82aa-4c6d0e6a0400" />>
<hr style="width:100%;">

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

<img width="817" height="829" alt="image" src="https://github.com/user-attachments/assets/40d14f65-2504-4677-802c-d86d899b5f2c" />
<hr style="width:100%;">

From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”

<img width="935" height="437" alt="image" src="https://github.com/user-attachments/assets/b466a4d3-00f6-428b-b247-cf3c1e0b0edb" />
<img width="666" height="475" alt="image" src="https://github.com/user-attachments/assets/37d28ded-96d2-4531-a822-5a2baa0bd96d" />
<img width="849" height="515" alt="image" src="https://github.com/user-attachments/assets/b5208fd6-214c-4253-9512-27f36e009648" />
<hr style="width:100%;">

Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”

<img width="548" height="351" alt="image" src="https://github.com/user-attachments/assets/9b8fa3ed-1f17-469d-b0d4-c9fb99babe21" />
<hr style="width:100%;">

<img width="830" height="698" alt="image" src="https://github.com/user-attachments/assets/3fa29414-39c3-41fc-aa6d-0a37a650d257" />

