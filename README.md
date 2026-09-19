# osTicket Help Desk Deployment, Configuration & Ticket Lifecycle

## Project Summary

This project documents the deployment and configuration of an **osTicket help desk environment** designed to simulate the workflow of an entry-level IT support team.

I built the environment on a Windows 11 Enterprise virtual machine hosted in Microsoft Azure, configured the web and database services required to run osTicket, and documented the implementation from installation through help desk configuration and ticket handling.

The project is organized into three connected sections:

1. **Installation** — Deploying osTicket and its supporting services
2. **Post-Installation Configuration** — Configuring the help desk environment
3. **Ticket Lifecycle** — Working support tickets from submission through resolution

The goal of the project is to demonstrate practical experience with ticketing systems, user support, troubleshooting, documentation, prioritization, escalation, and other skills commonly used in Help Desk and Technical Support roles.

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

## Languages Used

No scripting or programming languages were required for this implementation.

Configuration was completed through Windows administration tools, IIS Manager, PHP Manager, HeidiSQL, and the osTicket administrative interface.

---

## What This Project Demonstrates

This project focuses on skills relevant to entry-level IT Support and Help Desk positions, including:

- Deploying and configuring a ticketing system
- Working with Windows-based server components
- Configuring IIS and PHP
- Connecting a web application to a MySQL database
- Managing help desk users and agents
- Configuring roles and permissions
- Organizing departments and support teams
- Creating Service Level Agreements (SLAs)
- Configuring Help Topics
- Prioritizing and assigning support tickets
- Troubleshooting user issues
- Escalating tickets when appropriate
- Documenting troubleshooting steps and resolutions
- Closing and maintaining support tickets

---

# Project Walkthrough

## Part 1 — osTicket Installation

The first part of the project covers building the environment required to run osTicket.

I configured IIS as the web server, installed and registered PHP, configured MySQL, created the osTicket database, deployed the application into the IIS web root, and completed the web-based installation.

![osTicket installation complete](images/installation/21-osticket-installation-complete.png)

[View Part 1 — Installation](01-installation.md)

---

## Part 2 — Post-Installation Configuration

The second part focuses on turning the fresh osTicket installation into a usable help desk environment.

Configuration includes:

- System settings
- Roles and permissions
- Departments
- Teams
- Agents
- Users
- Service Level Agreements
- Help Topics
- Ticket settings
- User access and authentication settings

[View Part 2 — Post-Installation Configuration](02-configuration.md)

---

## Part 3 — Ticket Lifecycle

The third part demonstrates how the configured help desk is used to handle support requests.

Support scenarios are worked from the perspective of both the end user submitting the issue and the support agent responsible for resolving it.

The ticket workflow includes:

```text
User submits support request
        ↓
Ticket enters help desk queue
        ↓
Agent reviews the issue
        ↓
Priority and SLA are evaluated
        ↓
Ticket is assigned
        ↓
Troubleshooting is performed
        ↓
Escalation when appropriate
        ↓
Resolution is documented
        ↓
Ticket is closed
