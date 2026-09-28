<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-understand-deployment-statuses?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-09-27 -->

# Understand deployment statuses in Microsoft 365 Lighthouse

When a tenant's onboarding status becomes **Active** or when you access a tenant within Microsoft 365 Lighthouse, Lighthouse queries the tenant for existing configurations. The deployment status is assigned to each task based on the status of each setting included in the subtask and, where applicable, for each user to which the subtask is assigned.

Lighthouse automatically determines deployment statuses when detection is possible. When detection isn't possible, Lighthouse relies on the status you manually set.

Tasks can have the following statuses:

| Task Status | Description |
| --- | --- |
| Compliant | - All settings included in the subtask are **Compliant**.<br>- There are no settings that are **Not compliant**.<br>- There are no settings that are **Missing** from all existing configurations. A task can be **Compliant** if a setting is **Compliant** in one or more existing configurations without being **Not compliant** in another.<br>- There may be **Extra** settings detected within existing configurations. |
| Not compliant | - One or more settings included in the subtask are **Not compliant**.<br>- One or more settings are **Missing** from all existing configurations.<br>- There may be **Extra** settings detected within existing configurations. |
| Not licensed | The tenant isn't licensed for the services required to deploy the configuration associated with the subtask. |
| Dismissed | The subtask was dismissed by a Lighthouse user.<br><br>**Note:** A Lighthouse user can dismiss **Not licensed** subtasks. |

Lighthouse will stop detecting or reporting deployment status for subtasks that have been dismissed.

To determine the status of each subtask, Lighthouse detects the status of each setting included in the subtask.

Settings can be assigned the following statuses:

| Setting Status | Description |
| --- | --- |
| Compliant | The value detected in the existing configuration deployed to the customer tenant is equivalent to the value in the deployment plan for all targeted users. |
| Not compliant | The value detected in the existing configuration deployed to the customer tenant isn't equivalent to the value in the deployment plan for one or more targeted users. |
| Missing | There's no value detected in the tenant for a setting that is included in the deployment plan. |
| Extra | There's a value detected in the tenant for a setting that isn't included in the deployment plan. |

Where applicable, Lighthouse detects the status of each user for the applicable subtask.

Users can be assigned the following statuses:

| User Status | Description |
| --- | --- |
| Compliant | - The user is targeted for the subtask.<br>- The user has been assigned licenses for all services required by the subtask.<br>- All settings included in the subtask are **Compliant**.<br>- There are no settings that are **Not compliant**.<br>- There are no settings that are **Missing** from all existing configurations. A user can be **Compliant** if a setting is **Compliant** in one or more existing configurations without being **Not compliant** in another.<br>- There may be **Extra** settings detected within existing configurations. |
| Not compliant | - The user is targeted for the subtask.<br>- The user has been assigned licenses for all services required by the subtask.<br>- One or more settings included in the subtask are **Not compliant**.<br>- One or more settings are **Missing** from all existing configurations.<br>- There may be **Extra** settings detected within existing configurations. |
| Excluded | The user has been excluded from the subtask.<br><br>**Note:** When a user is **Excluded** from a subtask, status detection and reporting will be updated accordingly, but existing configurations won't be affected. |
| Not licensed | The user isn't licensed for the services required to deploy the prescribed configuration.<br><br>**Note:** Doesn't apply to users with **Not targeted** status. |
| Not targeted | The user isn't the intended target for the subtask. For example, a user that isn't an admin is reported as **Not targeted** for a subtask that is assigned only to admins. |

## Related content

[Overview of deployment tasks in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-deployment-task?view=o365-worldwide) \(article\)  
[Overview of using Microsoft 365 Lighthouse baselines to deploy standard tenant configurations](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-standard-tenant-configurations-overview?view=o365-worldwide) \(article\)  
[Overview of permissions in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-of-permissions?view=o365-worldwide) \(article\)  
[Configure Microsoft 365 Lighthouse portal security](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-configure-portal-security?view=o365-worldwide) \(article\)  
[Microsoft 365 Lighthouse FAQ](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-faq?view=o365-worldwide) \(article\)
