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

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation files
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>
To begin we will connect to our virtual machine using remote desktop and its pubilc IPv4
  
Your VMs IPv4 can be found in your Azure portal
  
 <img src="https://i.imgur.com/roNfFxZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
<p>
Once you have logged into your VM you need have to enable IIS, which is an abrevation for Internet Information Services

To do so go into control panel and select uninstall a program
  
Under the navigation tree located to the left select "Turn windows features on or off"
  
Once the list populates you will then enable Internet Information Services and selecting okay
</p>  
<img src="https://i.imgur.com/xoexjr5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
</p>
<p>
Next you need to install Web Platform Installer, which can be accessed through the following link https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
  
That link will have have all the applications and extensions you need to get osTicket installed and working porperly. 
</p>
<img src="https://i.imgur.com/Y3wHai2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
Now open Web Installer Platform to add the following MySQL 5.5, PHP 5.6.31, PHP 7.0.33 (x86), PHP 7.1.29 (x86), PHP 7.2.26 (x86) and PHP 7.3.25 (x86)
  
Once you select install you will be prompted by MySQL to enter a passowrd, the password will be "passowrd1".
  
<img src="https://i.imgur.com/TmLzg7h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
</p>
<p>
  
You will notice that 3 files will fail to install but you only need to install 2 out of the 3 which would be the C++ and PHP Manager
  
These files can found in the google drive installations files link.

Below I have attatched an image with the 2 files that you need to download circled. 
<img src="https://i.imgur.com/F661q8T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
  
Next download osTicket. Then extract and copy the "upload" folder into c:\inetpub\wwwroot
  
Afterwards rename the folder to osTicket
</P>
<img src="https://i.imgur.com/qvjxhML.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
<p>
</p>
<p>
Open IIS Manager and under "Manage Server" to the right you want to restart, stop and start the server
 
Then on the left hand side of IIS naviagte to Sites->Default->osTicket on the right, click "Browse*.80"
  
From there your default browser should open osTicket webserver
</p>
<img src="https://i.imgur.com/7fYjD7N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Go back into IIS manager to enable some extensions by going to Sites->Default->osTicket
  
Then double click on PHP manager. Click on "Disable or enable an extension" Enable "php_intl.dll" & "php_opcache.dll" 
  
Refresh the osTicket webserver and you should notice that "Intl Extension" should now be enabled
</p>
<img src="https://i.imgur.com/gmOK5S0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Go back into c:\inetpub\wwwroot\osTicket\include and rename "ost-sampleconfig.php" to "ost-config.php"
  
Assign permissions to ost-config.php by right cicking the file > select Properties >Security >Advanced >Disable inheritance >Remove all inherited permissions from this object
  
Now you want to add new permissions for Everyone allowing full control
</p>
<img src=https://i.imgur.com/zsG65V3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
</p>
<p>
Go back to your browser that has osTicket and click continue
                                                                                              
This will redirect you to a screen where you will name your Helpdesk and add an email that will receive emails from customers who submit tickets. 
</p>
<img src="https://i.imgur.com/YdFg6NP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<p>
Lastly you will need install HeidiSQL in order to fill out the Database portion of the osTicket setup
         
The HeidiSQL file can be found in the installation files link

<img src="https://i.imgur.com/CBnZecV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>                                                                                                 

Open HeidiSQL and select "New" for create a new connection

Username is root and the Password is password1 
                              
Create a new database called "osTicket"
                                       
Now in the osTicket installer fill out the following as such
                                       
MySQL Database: osTicket                                       
MySQL Username: root
MySQL Password: Password1
                                       
Click "Install Now"                                      
<img src="https://i.imgur.com/mRV7b39.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>                                                                                                  

You have now successfully installed osTicket!                                                                                                

In order to keep osTicket runnning smoothly you have to delete some files and set permissions                                                                           
                                                                                                 
Delete: C:\inetpub\wwwroot\osTicket\setup
                                                                                                 
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<img src="https://i.imgur.com/DuGnMMJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>                                                                                                  

