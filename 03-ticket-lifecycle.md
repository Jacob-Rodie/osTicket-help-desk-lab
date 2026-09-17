# Part 3 — osTicket Ticket Lifecycle

[← Previous: Post-Installation Configuration](02-configuration.md) | [🏠 Main Project](README.md)

---

## Overview

In this section of the project, I used the configured osTicket environment to simulate the lifecycle of real IT help desk tickets.

The goal was to demonstrate how support requests are created, reviewed, prioritized, assigned, escalated, worked, documented, resolved, and closed.

This portion of the lab allowed me to practice the day-to-day workflow of a Tier 1 help desk technician.

---

## Ticket Lifecycle Objectives

During this portion of the lab, I practiced:

* Creating support tickets
* Reviewing user-submitted issues
* Assigning ticket priorities
* Applying Service Level Agreements (SLAs)
* Assigning tickets to agents or departments
* Communicating with end users
* Documenting troubleshooting steps
* Escalating issues when necessary
* Resolving and closing tickets

---

## Ticket Lifecycle Process

A typical ticket in this lab followed the workflow below:

```text
User Submits Ticket
        ↓
Ticket Reviewed
        ↓
Priority Assigned
        ↓
SLA Applied
        ↓
Department / Agent Assigned
        ↓
Troubleshooting Performed
        ↓
Ticket Updated
        ↓
Issue Resolved
        ↓
Ticket Closed
```

---

# Ticket Scenario 1 — User Cannot Log In

## Issue

A user reported that they were unable to log into their workstation.

### Ticket Information

**Category:** Account / Password Issue
**Priority:** Normal
**Department:** Help Desk
**SLA:** Sev-C
**Status:** Open

### Screenshot

![New Login Ticket](images/tickets/login-ticket-open.png)

---

## Initial Assessment

I reviewed the ticket and confirmed the details of the user's login issue.

I determined that the problem appeared to be related to the user's account credentials rather than a hardware issue.

---

## Troubleshooting Steps

1. Reviewed the information provided by the user.
2. Confirmed the user's identity.
3. Verified the reported login problem.
4. Checked the account status.
5. Determined that the user's password required a reset.
6. Reset the user's credentials.
7. Asked the user to attempt to log in again.
8. Confirmed that the user regained access.

### Screenshot

![Login Ticket Troubleshooting](images/tickets/login-ticket-troubleshooting.png)

---

## Resolution

The user's password was reset successfully and the user confirmed that they could log into their workstation.

I documented the resolution in the ticket and changed the ticket status to **Closed**.

### Screenshot

![Login Ticket Resolved](images/tickets/login-ticket-closed.png)

### What I Learned

This ticket demonstrated the importance of verifying the user's issue, documenting troubleshooting steps, and confirming that the solution worked before closing the ticket.

---

# Ticket Scenario 2 — Printer Offline

## Issue

A user reported that they were unable to print to their office printer.

### Ticket Information

**Category:** Hardware Issue
**Priority:** Normal
**Department:** Help Desk
**SLA:** Sev-C
**Status:** Open

### Screenshot

![Printer Ticket](images/tickets/printer-ticket-open.png)

---

## Initial Assessment

I reviewed the ticket and determined that the issue affected a single user and did not represent a major business outage.

Because the impact was limited, the ticket remained at a normal priority.

---

## Troubleshooting Steps

1. Confirmed that the printer was powered on.
2. Verified the printer connection.
3. Checked whether Windows detected the printer.
4. Confirmed that the correct printer was selected.
5. Reviewed the printer queue.
6. Restarted the print service or printer if required.
7. Asked the user to print a test page.

### Screenshot

![Printer Troubleshooting](images/tickets/printer-ticket-troubleshooting.png)

---

## Resolution

The printer connection was restored and the user successfully printed a test page.

The troubleshooting steps and resolution were documented before closing the ticket.

### Screenshot

![Printer Ticket Closed](images/tickets/printer-ticket-closed.png)

### What I Learned

This scenario demonstrated how ticket priority can be based on the number of users affected and the overall impact on business operations.

---

# Ticket Scenario 3 — Department Network Outage

## Issue

Multiple users reported that they were unable to access the network or internet.

### Ticket Information

**Category:** Network Connectivity
**Priority:** Critical
**Department:** Network Operations
**SLA:** Sev-A
**Status:** Open / Escalated

### Screenshot

![Network Outage Ticket](images/tickets/network-ticket-open.png)

---

## Initial Assessment

Because multiple users were affected, I treated the incident as a higher-priority issue.

The widespread impact indicated that the problem could involve shared network infrastructure rather than an individual workstation.

---

## Troubleshooting and Escalation

1. Confirmed that multiple users were experiencing the same issue.
2. Verified that the problem was not isolated to one workstation.
3. Reviewed basic network connectivity information.
4. Confirmed the scope of the outage.
5. Increased the ticket priority.
6. Applied the appropriate SLA.
7. Reassigned or escalated the ticket to the **Network Operations** department.
8. Documented all actions taken before escalation.

