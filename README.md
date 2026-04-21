<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo" />
</p>

<h1 align="center">osTicket: Prerequisites and Installation</h1>

<p>
  This project demonstrates the installation and initial configuration of osTicket, an open-source help desk ticketing system, within a Windows 10 virtual machine hosted in Microsoft Azure. The lab focused on preparing the required web server environment, installing dependencies, configuring the application, and verifying that the help desk platform was operational.
</p>

<hr>

<h2>🎯 Goals &amp; Objectives</h2>

<p>
  The goal of this project was to build a working osTicket environment and understand the dependencies required to host a web-based ticketing system on Windows using IIS.
</p>

<p>By the end of this lab, I aimed to:</p>

<ul>
  <li>Deploy a Windows 10 virtual machine in Azure</li>
  <li>Install and configure IIS with CGI support</li>
  <li>Install required components such as PHP, MySQL, and IIS modules</li>
  <li>Deploy osTicket into the IIS web root</li>
  <li>Enable the required PHP extensions for osTicket</li>
  <li>Configure the application and connect it to a MySQL database</li>
  <li>Verify successful installation and perform basic post-installation cleanup</li>
</ul>

<hr>

<h2>📌 Overview</h2>

<p>
  In this project, I created a Windows 10 Azure virtual machine and used it as the host for an osTicket installation. I enabled IIS, installed the required PHP and MySQL components, configured the web application files, and completed the browser-based setup process.
</p>

<p>
  This project helped reinforce how web applications depend on multiple services working together, including the web server, PHP runtime, database engine, file permissions, and application configuration.
</p>

<hr>

<h2>🧰 Technologies Used</h2>

<ul>
  <li>Microsoft Azure (Virtual Machines)</li>
  <li>Windows 10</li>
  <li>Remote Desktop Protocol (RDP)</li>
  <li>Internet Information Services (IIS)</li>
  <li>PHP Manager for IIS</li>
  <li>PHP 7.3.8</li>
  <li>MySQL 5.5.62</li>
  <li>HeidiSQL</li>
  <li>osTicket v1.15.8</li>
</ul>

<hr>

<h2>💻 Environment</h2>

<ul>
  <li>Azure Virtual Machine: <code>osticket-vm</code></li>
  <li>Operating System: Windows 10</li>
  <li>VM Size: 4 vCPUs</li>
  <li>Web Server: IIS with CGI enabled</li>
  <li>Database Server: MySQL 5.5.62</li>
  <li>Application: osTicket v1.15.8</li>
</ul>

<hr>

<h2>⚙️ Implementation</h2>

<h3>1. Azure Virtual Machine Setup</h3>

<ul>
  <li>Created a Windows 10 virtual machine in Microsoft Azure</li>
  <li>Configured the machine for Remote Desktop access</li>
  <li>Logged into the VM and prepared it for software installation</li>
</ul>

<p>
  This provided the base environment for hosting the osTicket application and its required services.
</p>

<p align="center">
  <img src="images/vm-setup.png" alt="Azure VM Setup" width="80%" />
</p>

<hr>

<h3>2. Downloading Installation Files</h3>

<ul>
  <li>Downloaded the <code>osTicket-Installation-Files.zip</code> package inside the virtual machine</li>
  <li>Extracted the files to the desktop</li>
</ul>

<p>
  This folder contained the dependencies and installation files required for the lab.
</p>

<p align="center">
  <img src="images/installation-files.png" alt="osTicket Installation Files" width="80%" />
</p>

<hr>

<h3>3. Installing IIS and Required Components</h3>

<ul>
  <li>Enabled IIS in Windows</li>
  <li>Enabled CGI under Application Development Features</li>
  <li>Installed PHP Manager for IIS</li>
  <li>Installed the IIS Rewrite Module</li>
  <li>Created the <code>C:\PHP</code> directory</li>
  <li>Extracted PHP 7.3.8 into <code>C:\PHP</code></li>
  <li>Installed the Visual C++ Redistributable</li>
