<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-deployment-task?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-06-21 -->

# Overview of deployment tasks in Microsoft 365 Lighthouse

A tenant's deployment plan is complete when all tasks are compliant or explicitly dismissed. Microsoft 365 Lighthouse assesses each task based on the following factors:

| Factor | Description |
| --- | --- |
| Is the tenant licensed for the required services associated with the task? | - Tasks that aren't licensed won't be eligible for deployment.<br>- Tasks that aren't licensed may be **Dismissed**.<br>- Once Lighthouse detects that the tenant is licensed for the required services associated with the task, the status will be updated automatically. |
| Is the task related to other tasks? | - Tasks related to other tasks must be completed in sequential order.<br>- Subsequent tasks will be eligible for deployment once the pre-requisite tasks are **Compliant**. |
| Can the configuration associated with the task be deployed through Lighthouse? | - Tasks that require configurations that can't be deployed through Lighthouse will require manual implementation.<br>- Lighthouse can't deploy tasks when it can't detect any existing configuration. |
| Was the task dismissed? | - Dismissed tasks aren't eligible for deployment.<br>- Dismissed tasks can be **Reinstated**.<br>- Once a task is **Reinstated**, the status will be updated automatically. |
| Is the task compliant? | - Compliant tasks require no further action, but users may review task details and existing configurations. |

## Related content

[Deploy a task automatically](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-task-automatically?view=o365-worldwide) \(article\)  
[Deploy a task manually](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-task-manually?view=o365-worldwide) \(article\)  
[View task details](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-view-task-details?view=o365-worldwide) \(article\)  
[Dismiss a task](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-dismiss-task?view=o365-worldwide) \(article\)  
[Reinstate a task](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-reinstate-task?view=o365-worldwide) \(article\)  
[Overview of using Microsoft 365 Lighthouse baselines to deploy standard tenant configurations](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-standard-tenant-configurations-overview?view=o365-worldwide) \(article\)  
[Overview of permissions in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-of-permissions?view=o365-worldwide) \(article\)  
[Configure Microsoft 365 Lighthouse portal security](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-configure-portal-security?view=o365-worldwide) \(article\)  
[Microsoft 365 Lighthouse FAQ](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-faq?view=o365-worldwide) \(article\)
