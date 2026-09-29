<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/manage-incident-case-tasks -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Manage incident case tasks in the Microsoft Defender portal \(preview\)

Use tasks in the Microsoft Defender portal to break incident response work into actionable items, assign ownership, track progress, and document outcomes.

Incident case tasks help security operations teams coordinate investigation, response, remediation, handoff, and review work for incident cases.

Note

Incident cases are in preview and are the recommended experience for managing incidents in the Microsoft Defender portal. The legacy incident experience remains available during this preview.

For an overview of case management, see [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management).

## How incident case tasks work

Tasks help analysts organize incident response work into smaller steps. Each task can include details such as status, priority, assigned user, due date, description, and closing notes.

Using tasks is useful for:

- Assigning investigation or response actions to specific analysts
- Tracking work across shifts or teams
- Coordinating handoff between analysts
- Onboarding junior analysts
- Working with managed security service providers
- Documenting investigation outcomes
- Supporting post-incident review and audit requirements

When you close a task, add closing notes to document what was done and what the outcome was.

## Prerequisites

Before you begin, make sure you have one of the following Microsoft Defender unified RBAC permissions:

- To view incident case tasks: **Read-only** or **Security data basics \(read\)** in the **Security operations** group.
- To create and manage incident case tasks: **All read and manage permissions** or **Response \(manage\)** in the **Security operations** group.

For more information, see [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## View incident case tasks

To view tasks for an incident case:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Tasks**.

From **Tasks**, you can view task status, add tasks, edit existing tasks, or delete tasks.

## Create an incident case task

To create a task for an incident case:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Tasks**.
6. Select **Add task**.
7. Enter a name for your task.

   ![Screenshot showing the Add task pane for an incident case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/manage-incident-case-tasks/create-incident-case-task.png)
8. Select a task status.
9. Select a task priority.
10. Assign the task to a user, if needed.
11. Select a due date and due time, if needed.
12. Add a description for the task.
13. If you're closing the task, add closing notes to document the outcome.
14. Select **Save**.

## Update an incident case task

To update an incident case task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Tasks**.
6. Select the edit icon for the task you want to update.
7. Update the task details.
8. Select **Save**.

## Change task status

To change the status of an incident case task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Tasks**.
6. Select the task status.
7. Select the new status.

The task status is updated in **Tasks**.

## Close an incident case task

To close an incident case task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Tasks**.
6. Select the edit icon for the task you want to close.
7. Change the task status to **Closed**.
8. Add closing notes to document the outcome.
9. Select **Save**.

## Delete an incident case task

Delete a task only when you're sure it isn't needed.

To delete an incident case task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Tasks**.
6. Select the delete icon for the task you want to delete.
7. Select **Yes** to confirm.

## Related content

- [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management)
- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Manage generic cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-cases)
- [Manage generic case tasks in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-generic-case-tasks)
- [Plan an incident response workflow in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/plan-incident-response)
