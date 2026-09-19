# osTicket Help Desk Deployment, Configuration & Ticket Lifecycle

## Project Summary

This project documents the deployment, configuration, and operation of an **osTicket help desk environment** that demonstrates a typical entry-level IT support workflow.

The environment is hosted on a **Windows 11 Enterprise virtual machine in Microsoft Azure**. It includes the web server, PHP runtime, database services, help desk configuration, and ticket-handling workflow required to operate osTicket.

The project is divided into three connected parts:

1. **Installation** — Preparing Windows and deploying osTicket
2. **Post-Installation Configuration** — Structuring the help desk environment
3. **Ticket Lifecycle** — Processing support requests from intake through resolution

Together, these sections demonstrate how a ticketing system is deployed, configured, and used to support end users.

---

## Environment and Technologies

- Microsoft Azure
- Windows 11 Enterprise
- Microsoft Remote Desktop
- Internet Information Services (IIS)
- osTicket v1.15.8
- PHP 7.3.8
- PHP Manager for IIS
- IIS URL Rewrite Module
- MySQL Server 5.5.62
- HeidiSQL
- Microsoft Visual C++ Redistributable

---

## Languages Used

No scripting or programming languages were required for this implementation.

Configuration was completed through Windows administration tools, IIS Manager, PHP Manager, HeidiSQL, and the osTicket administrative interface.

---

## What This Project Demonstrates

The project covers practical skills commonly used in Help Desk and Technical Support environments, including:

- Deploying and configuring a ticketing system
- Working with Windows-based application services
- Configuring IIS and PHP
- Connecting a web application to a MySQL database
- Managing users and support agents
- Configuring roles and permissions
- Organizing departments and support teams
- Creating Service Level Agreements (SLAs)
- Configuring Help Topics
- Controlling user authentication and registration
- Prioritizing support requests
- Assigning tickets to support personnel
- Troubleshooting user issues
- Escalating tickets when additional expertise is required
- Documenting troubleshooting activity and resolutions
- Closing completed support tickets

---

# Project Walkthrough

## Part 1 — Installing osTicket

The first stage prepares the Windows environment and installs the components required to run osTicket.

The installation includes:

- Enabling IIS and CGI
- Installing PHP Manager
- Installing the IIS URL Rewrite Module
- Installing the required Visual C++ runtime
- Installing and configuring MySQL
- Registering PHP with IIS
- Deploying osTicket to the IIS web root
- Creating the osTicket database
- Connecting osTicket to MySQL
- Completing post-installation cleanup

![osTicket installation complete](images/installation/21-osticket-installation-complete.png)

[View Part 1 — Installing osTicket →](01-installation.md)

---

## Part 2 — Post-Installation Configuration

The second stage turns the fresh osTicket installation into a structured help desk environment.

The configuration includes:

- User authentication and registration settings
- Roles and permissions
- Departments
- Support teams
- Support agents
- Service Level Agreements
- Help Topics

The environment also introduces a support escalation structure using the **Support department**, **Level II Support team**, and **System Administrators department**.

![Support agents](images/configuration/05-agents-list.png)

[View Part 2 — Post-Installation Configuration →](02-configuration.md)

---

## Part 3 — Ticket Lifecycle

The final stage shows how the configured help desk processes support requests.

Three ticket scenarios are used to demonstrate different support workflows:

- A business-critical incident requiring higher-priority handling and escalation
- A standard user issue resolved through Tier 1 troubleshooting
- A routine support request handled through the normal support process

The general ticket lifecycle follows:

```text
Ticket Submission
      ↓
Review & Triage
      ↓
Priority / SLA Evaluation
      ↓
Assignment
      ↓
Troubleshooting
      ↓
Escalation if Required
      ↓
Resolution
      ↓
Documentation
      ↓
Closure
```

This section shows how the configuration created in Part 2 applies during actual ticket handling.

[View Part 3 — Ticket Lifecycle →](03-ticket-lifecycle.md)

---

## How the Three Parts Connect

The project follows the same progression as a real help desk implementation:

```text
Part 1
Install the Ticketing Platform
        ↓
Part 2
Configure the Help Desk Structure
        ↓
Part 3
Use the System to Process Support Requests
```

**Part 1** establishes the technical platform.

**Part 2** defines how users, agents, departments, teams, SLAs, and Help Topics operate within that platform.

**Part 3** demonstrates how those components work together during ticket intake, troubleshooting, escalation, resolution, and closure.

---

## Project Documentation

- [Part 1 — Installing osTicket](01-installation.md)
- [Part 2 — Post-Installation Configuration](02-configuration.md)
- [Part 3 — Ticket Lifecycle](03-ticket-lifecycle.md)
