# Part 2 — Post-Installation Configuration

[← Previous: Installation](01-installation.md) | [🏠 Main Project](README.md) | [Next: Ticket Lifecycle →](03-ticket-lifecycle.md)

## Overview

With osTicket installed and running, I configured the platform into a structured help desk environment that could support realistic ticket handling.

This stage focused on controlling user access, organizing support staff, defining permissions, creating an escalation path, and establishing how urgent support requests would be categorized and handled.

The configuration included:

- User authentication and registration settings
- Roles and permissions
- Departments
- Support teams
- Support agents
- Service Level Agreements (SLAs)
- Help Topics

These settings provide the structure used in the ticket lifecycle scenarios in Part 3.

---

## Configuring User Access

I started by configuring how end users would access the help desk.

For this environment, users are required to register and log in before creating tickets.

Registration was configured as:

**Private — Only agents can register users**

![User authentication settings](images/configuration/01-user-authentication-settings.png)

Additional authentication settings included:

- 4 failed login attempts before lockout
- 2-minute account lockout
- 30-minute user session timeout
- Authentication tokens enabled
- Email verification required when checking ticket status

This configuration gives the help desk more control over who can create and access support requests.

---

## Configuring Roles and Permissions

Roles determine what agents are allowed to do inside osTicket.

I reviewed the available roles and added a **Master Admin** role for higher-level administrative access.

![Roles configured in osTicket](images/configuration/02-roles-list.png)

The available roles included:

- All Access
- Expanded Access
- Limited Access
- Master Admin
- View Only

Using roles allows administrative permissions to be separated from normal ticket-handling responsibilities.

---

## Creating the System Administrators Department

Departments provide an organizational structure for agents and tickets.

I created a **System Administrators** department for higher-level technical and administrative responsibilities.

![System Administrators department](images/configuration/03-system-administrators-department.png)

The department was configured with:

- **Name:** System Administrators
- **Status:** Active
- **Type:** Public
- **Ticket Assignment:** All

This gives the help desk a separate area for issues that require more advanced technical support than the standard Support department.

---

## Creating a Level II Support Team

I created a **Level II Support** team to provide an escalation path for issues that cannot be resolved during initial troubleshooting.

![Level II Support team](images/configuration/04-level-ii-support-team.png)

The team was configured as active and can be used to bring additional technical experience into a ticket without changing the overall department structure.

A basic escalation path can now look like:

```text
Support Agent
     ↓
Initial Troubleshooting
     ↓
Issue Requires Additional Expertise
     ↓
Level II Support
