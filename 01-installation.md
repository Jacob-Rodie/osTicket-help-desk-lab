# Part 1 — Installing osTicket

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)

## Overview

This section covers preparing the Windows environment used to host the osTicket help desk.

Rather than beginning with a preconfigured ticketing system, the environment is built by installing and connecting the individual components osTicket depends on: **IIS** as the web server, **PHP** to process the application, and **MySQL** to store its data.

The environment is hosted on a **Windows 11 Enterprise virtual machine in Microsoft Azure**.

Azure VM creation is covered separately in the [Active Directory User Management & Administration](https://github.com/Jacob-Rodie/active-directory-user-management) project, so this walkthrough begins with preparing Windows to host osTicket.

---

## Technologies Used

* Microsoft Azure
* Microsoft Remote Desktop
* Windows 11 Enterprise
* Internet Information Services (IIS)
* PHP
* MySQL
* HeidiSQL
* osTicket

---

## Software & Installation Components

* Microsoft Azure Virtual Machine — Windows 11 Enterprise 25H2, Gen2
* osTicket v1.15.8
* MySQL Server v5.5.62 (win32)
* HeidiSQL v12.3.0.6589
* PHP 7.3.8 NTS (Win32 VC15 x86)
* PHP Manager for IIS v1.5.0
* IIS URL Rewrite Module 2
* Microsoft Visual C++ 2015–2022 Redistributable (x86) — 14.34.31931

---

## How the Environment Fits Together

The application stack for this project can be viewed as:

```text
Browser
   ↓
IIS
   ↓
PHP
   ↓
osTicket
   ↓
MySQL
```

IIS receives the web request, PHP processes the osTicket application, and MySQL stores the help desk data.

---

## Preparing IIS

osTicket is a PHP web application, so the Windows environment first needs a web server to host it.

For this environment, **Internet Information Services (IIS)** is used.

From Control Panel, open:

**Programs → Turn Windows features on or off**

![Control Panel Programs](images/installation/01-control-panel-programs.png)

Under **Internet Information Services**, navigate to:

**World Wide Web Services → Application Development Features**

Enable **CGI**.

![Enable IIS and CGI](images/installation/02-enable-iis-cgi.png)

CGI is required because IIS uses FastCGI to process the PHP application.

---

## Installing the PHP Components

Install **PHP Manager for IIS** so PHP can be registered and managed directly through IIS Manager.

![PHP Manager installed](images/installation/03-php-manager-installed.png)

Install the **IIS URL Rewrite Module** included with the installation files.

![IIS URL Rewrite installed](images/installation/04-iis-url-rewrite-installed.png)

The PHP build used in this environment also requires the Microsoft Visual C++ runtime, so install the included **Visual C++ Redistributable (x86)**.

![Visual C++ Redistributable installed](images/installation/05-vc-redist-installed.png)

Create the following directory:

`C:\PHP`

Extract PHP 7.3.8 into that directory.

![PHP files extracted](images/installation/06-php-files-extracted.png)

Keeping PHP in its own directory gives IIS a consistent location for the PHP executable.

---

## Setting Up MySQL

osTicket uses a database to store tickets, users, departments, and application settings.

Install **MySQL Server 5.5.62** using the Typical setup.

![MySQL Server installed](images/installation/07-mysql-server-installed.png)

After installation, run the MySQL configuration wizard using the **Standard Configuration**.

The final screen should confirm that:

* The configuration file was created
* The Windows service was installed
* The service started successfully
* Security settings were applied

![MySQL Server configured](images/installation/08-mysql-server-configured.png)

At this point, MySQL is running and ready for the osTicket database to be created later in the installation.

---

## Connecting PHP to IIS

With PHP extracted, open **PHP Manager** in IIS.

Select:

**Register new PHP version**

Browse to:

`C:\PHP\php-cgi.exe`

![Select PHP CGI executable](images/installation/09-select-php-cgi.png)

After registration, PHP Manager should recognize PHP 7.3.8 and its configuration.

![PHP registered in IIS](images/installation/10-php-registered-in-iis.png)

This is an important checkpoint because IIS can now process PHP rather than only serving static web content.

---

## Adding osTicket to the IIS Web Root

Extract the **osTicket v1.15.8** package.

The application files are contained inside a folder named:

`upload`

Move the folder into the default IIS web root:

`C:\inetpub\wwwroot`

![Move osTicket to IIS web root](images/installation/11-move-osticket-to-webroot.png)

Rename the folder from:

`upload`

to:

`osTicket`

The final application path becomes:

`C:\inetpub\wwwroot\osTicket`

![osTicket folder in IIS web root](images/installation/12-osticket-webroot.png)

Placing the application in the IIS web root allows IIS to serve osTicket through the browser.

---

## Reloading IIS

After adding the osTicket application files, restart IIS so the web server reloads the environment.

Stop IIS:

![Stop IIS](images/installation/13-stop-iis.png)

Then start IIS again:

![Start IIS](images/installation/14-start-iis.png)

After the restart, you can open the osTicket Installer locally.

---

## Checking the osTicket Prerequisites

When the osTicket Installer opens, it performs a prerequisite check and shows which PHP components are available.

Several recommended extensions need to be enabled through PHP Manager:

* `php_imap.dll`
* `php_intl.dll`
* `php_opcache.dll`

After enabling the extensions, refresh the osTicket Installer to verify the changes.

![PHP extensions verification](images/installation/15-php-extensions-verification.png)

The required PHP and MySQL components should now be detected successfully.

During this step, `php_opcache.dll` appeared enabled in PHP Manager while osTicket continued to report Zend OPcache as unavailable.

Because osTicket listed Zend OPcache as a **recommended** rather than **required** component, this did not prevent the installation from continuing.

---

## Preparing the osTicket Configuration File

Before continuing with the Installer, prepare the configuration file that osTicket uses to store its settings.

Navigate to:

`C:\inetpub\wwwroot\osTicket\include`

Rename:

`ost-sampleconfig.php`

to:

`ost-config.php`

Temporarily give the installer permission to write to this file so it can save the application configuration.

Once the installation is complete, the file permissions will be restricted again.

---

## Starting the osTicket Installer

Continue to the main **osTicket Basic Installation** page.

![osTicket Basic Installation](images/installation/16-osticket-basic-installation.png)

The Installer requires three main groups of information:

* Help desk settings
* The initial administrator account
* MySQL database connection information

Before completing the database portion of the form, create the Database that osTicket will use.

---

## Creating the osTicket Database

Install **HeidiSQL** to manage the local MySQL server.DatabaseiSQL installed](images/installation/17-heidisql-installed.png)

