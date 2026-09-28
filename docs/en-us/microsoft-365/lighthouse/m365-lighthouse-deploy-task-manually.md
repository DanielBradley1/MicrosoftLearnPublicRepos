<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-task-manually?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-08-11 -->

# Deploy a task manually in Microsoft 365 Lighthouse

Tasks that require configurations that can't be deployed automatically through Microsoft 365 Lighthouse require manual deployment. Once the manual deployment is complete, set the task status to **Compliant** to reflect the current state of the task.

## Before you begin

Make sure you and your customer tenants meet the requirements listed in [Requirements for Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-requirements?view=o365-worldwide).

Additionally, each partner tenant user must meet the following requirements:

- The partner tenant user must have DAP/GDAP access to the applicable tenant.

  - For DAP, the partner tenant user must be a member of the admin agent group.
  - For GDAP, the partner tenant user must be a member of a security group that has been granted GDAP permissions to the applicable workload associated with the task.

- The partner tenant user must enable MFA for their user account in the partner tenant.

## Deploy a task manually

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Tenants**.
2. From the tenant list, select the tenant you want to view.
3. Select the **Deployment Plan** tab.
4. From the task list, select the task you want to deploy manually.
5. From the task details pane, select **Mark as compliant**.
6. In the confirmation dialog box, type your name as it appears within Lighthouse.
7. Select **Save**.

The task status will be updated to **Compliant**, and the Task Details pane will reflect which Lighthouse user completed the implementation steps.

If the task status changes and is no longer compliant, you can reset the status to **Not compliant**. To do this:

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Tenants**.
2. From the tenant list, select the tenant you want to view.
3. Select the **Deployment Plan** tab.
4. From the task list, select the task you want to update.
5. In the task details pane, select **Mark as not compliant**.
6. In the **Mark task as not compliant** dialog box, select **Save**.

Tasks that must be deployed manually can also be dismissed regardless of their deployment status. Tasks that have been dismissed after being set as **Compliant**, will revert to **Not compliant** when reinstated.

## Related content

[Deploy a task automatically](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-task-automatically?view=o365-worldwide) \(article\)  
[Dismiss a task](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-dismiss-task?view=o365-worldwide) \(article\)  
[Reinstate a task](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-reinstate-task?view=o365-worldwide) \(article\)  
[Overview of deployment tasks in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-deployment-task?view=o365-worldwide) \(article\)  
[Overview of using Microsoft 365 Lighthouse baselines to deploy standard tenant configurations](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-standard-tenant-configurations-overview?view=o365-worldwide) \(article\)  
[Overview of permissions in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-of-permissions?view=o365-worldwide) \(article\)  
[Configure Microsoft 365 Lighthouse portal security](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-configure-portal-security?view=o365-worldwide) \(article\)  
[Microsoft 365 Lighthouse FAQ](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-faq?view=o365-worldwide) \(article\)
