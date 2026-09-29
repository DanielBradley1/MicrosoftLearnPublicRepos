<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/manage-generic-case-tasks -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Manage case tasks in the Microsoft Defender portal

Use tasks in the Microsoft Defender portal to break case work into actionable items, assign ownership, track progress, and document outcomes.

Tasks are available for supported case types, including incident cases and generic cases. Use tasks to coordinate investigation, response, remediation, handoff, and review work across your security operations team.

For an overview of case management, see [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management).

## How tasks work

Tasks help analysts organize case work into smaller steps. Each task can include details such as status, priority, assigned user, due date, description, and closing notes.

Using tasks is useful for:

- Assigning investigation or response actions to specific analysts
- Tracking work across shifts or teams
- Onboarding junior analysts
- Working with managed security service providers
- Documenting investigation outcomes
- Supporting post-incident review and audit requirements

When you close a task, add closing notes to document what was done and what the outcome was.

## Prerequisites

Before you begin, make sure that you have one of the following Microsoft Defender unified RBAC permissions:

- To view generic case tasks: **Security data basics \(read\)** in the **Security operations** group.
- To create and manage generic case tasks: **Alerts \(manage\)** in the **Security operations** group.

For more information, see [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## View tasks

To view tasks for a case:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Generic**
4. Select **Tasks**.

   ![Screenshot showing the Case tasks pane for a generic case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/manage-generic-case-tasks/manage-generic-case-tasks-view-tasks.png)

## Create a task

To create a task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Generic**.
4. Select **Tasks**.
5. Select **Add task**.
6. Enter a name for your task.

   ![Screenshot showing the Add task pane for a generic case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/manage-generic-case-tasks/manage-generic-case-tasks-add-task.png)
7. Select a task status.
8. Select a task priority.
9. Select a task due date and due time.
10. Select a category for your task.
11. Add a description for your task.
12. If you are closing your task, fill out the **Closing notes** field.
13. Select **Save**.

## Update a task

To update a task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Generic**
4. Open the case that contains the task you want to update.
5. Select **Tasks**.
6. Select the task you want to update.
7. Select the edit icon.
8. Update the task details.
9. Select **Save**.

## Close a task

To close a task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Generic**
4. Open the case that contains the task you want to close.
5. Select **Tasks**.
6. Select the task you want to close.
7. Change the task status to **Closed**.
8. Add closing notes to document the outcome.
9. Select **Save**.

## Delete a task

Delete a task only when you're sure it isn't needed.

To delete a task:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Generic**
4. Open the case that contains the task you want to delete.
5. Select **Tasks**.
6. Select the task you want to delete.
7. Select the delete icon.
8. Select **Yes** to confirm.

## Automate and synchronize tasks created in Microsoft Sentinel

When you onboard Microsoft Sentinel to the Defender portal, the Defender portal can synchronize incident tasks that were created in Microsoft Sentinel in the Azure portal.

Important

Synchronization is one-way. Tasks created in the Defender portal aren't synchronized back to Microsoft Sentinel in the Azure portal.

The Defender portal doesn't currently support automatic task creation. You can continue to use Microsoft Sentinel task automation rules, Logic App playbooks, or the Incident Tasks REST API in Azure to create tasks for Microsoft Sentinel incidents. These tasks are synchronized to the Defender portal.

## Related content

- [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management)
- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Manage generic cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-cases)
- [Plan an incident response workflow in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/plan-incident-response)
