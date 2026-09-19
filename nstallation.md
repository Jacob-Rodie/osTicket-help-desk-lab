# Part 1 — Installing osTicket

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)

## Overview

In this part of the project, I built the Windows environment that would host my osTicket help desk.

Rather than starting with an already-configured ticketing system, I installed and connected the individual components osTicket depends on: **IIS** as the web server, **PHP** to run the application, and **MySQL** to store its data.

The environment was hosted on a **Windows 11 Enterprise virtual machine in Microsoft Azure**.

Azure VM creation is covered separately in my [Active Directory User Management & Administration](https://github.com/Jacob-Rodie/active-directory-user-management) project, so this walkthrough begins with preparing Windows to host osTicket.

## Technologies Used

* Microsoft Azure
* Microsoft Remote Desktop
* Windows 11 Enterprise
* Internet Information Services (IIS)
* PHP
* MySQL
* HeidiSQL
* osTicket

## Software & Installation Components

* Microsoft Azure Virtual Machine — Windows 11 Enterprise 25H2, Gen2
* osTicket v1.15.8
* MySQL Server v5.5.62 (win32)
* HeidiSQL v12.3.0.6589
* PHP 7.3.8 NTS (Win32 VC15 x86)
* PHP Manager for IIS v1.5.0
* IIS URL Rewrite Module 2
* Microsoft Visual C++ 2015–2022 Redistributable (x86) — 14.34.31931

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

osTicket is a PHP web application, so I first needed a web server capable of hosting it.

On Windows, I used **Internet Information Services (IIS)**.

From Control Panel, I opened:

**Programs → Turn Windows features on or off**

![Control Panel Programs](images/installation/01-control-panel-programs.png)

Under **Internet Information Services**, I navigated to:

**World Wide Web Services → Application Development Features**

and enabled **CGI**.

![Enable IIS and CGI](images/installation/02-enable-iis-cgi.png)

CGI is needed here because IIS uses FastCGI to process the PHP application.

---

## Installing the PHP Components

I installed **PHP Manager for IIS** so I could register and manage PHP directly through IIS Manager.

![PHP Manager installed](images/installation/03-php-manager-installed.png)

I also installed the **IIS URL Rewrite Module** included with the installation files.

![IIS URL Rewrite installed](images/installation/04-iis-url-rewrite-installed.png)

The PHP build used in this environment also required the Microsoft Visual C++ runtime, so I installed the included **Visual C++ Redistributable (x86)**.

![Visual C++ Redistributable installed](images/installation/05-vc-redist-installed.png)

I then created:

`C:\PHP`

and extracted PHP 7.3.8 into that directory.

![PHP files extracted](images/installation/06-php-files-extracted.png)

Keeping PHP in its own directory gave IIS a consistent location for the PHP executable.

---

## Setting Up MySQL

osTicket uses a database to store information such as tickets, users, departments, and application settings.

I installed **MySQL Server 5.5.62** using the Typical setup.

![MySQL Server installed](images/installation/07-mysql-server-installed.png)

After the installation finished, I ran the MySQL configuration wizard using the Standard Configuration.

The final screen confirmed that the configuration file had been created, the Windows service had been installed, the service had started successfully, and the security settings had been applied.

![MySQL Server configured](images/installation/08-mysql-server-configured.png)

At this point, MySQL itself was running. I would create the actual osTicket database later in the installation.

---

## Connecting PHP to IIS

With PHP extracted, I returned to IIS and opened **PHP Manager**.

I selected **Register new PHP version** and browsed to:

`C:\PHP\php-cgi.exe`

![Select PHP CGI executable](images/installation/09-select-php-cgi.png)

After registering it, PHP Manager confirmed that IIS recognized PHP 7.3.8 and its configuration.

![PHP registered in IIS](images/installation/10-php-registered-in-iis.png)

This was an important checkpoint because IIS could now process PHP instead of only serving static web content.

---

## Adding osTicket to the IIS Web Root

Next, I extracted the **osTicket v1.15.8** package.

The application files were contained inside a folder named `upload`, which I moved into the default IIS web root:

`C:\inetpub\wwwroot`

![Move osTicket to IIS web root](images/installation/11-move-osticket-to-webroot.png)

I then renamed the folder from `upload` to:

`osTicket`

The final application path became:

`C:\inetpub\wwwroot\osTicket`

![osTicket folder in IIS web root](images/installation/12-osticket-webroot.png)

Placing the application in the IIS web root allowed IIS to serve osTicket through the browser.

---

## Reloading IIS

After adding the osTicket application files, I restarted IIS so the web server would reload the environment.

I first stopped IIS:

![Stop IIS](images/installation/13-stop-iis.png)

and then started it again:

![Start IIS](images/installation/14-start-iis.png)

After the restart, I was able to open the osTicket installer locally.

---

## Checking the osTicket Prerequisites

When I opened the osTicket installer, it performed a prerequisite check and showed which PHP components were available.

Several recommended extensions still needed to be enabled, so I returned to PHP Manager and enabled:

* `php_imap.dll`
* `php_intl.dll`
* `php_opcache.dll`

I then refreshed the osTicket installer to verify the changes.

![PHP extensions verification](images/installation/15-php-extensions-verification.png)

The required PHP and MySQL components were detected successfully.

One thing I noticed during this step was that `php_opcache.dll` appeared enabled in PHP Manager while osTicket continued to report Zend OPcache as unavailable. Because osTicket listed it as a recommended rather than required component, it did not prevent the installation from continuing.

---

## Preparing the osTicket Configuration File

Before continuing with the installer, I prepared the configuration file that osTicket would use to store its settings.

Inside:

`C:\inetpub\wwwroot\osTicket\include`

I renamed:

`ost-sampleconfig.php`

to:

`ost-config.php`

I temporarily gave the installer permission to write to this file so it could save the application configuration.

Once the installation was complete, I restricted those permissions again.

---

## Starting the osTicket Installer

After the server requirements were ready, I continued to the main **osTicket Basic Installation** page.

![osTicket Basic Installation](images/installation/16-osticket-basic-installation.png)

The installer required three main sets of information:

* Help desk settings
* The initial administrator account
* MySQL database connection information

Before completing the database portion of the form, I created the database that osTicket would use.

---

## Creating the osTicket Database

I installed **HeidiSQL** to manage the local MySQL server.

![HeidiSQL installed](images/installation/17-heidisql-installed.png)

After connecting to MySQL, I right-clicked the server connection and selected:

**Create new → Database**

![Create database in HeidiSQL](images/installation/18-create-database-menu.png)

I created a new database named:

`osTicket`

![Create osTicket database](images/installation/19-create-osticket-database.png)

This Database became the backend used by the ticketing system.

---

## Connecting osTicket to MySQL

I returned to the osTicket installer and completed the system, administrator, and database settings.

For the database connection, I used:

* **Hostname:** `localhost`
* **Database:** `osTicket`
* **MySQL User:** `root`

Because MySQL and osTicket ran on the same virtual machine, the database server could be referenced as `localhost`.

The screenshot obscures sensitive account information.

![osTicket installation configured](images/installation/20-osticket-installation-configured.png)

After reviewing the configuration, I started the installation.

---

## Verifying the Installation

The installation completed successfully.

![osTicket installation complete](images/installation/21-osticket-installation-complete.png)

Reaching this point confirmed that the main components of the environment were working together:

**IIS → PHP → osTicket → MySQL**

The next stage of the project is configuring the fresh osTicket installation into a functioning help desk environment.

---

## Post-Installation Cleanup

Before moving on to configuration, I completed the installation cleanup steps.

I deleted the installer directory:

`C:\inetpub\wwwroot\osTicket\setup`

I also changed the permissions on:

`C:\inetpub\wwwroot\osTicket\include\ost-config.php`

back to **Read-only**.

The configuration file needed write access during installation, but it no longer needed to remain writable once the application settings were saved.

This completed the installation portion of the project.

---

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)
