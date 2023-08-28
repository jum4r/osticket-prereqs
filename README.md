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

- PC or Laptop with Internet
- Microsoft Azure Subscription (Creating a new account grants you 200 free credits.)
- Notepad
- <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a> (We'll install these within the VM.)
- Your free time 

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/nybPIAD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Microsoft Azure and create a Virtual Machine (VM). Under "Resource Groups," click "Create New," and name it whatever you please. Choose Windows 10 Pro, and allocate at least 2-4 Virtual CPUs (vCPUs). Create a username and password of your choice, and make a note of these using Notepad or a similar application. Next, under Networking, allow it to create a new Virtual Network (VNet). Proceed to the "Review + Create" section to initiate the VM creation process. Once the deployment is complete, copy the VM's Public IP address and use Remote Desktop (RDP) to connect to it from your personal PC. On your desktop, go to Search, type "rdp," paste the "VM IP address," and then use the login credentials you created earlier.  
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

As soon as it's finished, we can check if IIS is properly installed. Open the browser and type "127.0.0.1"; the page should resemble the image below. If it doesn't appear as shown, we can backtrack and follow the steps above to uninstall and then reinstall IIS.
</p>
<p>
<img src="https://i.imgur.com/bnCEirF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<br />

<p>
<img src="https://i.imgur.com/uaKwINI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we will be downloading and installing all the prerequisites from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a>. Simply download then install these normally

- PHP Manager for IIS
- Rewrite Module
- PHP 7.3.8 (If there's a popup, choose to keep file.) Create a new folder on the C: drive and name it 'PHP.' Extract the contents of PHP version 7.3.8 into the newly created 'C:\PHP' folder.
- VC_redist.x86.exe
- MySQL 5.5.62 (Typical Setup -> Launch Configuration Wizard (after installation) -> Standard Configuration -> Set Password to 'Password1'. No quotes. Make note of MySQL username: root and password: Password1.

Windows Search for IIS and right-click to open it as an administrator. Go to PHP Manager, then click on 'Register PHP.' Point it to 'C:\PHP\php-cgi.exe' and press OK. Go back and click 'Restart' on the right pane under 'Manage Server. 

Download osTicket from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a>, extract the contents, and copy the 'upload' folder to 'c:\inetpub\wwwroot.

Within 'c:\inetpub\wwwroot,' rename the 'upload' folder to 'osTicket.'

Returning to IIS, click on 'Restart,' then navigate to 'Sites' -> 'Default' -> 'osTicket.' On the right pane, click 'Browse *:80,' and it should take you to this page.
<img src="https://i.imgur.com/AddZ5dJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Observe that certain features are currently disabled. Now, let's proceed to enable the remaining ones. Returning to IIS, double-click on PHP Manager and select 'Enable or disable an extension.' Right-click to enable 'php_imap.dll,' 'php_intl.dll,' and 'php_opcache.dll.' Afterward, return to the browser and refresh the page; it should now resemble this.

<img src="https://i.imgur.com/hdj3K8T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename 'ost-sampleconfig' to 'ost-config.php.' Right-click on 'ost-config.php,' go to properties, open the security tab, and then click on 'Advanced.' Click 'Disable inheritance,' which should prompt a popup to appear. Click on 'Remove all inherited permissions from this object.' This should result in empty permission entries.

Next, click on 'Add,' and then select 'Select Principal.' Type 'everyone,' and press 'Check Names,' followed by 'OK.' Afterward, click on 'Full Control.' Proceed to click 'Apply,' and then 'OK,' effectively granting everyone full permissions.
</p>
<br />

<p>
<img src="https://i.imgur.com/ro37fXa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we can proceed with setting up osTicket. Return to the osTicket browser and click 'Continue.' At this point, we simply need to fill in some information. Be sure to jot down these details, either in Notepad or a similar tool. You're free to choose any names to fill in, but if you're feeling a bit bewildered, here are some examples: 

- Helpdesk: Sam Helpdesk
- Default Email: sam@helper.com
- ADMIN USER
- First Name: Sam
- Last Name: Helper
- Email: sam@gmail.com
- Username: sam_admin
- Password: Password1
</p>
<br />

<p>
<img src="https://i.imgur.com/KXlrHGF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before we dive into the Database Settings, there are a couple of tasks to handle first. Begin by downloading and installing HeidiSQL from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a>. After installation, launch HeidiSQL and locate the 'New' button at the bottom left. Fill in the following details: Username: 'root' and Password: 'Password1,' then hit 'OK.' These credentials are the same as the ones we set up earlier for MySQL. 
  
In the left pane of HeidiSQL, right-click on 'Unnamed' and select 'Create New Database.' Name this new creation 'osTicket' and confirm with 'OK.' With this step completed, we can now circle back to osTicket to proceed with filling in the Database Settings.

- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: Password1

Click on 'Install Now,' and once it's finished, you should be greeted with this page.
<img src="https://i.imgur.com/bTlwUOZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/fzs0xez.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We're almost there! Just a few tidying-up tasks before we can dive into osTicket fun. Head to C:\inetpub\wwwroot\osTicket\setup and give that 'setup' folder the boot. Next, navigate to C:\inetpub\wwwroot\osTicket\include\ost-config.php, right-click on 'ost-config.php,' select Properties, then go to Security, and finally click on Advanced. Find 'Everyone,' give it a tap, and hit 'Edit.' Uncheck all the boxes except for 'Read' and 'Read & Execute.' Apply these changes and then click 'OK.

Phew, we've made it through! Now we're finally ready to rock and roll with osTicket.
</p>
<br />

<p>
<img src="https://i.imgur.com/usIB4II.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Also here's the Helpdesk login page: http://localhost/osTicket/scp/login.php. This is the spot where admins work their admin magic.

And for the End Users, the URL is: http://localhost/osTicket/. This is where users can hop on board to create tickets.
</p>
<p>
<img src="https://i.imgur.com/ufoJPOD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
