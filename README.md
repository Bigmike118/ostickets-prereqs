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

- PHP Manager for IIS
- Properly Downloading Files and Programs for osTicket
- Creating a new Directory within C://
- Configuration within osTicket

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/N7cw62H.png"/>
</p>
<p>
In this scenario, a Virtual Machine (VM) in Azure is used. The idea of using a VM for this is for the safe environment it provides for testing products. The user will then log into the device via Remote Desktop. Once logged into the VM, the user will install/enable IIS in Windows with CGI.
  
Start Menu -> Control Panel -> Programs and Features -> Turn Windows Features on or off -> World Wide Web Services -> Application Development Features -> "Checkmark" CGI
</p>
<br />

<p>
<img src="https://i.imgur.com/rD0uUF9.png"/>
</p>
<p>
After enabling the IIS Web Server, osTicket files and dependencies have to be installed onto the VM.
  
**(The following files and dependencies throughout this tutorial were found on the osTicket documentation website and aggregated to a zip file for convienance. Finding and collecting these files are outside the scope of this basic tutorial)**

  - PHP Manager (PHPManagerForIIS_V1.5.0.msi)
  - Rewrite Module (rewrite_amd64_en-US.msi)
</p>
<br />

<p>
<img src="https://i.imgur.com/4AOM2i9.png"/>
</p>
<p>
Next, a new directory on the "C" Drive will be created. The new directory will be named "C://PHP".
</p>
<br />

<p>
<img src="https://i.imgur.com/jIozeXb.png"/>
<img src="https://i.imgur.com/eFJ87wm.png"/>
<img src="https://i.imgur.com/ARGjAUT.png"/>
</p>
<p>
After C://PHP is created, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder. After, install VC_redist.x86.exe and MySQL 5.5.62

- Typical Setup ->
- Launch Configuration Wizard (after install) ->
- Standard Configuration ->
- Username: root
- Password: root
</p>
<br />

<p>
<img src="https://i.imgur.com/4IBa55u.png"/>

<img src=https://i.imgur.com/uKjEtID.png/>
</p> 
<p>
Open IIS as an Admin and register PHP via PHP Manager icon. the path chosen will be C:\PHP\php-cgi.exe
  
Reload IIS (On the right hand side in IIS, press Stop and then Start the server)
</p>
<br />

<p>
<img src="https://i.imgur.com/TASYm9v.png"/>
</p>
<p>
Next, install osTicket v1.15.8
  
Unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”

Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”

Reload IIS (Open IIS, Stop and Start the server)

<img src="https://i.imgur.com/AlgiiJ6.png"/>

Go to sites -> Default -> osTicket

On the right, click “Browse *:80”

<img src="https://i.imgur.com/Q6EVXPm.png"/>

Note that some extensions are not enabled

<img src="https://i.imgur.com/U475NJn.png"/>

Go back to IIS, sites -> Default -> osTicket. Double-click PHP Manager, and click “Enable or disable an extension”
- Enable: php_imap.dll
- Enable: php_intl.dll
- Enable: php_opcache.dll

<img src="https://i.imgur.com/Wr9WIAb.png"/>

Refresh the osTicket site in your browser, observe the changes

</p>
<br />

<p>

</p>
<p>
Rename: ost-config.php
  
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php

To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

<img src="https://i.imgur.com/yu1n0jk.png"/>
<img src="https://i.imgur.com/5mq84hO.png"/>

Assign Permissions: ost-config.php

Disable inheritance -> Remove All

<img src="https://i.imgur.com/N2PjSxz.png"/>

New Permissions -> Everyone -> All

</p>
<br />

<p>

</p>
<p>
Continue Setting up osTicket in the browser (click Continue)
  
Name it "Helpdesk"

Default email (receives email from customers).

From the “osTicket-Installation-Files” folder, install HeidiSQL.
- Open Heidi SQL
- Create a new session, root/root
- Connect to the session
- Create a database called “osTicket”

Continue Setting up osTicket in the browser
- MySQL Database: osTicket
- MySQL Username: root
- MySQL Password: root
- Click “Install Now!”

</p>
<br />

<p>
</p>
<p>
Congratulations, hopefully it is installed with no errors!
  
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

End Users osTicket URL:

http://localhost/osTicket/ 
</p>
<br />
