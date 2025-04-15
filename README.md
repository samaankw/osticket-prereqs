# osticket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)





<h2> Installation Steps</h2>



<h2> Step: 1 Connect to Your Machine with Remote Desktop</h2> 
</p> If you need help connecting to your virutal machine please watch my tutorial</p>

<p>
  <h2> Step 2: Install and Enable Internet Information Services (IIS) in Window </h2>
  <img src="https://i.imgur.com/i9bIcLO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Open the Start menu and search for Control Panel. Once in the Control Panel, click on Uninstall a Program under the "Programs" section. Then, on the left-hand side, select Turn Windows features on or off. In the list that appears, locate and check the box for Internet Information Services (IIS) to enable it, then click OK to apply the changes.</p>
<br />

<h2> Step 3: Download, Install, and Open the Web Platform Installer</h2>
<p>
  
</p>

<p> Installing osTicket via Web Platform Installer

  Go to the osTicket Installation Files page and click on Download Web Platform Installer. If you're prompted with a warning or confirmation, select Download Anyway to proceed.

Once the download is complete, click Open File from the top-right corner of your browser to begin the installation. Follow the on-screen prompts to complete the setup of the Web Platform Installer.

After the installation finishes, go ahead and launch the Web Platform Installer to begin setting up the components needed for osTicket.

 <img src="https://i.imgur.com/zOacQEI.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once the Web Platform Installer is open, go to the top-right corner and search for MySQL 5.5. Locate MySQL Windows 5.5 in the results and click Add. Next, search for PHP in the same search bar, then adjust the list to sort by name. Add all the simple x86 versions of PHP up to version 7.3 from the sorted list. After selecting all the required components, click Install at the bottom of the screen. During installation, you’ll be prompted to create a username and password to complete the setup.
</p>
<br />



<img src="https://i.imgur.com/chIwF6F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/5G6lK61.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
When prompted during the installation, set the username as root and the password as Password1, then follow the on-screen instructions to complete the process. If you receive a message saying that “some products have failed to install,” you can safely ignore it—just click Finish to proceed. Next, download and install the following required components from the provided lab files: PHP version 7.3.8, PHP Manager 1.5.0 for IIS 10, and the Microsoft Visual C++ 2009 Redistributable Package. These installations are essential for ensuring that osTicket runs smoothly on your system.</p>


<img src="https://i.imgur.com/f5ndQ4O.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/9Hh5h2L.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

<h2> Step 4: Install osTicket v1.15.8</h2>
<p>To begin the installation process, first download the osTicket file provided in the lab files. Once the download is complete, right-click on the file and select "Extract All" to unzip its contents. After extraction, open the newly created osTicket folder. Inside, you'll find a folder named "Upload". Copy this Upload folder and paste it into the following directory: C:\inetpub\wwwroot. Once the folder is in place, rename "Upload" to "osTicket" to keep things organized and to ensure proper configuration during setup</p>

<img src="https://i.imgur.com/44H21vB.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/RCsMAAC.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2> Step 5: Restart the IIS Server</h2>
<p> Next, search for Internet Information Services (IIS) in the Start menu and select Open to launch the IIS Manager. Once it's open, click Restart on the right-hand side to ensure the web server is refreshed and ready to serve your files.

In the left-hand panel, navigate through the directory tree by selecting your computer name (e.g., VirtualMachine) > Sites > Default Web Site, and then click on the osTicket folder you previously placed in the wwwroot directory.

With osTicket selected, look to the right-hand panel and click “Browse *:80”. This will launch your default web browser and open the osTicket setup page, confirming that your installation is being served correctly.

Before moving forward with the setup, return to IIS Manager to continue with the necessary configuration steps.</p>

<p> </p>


<img src="https://i.imgur.com/bMXwpEU.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/NMz0MFd.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h2> Step 6: Enable Extensions in IIS </h2>
<p> Return to IIS Manager and navigate to Sites > Default Web Site > osTicket. Once there, double-click on PHP Manager in the main window. Scroll down to the bottom of the screen and click on "Enable or Disable an Extension" under the PHP Extensions section.