</ul>

<p>
  These steps established the web server environment and prepared IIS to run PHP-based applications.
</p>

<p align="center">
  <img src="images/iis-installation.png" alt="IIS and CGI Installation" width="80%" />
</p>

<hr>

<h3>4. Installing and Configuring MySQL</h3>

<ul>
  <li>Installed MySQL 5.5.62</li>
  <li>Used the standard configuration wizard</li>
  <li>Configured the MySQL root account</li>
</ul>

<p>
  MySQL was required to store osTicket’s application data, settings, and ticket records.
</p>

<p align="center">
  <img src="images/mysql-installation.png" alt="MySQL Installation" width="80%" />
</p>

<hr>

<h3>5. Registering PHP in IIS</h3>

<ul>
  <li>Opened IIS as an administrator</li>
  <li>Registered PHP using PHP Manager</li>
  <li>Pointed IIS to <code>C:\PHP\php-cgi.exe</code></li>
  <li>Restarted IIS to apply the configuration</li>
</ul>

<p>
  This step connected the PHP runtime to IIS so PHP files could be executed properly through the web server.
</p>

<p align="center">
  <img src="images/php-registration.png" alt="PHP Registration in IIS" width="80%" />
</p>

<hr>

<h3>6. Deploying osTicket</h3>

<ul>
  <li>Extracted the osTicket installation files</li>
  <li>Copied the <code>upload</code> folder into <code>C:\inetpub\wwwroot</code></li>
  <li>Renamed <code>upload</code> to <code>osTicket</code></li>
  <li>Restarted IIS</li>
  <li>Opened the osTicket site in the browser through IIS</li>
</ul>

<p>
  This placed the application inside the IIS web root and made it accessible through the local web server.
</p>

<p align="center">
  <img src="images/osticket-deployment.png" alt="osTicket Deployment" width="80%" />
</p>

<hr>

<h3>7. Enabling Required PHP Extensions</h3>

<ul>
  <li>Reviewed the osTicket setup page and identified missing extensions</li>
  <li>Enabled the required extensions in PHP Manager:
    <ul>
      <li><code>php_imap.dll</code></li>
      <li><code>php_intl.dll</code></li>
      <li><code>php_opcache.dll</code></li>
    </ul>
  </li>
  <li>Refreshed the osTicket site and confirmed the warnings were cleared</li>
</ul>

<p>
  This step highlighted that successful application deployment depends on both the base runtime and the correct feature set being enabled.
</p>

<p align="center">
  <img src="images/php-extensions.png" alt="PHP Extensions for osTicket" width="80%" />
</p>

<hr>

<h3>8. Configuring osTicket Application Files</h3>

<ul>
  <li>Renamed <code>ost-sampleconfig.php</code> to <code>ost-config.php</code></li>
  <li>Updated permissions on <code>ost-config.php</code></li>
  <li>Disabled inheritance</li>
  <li>Assigned broader access temporarily so setup could complete</li>
</ul>

<p>
  Proper configuration and file permissions were required before the browser-based installation could continue.
</p>

<p align="center">
  <img src="images/config-file-permissions.png" alt="osTicket Config File Permissions" width="80%" />
</p>

<hr>

<h3>9. Creating the Database in HeidiSQL</h3>

<ul>
  <li>Installed HeidiSQL</li>
  <li>Connected to MySQL using the root account</li>
  <li>Created a new database named <code>osTicket</code></li>
</ul>

<p>
  This prepared the backend database required for the application installation.
</p>

<p align="center">
  <img src="images/heidisql-database.png" alt="HeidiSQL Database Creation" width="80%" />
</p>

<hr>

<h3>10. Completing osTicket Setup</h3>

<ul>
  <li>Entered the help desk name and default email address</li>
  <li>Entered MySQL database information</li>
  <li>Completed the installation through the browser</li>
  <li>Verified access to the admin login page and end-user portal</li>