After connecting to MySQL, right-click the server connection and select:

**Create new → Database**

![Create database in HeidiSQL](images/installation/18-create-database-menu.png)

Create a new database named:

`osTicket`

![Create osTicket database](images/installation/19-create-osticket-database.png)

This Database serves as the ticketing system's backend.

---

## Connecting osTicket to MySQL

Return to the osTicket Installer and complete the system, administrator, and database settings.

For the database connection, use:

* **Hostname:** `localhost`
* **Database:** `osTicket`
* **MySQL User:** `root`

Because MySQL and osTicket are running on the same virtual machine, the database server can be referenced as:

`localhost`

The screenshot obscures sensitive account information.

![osTicket installation configured](images/installation/20-osticket-installation-configuredDatabaDatabaseeviewing the configuration, begin the installation.

---

## Verifying the Installation

A successful installation displays the osTicket completion page.

![osTicket installation complete](images/installation/21-osticket-installation-complete.png)

Reaching this point confirms that the main components of the environment are working together:

**IIS → PHP → osTicket → MySQL**

The application is now installed and ready for post-installation configuration.

---

## Post-Installation Cleanup

Before moving on to configuration, complete the installation cleanup steps.

Delete the installer directory:

`C:\inetpub\wwwroot\osTicket\setup`

Then change the permissions on:

`C:\inetpub\wwwroot\osTicket\include\ost-config.php`

back to **Read-only**.

The configuration file requires write access during installation, but it no longer needs to be writable once the application settings are saved.

This completes the installation portion of the project.

---

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)