In the list that appears, locate the following extensions:
 -  php_imap.dll (this may already be enabled)
 -  php_intl.dll,
 -  php_opcache.dll. 
Right-click on each one and select Enable to ensure they're active. These extensions are essential for osTicket to function properly, especially for features like email piping and internationalization.</p>

<img src="https://i.imgur.com/XyWWK9r.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/iVVLP1F.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2> Step 7: Refresh the osTicket Site in Your Browser</h2>
<p>After enabling the necessary PHP extensions, return to your web browser and refresh the osTicket site. You should now see that the Intl Extension has a green checkmark next to it on the requirements page. This indicates that the extension is properly enabled and that your environment is correctly configured to proceed with the installation.</p>
<img src="https://i.imgur.com/NMz0MFd.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

<h2> Step 8: Rename</h2>
<p> Open File Explorer and navigate to the following path:
C: > inetpub > wwwroot > osTicket > include.

Inside the include folder, locate the file named ost-SAMPLEconfig.php. Right-click on this file and rename it to ost-config.php. This step is essential, as osTicket requires this configuration file to complete the installation process and connect to the database properly./p>

<img src="https://i.imgur.com/0Yunw16.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2> Step 9: Assign Permissions to ost-config.php</h2>
<p>Right-click on the ost-config.php file and select Properties. In the Properties window, go to the Security tab and click on the Advanced button. Under the Permissions section, click Disable Inheritance, then choose “Remove all inherited permissions from this object.”

This step helps secure the configuration file by ensuring only explicitly defined permissions apply, reducing the risk of unauthorized access or modifications.</p>

<img src="https://i.imgur.com/nCQ6UBM.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<p>Next, click on Add, then select Select a principal. In the dialog box that appears, type "Everyone" and click Check Names to verify the entry. Once confirmed, click OK.

In the permissions window, check Full control to grant all permissions to "Everyone." After selecting all the boxes, click Apply, then OK to save the changes. This temporary permission setting allows osTicket to write to the configuration file during installation. You can tighten these permissions after the setup is complete to enhance security.</p>



<h2> Step 10: Continue Settting Up osTicket in Browser</h2>
<p>Return to your web browser and click Continue to proceed with the osTicket setup. On the configuration page, fill out the required fields as follows:

Name: Enter a name for your helpdesk (e.g., Helpdesk).

Email: Use any valid email address you'd like to associate with the helpdesk.

First Name: Enter your own first name.

Last Name: Enter your own last name.

Email Address: Provide a valid personal email address—this should be different from the helpdesk's default email.

Username: Use user_admin as the administrator username.

Password: Set the password to Password1.

This information sets up your helpdesk identity and creates the main admin account for accessing the osTicket dashboard.</p>
<img src="https://i.imgur.com/oT7zaf3.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

<h2> Step 11: Download and Install HeidiSQL</h2>
<p>Next, go to the osTicket Installation Files link provided in your lab and download HeidiSQL, a tool used to manage MySQL databases. Once the download is complete, install and launch HeidiSQL.

In the HeidiSQL interface, click "New" at the bottom-left corner to create a new session. For the connection settings, enter the following:

User: root

Password: Password

After entering the credentials, click Open to connect to the MySQL server.

Once connected, look to the left panel, right-click on Unnamed (or the server name), and select Create New > Database. When prompted, name the new database osTicket and click OK to create it. This will serve as the database for your osTicket installation.</p>

<img src="https://i.imgur.com/MAtavm2.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://i.imgur.com/cIViv8Q.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<h2> Step 12: Continue Setting Up osTicket</h2>
<p>Return to your web browser to complete the osTicket installation form. For the MySQL Database, enter osTicket—this is the database you created earlier in HeidiSQL.

For the MySQL Username, type root, and for the MySQL Password, enter Password1 (make sure it matches what you configured earlier).

Once all the required fields are filled out, click Install Now to begin the final installation process.</p>
<img src="https://i.imgur.com/kWH43qO.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

<h2>Congratulations! You have sucessfully installed osTicket adn all of its pre-requisite files!</h2>

<img src="https://i.imgur.com/tNwHF8y.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/> 

