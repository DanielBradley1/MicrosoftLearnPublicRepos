<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-assign-a-baseline?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Assign a baseline in Microsoft 365 Lighthouse

By default, Microsoft 365 Lighthouse assigns the default baseline to all tenants. You can create and assign a baseline to accommodate varying customer requirements.

## Before you begin

Make sure you and your customer tenants meet the requirements listed in [Requirements for Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-requirements?view=o365-worldwide).

Additionally, each partner tenant user must hold the Administrator role in Lighthouse.

## Assign a baseline to one or more tenants

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Tenants**.
2. Select the checkbox next to the tenants to which you want to assign a new baseline, and then select **Assign baseline** at the top of the table.
3. Select the baseline you want to assign to the selected tenants.

Note

Baselines don't include tenant-specific attributes, and the assignment of a new baseline overwrites any pre-existing customization to the configuration of a tenant's deployment plan, such as deployment task dismissals, user and user group exclusions, and deployment statuses of manual deployment tasks. These values need to be re-entered for each tenant, as needed.

## Next steps

Once the baseline is assigned, Lighthouse queries the assigned tenants to detect and report their deployment status. [Review the deployment plan](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-review-deployment-plan?view=o365-worldwide) to determine the next steps in the deployment process.

## Related content

[Create baselines](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-create-a-baseline?view=o365-worldwide) \(article\)  
[Overview of using Microsoft 365 Lighthouse baselines to deploy standard tenant configurations](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-deploy-standard-tenant-configurations-overview?view=o365-worldwide) \(article\)  
[Overview of permissions in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-overview-of-permissions?view=o365-worldwide) \(article\)  
[Microsoft 365 Lighthouse FAQ](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-faq?view=o365-worldwide) \(article\)
