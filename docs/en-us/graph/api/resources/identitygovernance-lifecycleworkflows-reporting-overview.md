<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-reporting-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# Lifecycle Workflow reporting API Overview

Lifecycle Workflows offers reports that enable organizations to gain insight into how lifecycle workflows were processed for users in your organization.

Note

This article describes how to export personal data from a device or service. These steps can be used to support your obligations under the General Data Protection Regulation \(GDPR\). Authorized tenant admins can use Microsoft Graph to correct, update, or delete identifiable information about end users, including customer and employee user profiles or personal data, such as a user's name, work title, address, or phone number, in your [Microsoft Entra ID](https://www.microsoft.com/security/business/identity-access/microsoft-entra-id) environment.

The lifecycle workflows API is defined in the OData subnamespace, microsoft.graph.identityGovernance.

## Key elements of Lifecycle Workflows reports

| Reporting feature | Description |
| --- | --- |
| [User processing result](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) | Result of a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) that was executed for a specific user. The result is an aggregation of all [task processing results](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) of the [workflow tasks](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) that were part of the lifecycle workflow and executed for the specific user. |
| [Task processing result](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) | Result of a [workflow task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) that was executed for a specific user. |
| [Workflow run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) | Result of a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) that was executed for a collection of users. The result is an aggregation of all [user processing results](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) of the users that were either processed within an [interval](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0#properties) or were part of an [on-demand execution](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activate?view=graph-rest-1.0). |
| [Task report](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0) | An aggregation of [task processing results](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) for a specific [workflow task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) within a [workflow run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0). With this report, the health status of a workflow task within a workflow run can be easily determined and thus the source of error can be identified more quickly should a workflow run fail. |

## Lifecycle workflows in audit logs

*All* events run in Lifecycle Workflows are logged by Microsoft Entra ID. These include creating, updating, deleting, or running workflows, and assigning permissions to apps.

These auditable logs are represented by the [directoryAudit resource type](https://learn.microsoft.com/en-us/graph/api/resources/directoryaudit) and its associated GET methods in Microsoft Graph.

## License checks

The Lifecycle Workflows feature, including the API, is included in the Microsoft Entra ID P2 license. The tenant where Lifecycle Workflows are being created must have a valid purchased, or trial, Microsoft Entra ID P2 or EMS E5 subscription. For more information about the license requirements, see [Lifecycle Workflows license requirements](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflows-deployment#licenses).

## Role and application permission authorization checks

The following [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) are required for a calling user to read reports in Lifecycle Workflows.

| Operation | Application permissions | Required directory role of the calling user |
| :--- | :--- | :--- |
| Read | LifecycleWorkflows.Read.All or LifecycleWorkflows.ReadWrite.All | Global Reader or Lifecycle Workflows Administrator |
| Create, Update or Delete | LifecycleWorkflows.ReadWrite.All | Lifecycle Workflows Administrator |

## Related content

- [What are Lifecycle Workflows?](https://learn.microsoft.com/en-us/azure/active-directory/governance/what-are-lifecycle-workflows)
- [Overview of Lifecycle Workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-overview?view=graph-rest-1.0)
