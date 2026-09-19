# Part 2 — Post-Installation Configuration

[← Previous: Installation](01-installation.md) | [🏠 Main Project](README.md) | [Next: Ticket Lifecycle →](03-ticket-lifecycle.md)

## Overview

After installing osTicket, I configured the platform into a structured help desk environment for ticket handling.

The goal of this stage was to define how users access support, how support staff are organized, what permissions agents receive, how urgent incidents are handled, and how tickets are categorized when submitted.

The configuration included:

- User authentication and registration settings
- Roles
- Departments
- Teams
- Support agents
- Service Level Agreements (SLAs)
- Help Topics

These settings provide the structure used during the ticket lifecycle scenarios in Part 3.

---

## Configuring User Access

I first reviewed how end users would access the help desk.

For this environment, I configured osTicket so that users must have an account and log in before creating tickets.

Registration was set to:

**Private — Only agents can register users**

![User authentication settings](images/configuration/01-user-authentication-settings.png)

The configuration also includes:

- 4 failed login attempts before lockout
- 2-minute account lockout
- 30-minute user session timeout
- Authentication tokens enabled
- Email verification required when checking ticket status

This gives the help desk more control over who can create and access support requests.

---

## Configuring Roles

Roles determine what agents can do inside osTicket.

The environment includes the standard osTicket roles, plus a **Master Admin** role for higher-level administrative access.

![Roles configured in osTicket](images/configuration/02-roles-list.png)

The available roles include:

- All Access
- Expanded Access
- Limited Access
- Master Admin
- View Only

Using roles separates administrative access from normal ticket-handling responsibilities.

---

## Creating the System Administrators Department

Departments organize support staff and control where tickets can be assigned.

I created a **System Administrators** department for administrative or higher-level technical responsibilities.

![System Administrators department](images/configuration/03-system-administrators-department.png)

The department was configured as:

- **Name:** System Administrators
- **Status:** Active
- **Type:** Public
- **Ticket Assignment:** All

This provides a separate organizational area from the standard Support department.

---

## Creating a Level II Support Team

I also created a **Level II Support** team.

![Level II Support team](images/configuration/04-level-ii-support-team.png)

Teams provide another way to organize agents without changing their primary department.

This gives the help desk a structure to use for escalation when an issue requires more advanced troubleshooting.

For example:

```text
Support Agent
     ↓
Initial troubleshooting
     ↓
Issue requires additional expertise
     ↓
Level II Support
