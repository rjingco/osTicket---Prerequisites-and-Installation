<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

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

Congratulations, hopefully it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:
http://localhost/osTicket/ 

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php


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
We will use the files in this folder to install osTicket and some of the dependencies. <p>
You can access the osTicket Installation Files.zip by pasting (https://docs.google.com/document/d/1DyjX8LeVU98LjhXO2t2K2F0aHywI2N9GD57T3taO5qo/edit?tab=t.0) in Microsoft Edge. 
<img width="1578" height="674" alt="image" src="https://github.com/user-attachments/assets/667ff472-29e3-4e0a-b597-4a3202b57ad5" />
<img width="1041" height="555" alt="image" src="https://github.com/user-attachments/assets/7f529a41-2985-4943-8bfe-34d20b736379" />
<hr style="width:100%;">

Install / Enable IIS in Windows WITH CGI<p>
World Wide Web Services -> Application Development Features -> [X] CGI<p>
Access Control Panel > Panel > Panels and Features <p>
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
Username: root
Password: root

<img width="1012" height="850" alt="image" src="https://github.com/user-attachments/assets/db46052a-e26e-4938-b119-4e6a109f9c1a" />
<img width="738" height="614" alt="image" src="https://github.com/user-attachments/assets/9a26fd12-7f1e-4577-abc8-97ceb70111e7" />
<hr style="width:100%;">
