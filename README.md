<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- Item 1
- Item 2
- Item 3
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/nybPIAD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Microsoft Azure and create a Virtual Machine (VM). Choose Windows 10 Pro, and allocate at least 2-4 Virtual CPUs (vCPUs). Create a username and password of your choice, and make a note of them. Next, under Networking, allow it to create a new Virtual Network (VNet). Proceed to the "Review + Create" section to initiate the VM creation process. Once the deployment is complete, copy the VM's Public IP address and use Remote Desktop (RDP) to connect to it from your personal PC. On your desktop, go to Search, type "rdp," paste the "VM IP address," and then use the login credentials you created earlier.  
</p>
<br />

<p>
<img src="https://i.imgur.com/DmMgZbU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once we access our VM through Remote Desktop (RDP), we need to install and enable Internet Information Services (IIS) along with CGI, Common HTTP Features, and the IIS Management Console. IIS serves as the web server for osTicket, making this a necessary step. To begin, access the Control Panel by navigating to Search -> type "control panel" -> Programs -> Turn Windows features on or off. Scroll down and expand the Internet Information Services section, then enable the following:

- World Wide Web Services -> Application Development Features ->

  [X] CGI
 
  [X] Common HTTP Features(expand and ensure that all boxes under this category are checked.)

- Internet Information Services -> Web Management Tools -> IIS Management Console

  [X] IIS Management Console

As soon as it's finished, we can check if IIS is properly installed. Open the browser and type "127.0.0.1"; the page should resemble the image below. If it doesn't appear as shown, we can backtrack and follow the steps above to uninstall and then reinstall.
</p>
<p>
<img src="https://i.imgur.com/bnCEirF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<br />

<p>
<img src="https://i.imgur.com/uaKwINI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we will be downloading and installing all the prerequisites from the Google Drive Installation Files. Open the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a>, download, and install:

- PHP Manager for IIS

- Rewrite Module

- PHP 7.3.8 (If there's a popup, choose to keep file.)

- VC_redist.x86.exe

- MySQL 5.5.62 (Typical Setup -> Launch Configuration Wizard (after installation) -> Standard Configuration -> Set Password to 'Password1'. No quotes.

Search IIS and right-click to open as Admin. Go to PHP Manager then click "Register PHP". Click "Restart" on the right-pane. Download osTicket from <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a> and extract and copy “upload” folder to c:\inetpub\wwwroot. Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”. Back in IIS click "Restart" 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