### Screenshot

![Network Ticket Escalation](images/tickets/network-ticket-escalated.png)

---

## Resolution

After the issue was investigated by the appropriate support team, network connectivity was restored.

The ticket was updated with the resolution and closed after service was confirmed.

### Screenshot

![Network Ticket Closed](images/tickets/network-ticket-closed.png)

### What I Learned

This scenario demonstrated the importance of identifying the scope and business impact of an incident.

A problem affecting multiple users may require a higher priority and escalation to a specialized support team.

---

# Ticket Scenario 4 — Software Installation Request

## Issue

A user requested the installation of an approved application required for their job.

### Ticket Information

**Category:** Software Issue / Service Request
**Priority:** Normal
**Department:** Help Desk
**SLA:** Sev-C
**Status:** Open

### Screenshot

![Software Request Ticket](images/tickets/software-ticket-open.png)

---

## Initial Assessment

I reviewed the request to determine whether the software installation could be completed by the Help Desk or required additional approval.

---

## Actions Taken

1. Reviewed the software request.
2. Confirmed the application being requested.
3. Verified that the request was appropriate.
4. Assigned the ticket to the appropriate technician.
5. Documented the installation.
6. Asked the user to confirm that the application launched correctly.

### Screenshot

![Software Request Progress](images/tickets/software-ticket-progress.png)

---

## Resolution

The requested software was installed successfully and the user confirmed that the application was working correctly.

The ticket was documented and closed.

### Screenshot

![Software Ticket Closed](images/tickets/software-ticket-closed.png)

### What I Learned

This scenario helped demonstrate the difference between an incident and a service request.

Not every help desk ticket represents something that is broken. Some tickets involve standard requests for approved services or equipment.

---

# Ticket Prioritization

Throughout the project, I used the impact and urgency of each issue to determine an appropriate priority.

| Priority | Example                      | Reason                                             |
| -------- | ---------------------------- | -------------------------------------------------- |
| Critical | Department network outage    | Multiple users or major business services affected |
| High     | Important system unavailable | Significant impact on user productivity            |
| Normal   | Password reset               | Limited impact affecting an individual user        |
| Low      | General request              | No immediate impact on business operations         |

---

# Service Level Agreements

The SLA plans configured during the previous section were used to establish different response expectations.

| SLA   | Severity | Example                     |
| ----- | -------- | --------------------------- |
| Sev-A | Critical | Major outage                |
| Sev-B | High     | Significant business impact |
| Sev-C | Normal   | Standard support issue      |

Using different SLAs helped demonstrate how ticketing systems can organize support work based on urgency and business impact.

---

# Ticket Escalation

Not every issue should remain with the original technician.

During the lab, tickets could be escalated when:

* The issue exceeded Tier 1 troubleshooting capabilities
* Multiple users were affected
* Specialized technical knowledge was required
* The issue involved network or system infrastructure
* The ticket required a different department

Before escalation, I documented the troubleshooting steps already completed so the next technician would have the information needed to continue working the issue.

---

# Documentation Practices

Throughout the ticket lifecycle, I practiced documenting:

* The user's reported issue
* Initial observations
* Troubleshooting steps
* Changes made
* Ticket priority
* Assigned SLA
* Escalation decisions
* User communication
* Final resolution

Clear documentation helps prevent repeated troubleshooting and allows another technician to quickly understand the history of a support request.

---

# Ticket Lifecycle Complete

This portion of the project demonstrated how an IT help desk uses a ticketing system to manage support requests from beginning to end.

The complete workflow included:

```text
Issue Reported
      ↓
Ticket Created
      ↓
Impact Assessed
      ↓
Priority Selected
      ↓
SLA Applied
      ↓
Ticket Assigned
      ↓
Troubleshooting
      ↓
Escalation if Required
      ↓
Resolution Documented
      ↓
User Confirms Solution
      ↓
Ticket Closed
```

---

## Skills Demonstrated

* Help Desk Support
* Ticket Management
* Troubleshooting
* Incident Prioritization
* SLA Management
* Ticket Escalation
* Technical Documentation
* End-User Communication
* Incident Resolution
* Service Request Management

---

## What I Learned

This project gave me hands-on experience with the complete lifecycle of help desk tickets.

I learned that effective IT support involves more than solving technical problems. Support technicians must also properly prioritize incidents, communicate with users, document their work, understand when to escalate an issue, and confirm that the user is satisfied before closing a ticket.

Using osTicket helped me understand how ticketing systems provide structure and accountability throughout the support process.

---

## Project Complete

This completes all three sections of the osTicket Help Desk Lab:

### [Part 1 — Installation](01-installation.md)

### [Part 2 — Post-Installation Configuration](02-configuration.md)

### Part 3 — Ticket Lifecycle

Return to the main project page:

### [🏠 osTicket Help Desk Lab](README.md)

---

[← Previous: Post-Installation Configuration](02-configuration.md) | [🏠 Main Project](README.md)
