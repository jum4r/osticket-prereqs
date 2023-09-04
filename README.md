<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- PC or Laptop with Internet
- Microsoft Azure Subscription (A new account grants you 200 free credits.)
- Notepad
- [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) (We'll install these within the VM.)
- Your free time 

<h2>Installation Steps</h2>

### Creating a Free Azure Account
<img width="786" alt="image" src="https://i.imgur.com/h1oEndK.png">

1. Sign up: [Azure Free Account](https://azure.microsoft.com/en-us/free/)
2. Login: [Azure Portal](https://portal.azure.com)

### Creating a Virtual Machine then Enabling Internet Information Services (IIS)

<img width="786" alt="image" src="https://i.imgur.com/CH0z1XB.png">

1. Go to [Azure Portal](https://portal.azure.com)
2. Search for Virtual Machines and create a new Virtual Machine.
3. Configure the VM:
   - Resource Group: RG-osTicket
   - VM Name: vm-osticket
   - Region: East US 2 (or a region closer to you)
   - Virtual Network: Default settings
   - Image: Windows 10 Pro
   - Size: 4 vCPUs
   - Username: azureuser / Password123!
   - Networking: Default settings
4. Create the VM.
5. Once the VM is created, copy the VM's Public IP and ensure you can RDP into it with the provided credentials. 
6. After logging in, install/enable IIS:
   - Control Panel -> Programs -> Turn Windows features on or off
   - Expand IIS -> World Wide Web Services -> Application Development Features
   - Enable CGI
   - Enable Common HTTP Features and all boxes under it
   - Expand IIS -> Web Management Tools -> IIS Management Console
   - Enable IIS Management Console
   - Press OK to install
7. Once IIS is installed, check if it's properly set up.
8. Open a browser, type 127.0.0.1, and it should take you to the IIS landing page.

### Installing the Prerequisites

<img width="886" alt="image" src="https://i.imgur.com/uaKwINI.png">

1. Create a folder named 'PHP' on the C:\ drive
2. From [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) download and install:
   - PHP Manager
   - Rewrite Module
   - PHP 7.3.8, extract the contents to C:\PHP folder
   - VC_redist.x86.exe
3. Install MySQL 5.5.62 with these options:
   - Typical Setup
   - Launch Configuration Wizard (after installation)
   - Standard Configuration
   - Password: Password1
4. Windows Search 'IIS' and run as Administrator, once IIS is open:
   - Go to PHP Manager, click 'Register PHP'
   - Point it to C:\PHP\php-cgi.exe
   - Back in IIS under 'Manage Server' click 'Restart'

### Installing osTicket

<img width="886" alt="image" src="https://i.imgur.com/hdj3K8T.png">

1. In [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) download osTicket.
2. Extract the 'upload' folder to C:\inetpub\wwwroot
3. Rename the 'upload' folder to 'osTicket'
4. Back in IIS window click 'Restart'
5. Navigate to Sites -> Default -> osTicket
6. Click 'Browse *:80' and it will open the osTicket page
7. In IIS, click PHP Manager and select 'Enable or disable an extension'. Right-click and:
   - Enable php_imap.dll
   - Enable php_intl.dll
   - Enable php_opcache.dll
8. Refresh the osTicket page and ensure most features are enabled.
9. Navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename 'ost-sampleconfig' to 'ost-config.php'
10. Right-click 'ost-config.php', select Properties -> Security -> Advanced
11. Click 'Disable inheritance' then 'Remove all inherited permissions from this object'
12. Click on 'Add,' then choose 'Select Principal'
13. Type 'everyone,' and click 'Check Names,' then 'OK'
14. Click 'Full Control' then 'Apply'

### Setting up osTicket

<img width="886" alt="image" src="https://i.imgur.com/ro37fXa.png">

1. In the osTicket browser click 'Continue'
2. Configure osTicket:
   - Helpdesk: Sam Helpdesk
   - Default Email: sam@helper.com
   - First Name: Sam
   - Last Name: Helper
   - Email: sam@gmail.com
   - Username: sam_admin
   - Password: Password1
3. From [Installation Files](https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6) download and install HeidiSQL
4. Launch HeidiSQL, click 'New' and fill in:
   - Username: root
   - Password: Password1
5. Right-click 'Unnamed' amd select 'Create New Database'. Name it 'osTicket'
6. Back in osTicket, continue configuring:
   - MySQL Database: osTicket
   - MySQL Username: root
   - MySQL Password: Password1
7. Install osTicket
  
### Cleanup

<img width="886" alt="image" src="https://i.imgur.com/fzs0xez.png">

1. Head to C:\inetpub\wwwroot\osTicket\setup amd delete 'setup' folder
2. Navigate to C:\inetpub\wwwroot\osTicket\include\ost-config.php
3. Right-click 'ost-config.php', Properties -> Security -> Advanced
4. Find 'everyone' hit 'Edit'
5. Check only 'Read' and 'Read & Execute' boxes. Apply

### Bonus

1. Here's the Helpdesk [Admin Login Page](http://localhost/osTicket/scp/login.php). This is where admins/agents mainly work.
2. This is the [End Users Login Page](http://localhost/osTicket/). This is where users can create tickets.