</ul>

<p>
  This confirmed that IIS, PHP, MySQL, and osTicket were working together as a complete application stack.
</p>

<p align="center">
  <img src="images/osticket-installed.png" alt="osTicket Successfully Installed" width="80%" />
</p>

<hr>

<h2>🔍 Troubleshooting</h2>

<h3>Missing PHP Extensions</h3>

<ul>
  <li><strong>Problem:</strong> osTicket setup reported missing required extensions</li>
  <li><strong>Cause:</strong> PHP was installed, but necessary modules were not yet enabled in IIS</li>
  <li><strong>Fix:</strong> Enabled the required PHP extensions through PHP Manager and refreshed the site</li>
</ul>

<p>
  This reinforced that application installation problems are often dependency problems rather than application problems.
</p>

<h3>Configuration File Access</h3>

<ul>
  <li><strong>Problem:</strong> osTicket required changes to the configuration file before installation could continue</li>
  <li><strong>Cause:</strong> Default file state and permissions were not suitable for setup</li>
  <li><strong>Fix:</strong> Renamed the sample configuration file and adjusted permissions temporarily</li>
</ul>

<p>
  This showed how file permissions can directly affect installation success.
</p>

<hr>

<h2>🧠 Design Decisions</h2>

<ul>
  <li>Used Azure to simulate a realistic cloud-hosted support system environment</li>
  <li>Used IIS with CGI to support PHP-based application hosting on Windows</li>
  <li>Created a dedicated <code>C:\PHP</code> directory to keep the PHP runtime organized and separate</li>
  <li>Used HeidiSQL to simplify MySQL database creation and management</li>
  <li>Performed post-installation cleanup to reduce unnecessary exposure of setup files</li>
</ul>

<hr>

<h2>🛡️ Security Awareness</h2>

<ul>
  <li>Installation and setup files should not remain exposed after deployment</li>
  <li>Configuration file permissions should be tightened after installation completes</li>
  <li>Using readable passwords in documentation is not a real-world best practice</li>
  <li>Administrative credentials and database credentials should be protected using secure storage practices</li>
</ul>

<hr>

<h2>🌍 Real-World Relevance</h2>

<ul>
  <li>Help desk platforms are commonly used in IT environments to manage support requests and workflows</li>
  <li>Installing osTicket reinforces how web applications depend on the web server, runtime, database, and file permissions working together</li>
  <li>This type of deployment builds practical experience relevant to system administration, IT support, and entry-level infrastructure roles</li>
</ul>

<hr>

<h2>📌 Lessons Learned</h2>

<ul>
  <li>Web application deployment depends heavily on prerequisite components being installed in the correct order</li>
  <li>Missing runtime extensions can prevent an application from functioning even when the main software is installed</li>
  <li>File permissions are a critical part of successful setup and post-installation hardening</li>
  <li>Installing an application is only part of the work; cleanup and tightening permissions matter too</li>
  <li>Understanding dependencies makes troubleshooting much faster and more methodical</li>
</ul>

<hr>

<h2>💭 Key Takeaways</h2>

<p>
  Before this lab, it would have been easy to think of installing a help desk platform as just running an installer. In practice, the process required coordinating IIS, PHP, MySQL, application files, permissions, and browser-based configuration.
</p>

<p>
  This project helped me better understand how multiple infrastructure components support a single business application and how small missing pieces can prevent the entire system from working.
</p>

<hr>

<h2>🧹 Cleanup</h2>

<ul>
  <li>Deleted the <code>setup</code> folder from the osTicket web directory</li>
  <li>Changed <code>ost-config.php</code> permissions to read-only</li>
</ul>

<p>
  These steps reduced unnecessary risk after installation and left the application in a more secure state.
</p>

<p align="center">
  <img src="images/cleanup.png" alt="osTicket Cleanup" width="80%" />
</p>
