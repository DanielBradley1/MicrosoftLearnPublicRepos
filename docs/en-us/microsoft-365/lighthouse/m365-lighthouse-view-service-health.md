<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-view-service-health?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# View tenant service health in Microsoft 365 Lighthouse

You can view service health for the tenants you manage in Microsoft 365 Lighthouse. Service health includes incidents and advisories for several services, including Microsoft Intune, Microsoft Entra identity services, and mobile device management \(MDM\) cloud services. You can also see how many of your managed tenants are affected by incidents. For example, if one of your tenants is experiencing problems, you can check the Service health page to determine whether it's a known issue with a resolution in progress or whether a recent change might be impacting them. Checking service health could save you time troubleshooting and reduce support calls.

If you can't sign in to Lighthouse, you can use the [Microsoft Service Health Status](https://status.cloud.microsoft/) page to check for known issues preventing you from logging in to your partner tenant. Also, sign up to follow [@MSFT365status](https://twitter.com/MSFT365Status) on Twitter to see information on specific service incidents.

## Before you begin

To view service health, you must have at least one Microsoft Entra role in the partner tenant with the following property set: **microsoft.office365.serviceHealth/allEntities/allTasks**. For a list of Microsoft Entra roles, see [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/azure/active-directory/roles/permissions-reference).

## View service health status and issue details

1. In the left navigation pane in [Lighthouse](https://go.microsoft.com/fwlink/p/?linkid=2168110), select **Service health**.
2. At the top of the page, review the current service health status of all your tenants:

   - Total number of incidents
   - Total number of advisories affecting any of the managed tenants
   - Number of services with active incidents

3. To review issues by service, select the **All services** tab. To review all current issues, select the **All issues** tab.
4. Select an issue from the list to open the issue details pane.
5. Select the **Overview** tab to view information including issue type, status, user impact, and issue history.
6. Select the **Tenants affected** tab to see a list of tenants affected by the issue. From here, you can export a list of affected tenants to a comma-separated values \(.csv\) file so you can share it with your support teams.

## Related content

[How to check Microsoft 365 service health](https://learn.microsoft.com/en-us/microsoft-365/enterprise/view-service-health) \(article\)  
[Known issues with Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-known-issues?view=o365-worldwide) \(article\)  
[View your Microsoft Entra roles in Microsoft 365 Lighthouse](https://learn.microsoft.com/en-us/microsoft-365/lighthouse/m365-lighthouse-view-your-roles?view=o365-worldwide) \(article\)
