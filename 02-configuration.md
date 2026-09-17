# Part 2 — osTicket Post-Installation Configuration

[← Previous: Installation](installation.md) | [🏠 Main Project](README.md) | [Next: Ticket Lifecycle →](ticket-lifecycle.md)

---

## Overview

In this section of the project, I configured the osTicket environment after completing the initial installation.

The goal was to prepare the ticketing system to simulate a realistic IT help desk environment by creating roles, departments, teams, agents, users, Service Level Agreements (SLAs), and help topics.

This configuration provides the structure needed to assign, prioritize, escalate, and resolve support tickets during the ticket lifecycle portion of the lab.

---

## Configuration Objectives

During this portion of the lab, I configured:

* Roles and permissions
* Departments
* Teams
* Agents
* Users
* Service Level Agreements (SLAs)
* Help Topics
* Ticket settings and permissions

---

# 1. Configure Roles

Roles determine what permissions agents have inside the osTicket system.

To configure roles:

1. Navigate to the **Admin Panel**.
2. Select **Agents**.
3. Select **Roles**.
4. Click **Add New Role**.
5. Enter the role name.
6. Configure the appropriate permissions.
7. Save the role.

### Roles Created

* Help Desk Technician
* Senior Technician
* Help Desk Administrator

### Screenshot

![Configure Roles](images/configuration/roles.png)

### What I Learned

Roles allow administrators to control what different support technicians can access and modify inside the ticketing system. This helps enforce appropriate permissions and separates responsibilities between support staff.

---

# 2. Configure Departments

Departments allow tickets to be organized and routed to the appropriate area of the IT support team.

To configure departments:

1. Navigate to **Admin Panel → Staff → Departments**.
2. Select **Add New Department**.
3. Enter the department name.
4. Configure the department settings.
5. Save the department.

### Departments Created

* Help Desk
* Systems Administration
* Network Operations

### Screenshot

![Configure Departments](images/configuration/departments.png)

### What I Learned

Departments help organize support requests by technical responsibility. For example, basic issues can remain with the Help Desk while more advanced server or network issues can be escalated to specialized teams.

---

# 3. Configure Teams

Teams allow agents from different departments or roles to work together on specific types of tickets.

To configure teams:

1. Navigate to **Admin Panel → Agents → Teams**.
2. Select **Add New Team**.
3. Enter the team name.
4. Assign agents to the team.
5. Save the team.

### Teams Created

* Tier 1 Support
* Tier 2 Support

### Screenshot

![Configure Teams](images/configuration/teams.png)

### What I Learned

Teams make it possible to group technicians based on support responsibilities rather than only by department. This can help organizations assign tickets to technicians with the appropriate level of experience.

---

# 4. Configure Agents

Agents are the IT support staff responsible for reviewing, troubleshooting, updating, and resolving tickets.

To configure agents:

1. Navigate to **Admin Panel → Agents → Agents**.
2. Select **Add New Agent**.
3. Enter the agent's information.
4. Assign the agent to a department.
5. Assign the appropriate role and permissions.
6. Add the agent to a team if required.
7. Save the account.

### Example Agents

* Tier 1 Help Desk Technician
* Tier 2 Technician
* Help Desk Administrator

### Screenshot

![Configure Agents](images/configuration/agents.png)

### What I Learned

Agent accounts determine which technicians can access tickets and what actions they are allowed to perform. Assigning the correct department, team, and permissions helps create a structured support environment.

---

# 5. Configure Users

Users represent the employees or customers who submit support requests to the help desk.

To configure users:

1. Navigate to the **Agent Panel**.
2. Select **Users**.
3. Select **Add User**.
4. Enter the user's name and email address.
5. Save the user.

### Example Users Created

* Employee 1
* Employee 2
* Employee 3

### Screenshot

![Configure Users](images/configuration/users.png)

### What I Learned

User accounts allow the help desk to track who submitted a ticket and maintain a history of that user's support requests.

---

# 6. Configure Service Level Agreements (SLAs)

Service Level Agreements define expected response and resolution timeframes based on the urgency of a support request.

To configure SLAs:

1. Navigate to **Admin Panel → Manage → SLA Plans**.
2. Select **Add New SLA Plan**.
3. Enter the SLA name.
4. Configure the grace period and schedule.
5. Save the SLA.

### SLA Plans Created

| SLA   | Priority | Example Use                              |
| ----- | -------- | ---------------------------------------- |
| Sev-A | Critical | Major outage or business-critical issue  |
| Sev-B | High     | Significant issue affecting productivity |
| Sev-C | Normal   | Standard support request                 |

### Screenshot

![Configure SLAs](images/configuration/slas.png)

### What I Learned

SLAs help support teams prioritize incidents and establish expectations for how quickly different types of problems should be addressed.

---

# 7. Configure Help Topics

Help Topics allow users and technicians to categorize support requests based on the type of issue.

To configure Help Topics:

1. Navigate to **Admin Panel → Manage → Help Topics**.
2. Select **Add New Help Topic**.
3. Enter the topic name.
4. Configure the appropriate department or priority.
5. Save the Help Topic.

### Help Topics Created

* Account / Password Issue
* Network Connectivity
* Hardware Issue
* Software Issue
* Equipment Request

### Screenshot

![Configure Help Topics](images/configuration/help-topics.png)

### What I Learned

Help Topics make ticket categorization easier and can help automatically route support requests to the appropriate department or support team.

---

# 8. Review Ticket Settings

After configuring the organizational structure, I reviewed the ticket settings to confirm that tickets could be created, assigned, prioritized, escalated, and resolved properly.

I verified settings related to:

* Ticket priorities
* Assignment
* Department routing
* Agent permissions
* SLA plans
* Help Topics
* Ticket status

### Screenshot

![Ticket Settings](images/configuration/ticket-settings.png)

---

# Final Configuration

After completing the configuration, the osTicket environment was ready to simulate a functioning IT help desk.

The environment now included:

```text
Help Desk Environment
│
├── Departments
│   ├── Help Desk
│   ├── Systems Administration
│   └── Network Operations
│
├── Teams
│   ├── Tier 1 Support
│   └── Tier 2 Support
│
├── Agents
├── Users
├── SLA Plans
└── Help Topics
```

This structure will be used in the next portion of the project to demonstrate the full ticket lifecycle, including ticket creation, assignment, prioritization, escalation, troubleshooting, resolution, and closure.

---

## Skills Demonstrated

* Help Desk Configuration
* Ticketing System Administration
* User and Agent Management
* Role-Based Access Control
* Service Level Agreement Management
* Ticket Categorization
* Incident Prioritization
* Technical Documentation

---

## Next Section

Continue to the ticket lifecycle demonstration:

### [Part 3 — Ticket Lifecycle →](03-ticket-lifecycle.md)

---

[← Previous: Installation](installation.md) | [🏠 Main Project](README.md) | [Next: Ticket Lifecycle →](ticket-lifecycle.md)
