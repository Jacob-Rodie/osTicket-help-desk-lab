# Part 2 — Post-Installation Configuration

[← Previous: Installation](01-installation.md) | [🏠 Main Project](README.md) | [Next: Ticket Lifecycle →](03-ticket-lifecycle.md)

## Overview

After installing osTicket, the next step is to configure the platform as a structured help desk environment.

This section covers the administrative settings that determine:

- How end users access support
- What permissions support agents receive
- How support staff are organized
- How tickets can be escalated
- How urgent incidents are tracked
- How users categorize support requests

The configuration created here will be used during the ticket lifecycle scenarios in Part 3.

---

## Configure User Access

User authentication settings control who can create tickets and how users access the help desk.

Navigate to the **User Settings** page and configure registration requirements.

For this environment:

- **Registration Required:** Enabled
- **Registration Method:** Private — Only agents can register users
- **Failed Login Attempts:** 4
- **Lockout Duration:** 2 minutes
- **Session Timeout:** 30 minutes
- **Authentication Tokens:** Enabled
- **Email Verification:** Required when checking ticket status

![User authentication settings](images/configuration/01-user-authentication-settings.png)

Requiring registration gives you more control over who can submit and access support requests.

---

## Configure Roles and Permissions

Roles determine which actions an agent can perform within osTicket.

Open the **Roles** section from the Agents area to review the available permission levels.

![Roles configured in osTicket](images/configuration/02-roles-list.png)

The environment contains the following roles:

- All Access
- Expanded Access
- Limited Access
- Master Admin
- View Only

A dedicated **Master Admin** role provides higher-level administrative access, while the other roles let you limit agents to the permissions they need for their responsibilities.

Roles separate normal ticket handling from administrative functions.

---

## Create the System Administrators Department

Departments organize support responsibilities and provide a destination for ticket assignment.

Create a department named:

**System Administrators**

![System Administrators department](images/configuration/03-system-administrators-department.png)

Configure the department with:

- **Status:** Active
- **Type:** Public
- **Ticket Assignment:** All

This department provides a separate destination for issues requiring higher-level technical or administrative support.

The default **Support** department can continue to handle general help desk requests.

---

## Create a Level II Support Team

Teams let agents group for a specific support function without requiring them to belong to the same primary department.

Create a new team named:

**Level II Support**

![Level II Support team](images/configuration/04-level-ii-support-team.png)

Set the team status to **Active**.

The Level II Support team provides an escalation path for tickets that cannot be resolved during initial troubleshooting.

A basic escalation path can now follow this structure:

```text
Support Agent
     ↓
Initial Troubleshooting
     ↓
Issue Cannot Be Resolved.
     ↓
Level II Support
