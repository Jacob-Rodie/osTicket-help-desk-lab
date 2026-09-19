# Part 2 — Post-Installation Configuration

[← Previous: Installation](01-installation.md) | [🏠 Main Project](README.md) | [Next: Ticket Lifecycle →](03-ticket-lifecycle.md)

After completing the osTicket installation, I configured the system into a basic internal help desk environment. This section set up the users, agents, roles, departments, teams, SLAs, and help topics needed to support realistic ticket handling.

This configuration prepares the environment for the next part of the project, where users will submit tickets, support agents will review them, tickets will be escalated when needed, and tickets will move through the lifecycle to resolution.

User Access and Authentication

The first area I configured was user access. I configured the system so users must register before creating tickets. I also set registration to private, meaning agents add users instead of allowing anyone to register publicly.

This matters because an internal help desk usually supports known employees or approved users. Private registration helps keep the user directory controlled and prevents random or duplicate accounts.



Roles and Permissions

Next, I reviewed the role structure and added a Master Admin role. Roles control what staff members can do inside osTicket, such as managing tickets, assigning work, editing ticket details, or performing administrative tasks.

This is important because not every support agent should have the same level of access. A help desk should separate administrative access from regular ticket support access so agents have only the permissions they need for their responsibilities.



Departments

I configured a System Administrators department to represent a higher-level technical support group. In a real support environment, this type of department would handle issues that require elevated access, deeper troubleshooting, or escalation beyond frontline support.

Departments help organize ticket ownership. They make it easier to decide which group should own a ticket based on the type of issue being reported.



Teams

I also added a Level II Support team. Teams are useful because they let you assign tickets to a support group instead of only a department or individual agent.

For this project, Level I support represents the first point of contact for common user issues. Level II support represents the escalation path when a ticket needs more advanced troubleshooting.



Agents

I created support agents so the ticket lifecycle can show how work moves through the help desk. Daniel Brooks is set up as a support agent, and Sophie Mitchell is associated with the System Administrators department.

This creates a simple but realistic support structure. A user can submit a ticket, Level I support can review it, and the ticket can be escalated to a higher-level agent or department if needed.



Service Level Agreements

I configured a Sev-A SLA plan with a one-hour grace period and a 24/7 schedule. This SLA is meant for urgent issues that need fast attention.

SLAs are important in a help desk because they help prioritize tickets based on urgency and business impact. Instead of treating every request the same way, the help desk can respond faster to issues that affect important systems or multiple users.



Help Topics

I added a Business Critical Outage help topic. Help topics categorize incoming tickets and help route them to the right support group.

This topic is useful for demonstrating a high-priority ticket scenario. In the next section, it can show how osTicket handles ticket classification, urgency, assignment, escalation, and resolution.



How This Supports the Ticket Lifecycle

These configuration steps create the foundation for realistic help desk work. Registered users can submit tickets, agents can manage tickets from the agent panel, departments and teams provide routing options, and SLAs/help topics help define ticket priority.

The next part of the project will use this setup to demonstrate the full ticket lifecycle, including ticket creation, assignment, communication, escalation, and resolution.
