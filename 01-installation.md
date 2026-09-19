# Part 1 — osTicket Installation

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)

## Overview

In this part of the project, I installed **osTicket v1.15.8** on a Windows virtual machine and configured the supporting components required for the application to run.

The environment uses:

- Windows 11 Enterprise virtual machine hosted in Microsoft Azure
- Internet Information Services (IIS)
- PHP 7.3.8
- PHP Manager for IIS
- IIS URL Rewrite Module
- Microsoft Visual C++ Redistributable
- MySQL Server 5.5.62
- HeidiSQL
- osTicket v1.15.8

The goal of this section was to build a functioning osTicket environment before moving on to help desk configuration and ticket management.

---

## 1. Prepare the Windows Virtual Machine

I used a **Windows 11 Enterprise virtual machine in Microsoft Azure** as the environment for the osTicket deployment.

The Azure virtual machine creation process is covered separately in my:

[Active Directory User Management & Administration](https://github.com/Jacob-Rodie/active-directory-user-management)

After creating the VM, I connected to it using Remote Desktop and began preparing the Windows environment for osTicket.

---

## 2. Enable IIS and CGI

osTicket requires a web server to host the application. For this environment, I used **Internet Information Services (IIS)**, Microsoft's web server for Windows.

From Control Panel, I opened:

**Programs → Turn Windows features on or off**

![Control Panel Programs](images/installation/01-control-panel-programs.png)

Under **Internet Information Services**, I expanded:

**World Wide Web Services → Application Development Features**

I then enabled **CGI**, which allows IIS to process PHP through FastCGI.

![Enable IIS and CGI](images/installation/02-enable-iis-cgi.png)

After applying the changes, Windows installed the required IIS components.

---

## 3. Install PHP Manager for IIS

I installed **PHP Manager for IIS** so that PHP could be registered and managed through IIS Manager.

![PHP Manager installed](images/installation/03-php-manager-installed.png)

PHP Manager was later used to register the PHP executable and manage PHP extensions required by osTicket.

---

## 4. Install the IIS URL Rewrite Module

Next, I installed the **IIS URL Rewrite Module** included with the lab installation files.

![IIS URL Rewrite installed](images/installation/04-iis-url-rewrite-installed.png)

The installer completed successfully and added the URL Rewrite feature to IIS.

---

## 5. Install the Visual C++ Redistributable

I installed the **Microsoft Visual C++ Redistributable (x86)** included with the lab files.

This runtime is required by the PHP build being used in the environment.

![Visual C++ Redistributable installed](images/installation/05-vc-redist-installed.png)

---

## 6. Prepare PHP

I created the following directory:

`C:\PHP`

I then extracted the **PHP 7.3.8** files provided with the lab into this folder.

This placed the PHP executable and supporting files in a consistent location for IIS.

![PHP files extracted](images/installation/06-php-files-extracted.png)

---

## 7. Install and Configure MySQL

osTicket requires a database to store application data such as tickets, users, settings, departments, and other help desk information.

I installed **MySQL Server 5.5.62** using the Typical installation option.

![MySQL Server installed](images/installation/07-mysql-server-installed.png)

After installation, I launched the MySQL Instance Configuration Wizard and used the **Standard Configuration** option.

Once configuration completed, I verified that:

- The MySQL configuration file was created
- The MySQL Windows service was installed
- The MySQL service started successfully
- The security settings were applied

![MySQL Server configured](images/installation/08-mysql-server-configured.png)

---

## 8. Register PHP with IIS

After PHP was extracted, I opened **PHP Manager** from IIS Manager.

I selected **Register new PHP version** and browsed to:

`C:\PHP\php-cgi.exe`

![Select PHP CGI executable](images/installation/09-select-php-cgi.png)

After registering the executable, PHP Manager confirmed that IIS recognized:

- PHP version 7.3.8
- `C:\PHP\php-cgi.exe`
- The PHP configuration file
- The installed PHP extensions

![PHP registered in IIS](images/installation/10-php-registered-in-iis.png)

At this point, IIS was able to process PHP applications.

---

## 9. Add osTicket to the IIS Web Root

I extracted the **osTicket v1.15.8** installation package.

The extracted package contained an `upload` directory containing the osTicket application files.

I moved the `upload` directory into the IIS web root:

`C:\inetpub\wwwroot`

![Move osTicket to IIS web root](images/installation/11-move-osticket-to-webroot.png)

I then renamed the folder from:

`upload`

to:

`osTicket`

The final application path was:

`C:\inetpub\wwwroot\osTicket`

![osTicket folder in IIS web root](images/installation/12-osticket-webroot.png)

---

## 10. Reload IIS

After placing the osTicket application inside the IIS web root, I reloaded IIS so the server would recognize the application and updated configuration.

I first stopped the IIS server.

![Stop IIS](images/installation/13-stop-iis.png)

I then started the server again.

![Start IIS](images/installation/14-start-iis.png)

With IIS running again, I was able to browse to the osTicket installer locally.

---

## 11. Verify and Enable PHP Extensions

I opened the osTicket installer through the browser and reviewed its prerequisite check.

The required PHP and MySQL components were detected, but several recommended PHP extensions needed to be enabled.

Using **PHP Manager** in IIS, I enabled the extensions required by the lab:

- `php_imap.dll`
- `php_intl.dll`
- `php_opcache.dll`

I refreshed the osTicket installer after making the changes.

![PHP extensions verification](images/installation/15-php-extensions-verification.png)

The required components were detected successfully and the installer allowed me to continue.

`php_opcache.dll` was enabled through PHP Manager, although the osTicket prerequisite page continued to display Zend OPcache as unavailable. Because this was listed as a recommended rather than required component, it did not prevent the installation from continuing.

---

## 12. Prepare the osTicket Configuration File

Before continuing with the web installer, I prepared the osTicket configuration file.

Inside:

`C:\inetpub\wwwroot\osTicket\include`

I renamed:

`ost-sampleconfig.php`

to:

`ost-config.php`

I then temporarily adjusted the file permissions so the osTicket installer could write the required configuration information.

After the installation was completed, these permissions were restricted again during post-installation cleanup.

---

## 13. Begin the osTicket Installation

After the server prerequisites were ready, I continued to the **osTicket Basic Installation** page.

The installer required information for three areas:

- Help desk system settings
- The initial administrator account
- MySQL database settings

![osTicket Basic Installation](images/installation/16-osticket-basic-installation.png)

Before completing the database section of the installer, I created a dedicated MySQL database for osTicket.

---

## 14. Install HeidiSQL

I installed **HeidiSQL** to manage the MySQL database used by osTicket.

![HeidiSQL installed](images/installation/17-heidisql-installed.png)

After installation, I launched HeidiSQL and connected to the local MySQL server.

---

## 15. Create the osTicket Database

Inside HeidiSQL, I created a dedicated database for osTicket.

I right-clicked the MySQL server connection and selected:

**Create new → Database**

![Create database in HeidiSQL](images/installation/18-create-database-menu.png)

I named the new database:

`osTicket`

![Create osTicket database](images/installation/19-create-osticket-database.png)

This database would be used by the osTicket application to store its data.

---

## 16. Complete the osTicket Installer

After creating the database, I returned to the osTicket installer and completed the system, administrator, and database settings.

For the database connection, I used:

- **MySQL Hostname:** `localhost`
- **MySQL Database:** `osTicket`
- **MySQL Username:** `root`

Sensitive account information and credentials have been obscured in the screenshot.

![osTicket installation configured](images/installation/20-osticket-installation-configured.png)

After confirming the settings, I selected **Install Now**.

---

## 17. Verify Successful Installation

The osTicket installer completed successfully.

![osTicket installation complete](images/installation/21-osticket-installation-complete.png)

The completed installation provided access to two main interfaces:

**End-User Portal**

`http://localhost/osTicket/`

This is where users can submit and manage support requests.

**Staff Control Panel**

`http://localhost/osTicket/scp/login.php`

This is where help desk agents and administrators manage tickets and configure the system.

The successful installation confirmed that IIS, PHP, MySQL, and osTicket were working together correctly.

---

## 18. Post-Installation Cleanup

After verifying that osTicket installed successfully, I completed the cleanup steps from the lab.

I deleted the installer directory:

`C:\inetpub\wwwroot\osTicket\setup`

I also changed the permissions on:

`C:\inetpub\wwwroot\osTicket\include\ost-config.php`

so that the configuration file was set back to **Read-only**.

This completed the installation portion of the project.

---

## What I Learned

This portion of the project reinforced how several components work together to host a web-based help desk application.

I gained hands-on experience with:

- Enabling and configuring IIS on Windows
- Registering PHP with IIS through FastCGI
- Managing PHP extensions
- Installing and configuring a MySQL database server
- Using HeidiSQL to create and manage a database
- Deploying a PHP application into an IIS web root
- Verifying application prerequisites
- Connecting osTicket to a MySQL database
- Recognizing and documenting an installation issue that did not prevent deployment
- Performing post-installation cleanup

More importantly, the installation helped me understand that deploying an application involves more than simply running an installer. Each component—web server, application runtime, database, file permissions, and application configuration—needs to work together before the system is usable.

---

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)
