# Part 1 — osTicket Prerequisites & Installation

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)

---

## Overview

In this section of the project, I prepared the Windows environment and installed the components required to run osTicket.

The goal was to deploy a functional osTicket help desk environment that could later be configured with agents, departments, teams, users, SLAs, and help topics.

---

## Installation Objectives

During this portion of the lab, I:

* Prepared the Windows environment
* Enabled Internet Information Services (IIS)
* Installed PHP
* Installed and configured a database service
* Downloaded and installed osTicket
* Configured required permissions
* Completed the osTicket web installer
* Verified that the help desk portal was operational

---

## Environments and Technologies Used

**Environment**

* Windows 11
* Local virtual machine / lab environment

**Technologies and Applications**

* osTicket
* Internet Information Services (IIS)
* PHP
* MySQL / MariaDB
* Web Browser

**Languages Used**

* None

---

# 1. Prepare the Windows Environment

I first prepared the Windows system that would host the osTicket application.

Before installing osTicket, I verified that Windows was updated and that I had administrator access to make system-level changes.

### Screenshot

![Windows Environment](images/installation/windows-environment.png)

---

# 2. Enable Internet Information Services (IIS)

osTicket requires a web server to host its web interface.

I enabled **Internet Information Services (IIS)** through Windows Features.

### Steps

1. Open **Control Panel**.
2. Select **Programs and Features**.
3. Select **Turn Windows features on or off**.
4. Enable **Internet Information Services**.
5. Enable the required IIS management and web features.
6. Apply the changes.

### Screenshot

![Enable IIS](images/installation/iis.png)

### Verification

After IIS was installed, I opened a web browser and navigated to:

```text
http://localhost
```

The IIS default page confirmed that the web server was running correctly.

![IIS Verification](images/installation/iis-verification.png)

### What I Learned

IIS provides the web server environment that allows osTicket to be accessed through a browser.

---

# 3. Install PHP

osTicket is a PHP-based application, so PHP must be installed and configured before osTicket can run.

I installed the required version of PHP and configured it to work with IIS.

### Steps

1. Download PHP.
2. Extract the PHP files.
3. Configure PHP settings.
4. Enable the required PHP extensions.
5. Configure IIS to process PHP files.
6. Restart IIS.

### Screenshot

![PHP Configuration](images/installation/php.png)

### What I Learned

PHP allows the web server to process the application code used by osTicket.

---

# 4. Install the Database Service

osTicket stores ticket information, user accounts, configuration settings, and other application data inside a database.

I installed and configured **MySQL / MariaDB** to provide the database backend for the help desk.

### Steps

1. Install the database server.
2. Configure the administrative account.
3. Start the database service.
4. Create a database for osTicket.
5. Prepare the database credentials for the installer.

### Screenshot

![Database Installation](images/installation/database.png)

### What I Learned

The database stores the information required for osTicket to function, including tickets, users, agents, and system settings.

---

# 5. Download and Prepare osTicket

After the required dependencies were installed, I downloaded the osTicket application files.

### Steps

1. Download osTicket.
2. Extract the application files.
3. Copy the required files into the IIS web directory.
4. Rename the sample configuration file if required.
5. Configure the appropriate file permissions.

### Screenshot

![osTicket Files](images/installation/osticket-files.png)

---

# 6. Configure File Permissions

Before running the installer, I configured the permissions required for osTicket to write to its configuration files.

### Screenshot

![File Permissions](images/installation/permissions.png)

### What I Learned

Applications often require specific file permissions during installation. Incorrect permissions can prevent configuration files from being created or modified.

---

# 7. Run the osTicket Web Installer

Once the web server, PHP, database, and application files were ready, I launched the osTicket installer through the web browser.

### Installation Information

During setup, I configured:

* Help desk name
* Administrator account
* Administrator email
* Database name
* Database username
* Database password
* Database host

### Screenshot

![osTicket Installer](images/installation/osticket-installer.png)

---

# 8. Complete the Installation

After entering the required information, the installer completed successfully.

I verified that osTicket could connect to the database and that the application loaded correctly.

### Screenshot

![Installation Complete](images/installation/installation-complete.png)

---

# 9. Verify the Help Desk Portal

After installation, I opened the osTicket support portal to confirm that the help desk was operational.

### User Portal

The user-facing portal allows users to submit and review support requests.

![User Portal](images/installation/user-portal.png)

### Agent / Admin Portal

The administrative interface allows support staff to manage tickets and configure the help desk environment.

![Agent Portal](images/installation/agent-portal.png)

---

# Installation Complete

At this stage, the osTicket application was successfully installed and operational.

The environment now included:

```text
Windows 11
    ↓
IIS Web Server
    ↓
PHP
    ↓
MySQL / MariaDB
    ↓
osTicket
```

The next step was to configure the help desk structure, including:

* Roles
* Departments
* Teams
* Agents
* Users
* Service Level Agreements
* Help Topics

---

## Skills Demonstrated

* Application Installation
* Windows Administration
* IIS Configuration
* Web Application Deployment
* Database Setup
* File and Folder Permissions
* Troubleshooting
* Technical Documentation

---

## Next Section

Continue to the post-installation configuration:

### [Part 2 — osTicket Post-Installation Configuration →](02-configuration.md)

---

[🏠 Main Project](README.md) | [Next: Post-Installation Configuration →](02-configuration.md)
