<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/applications-inventory -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Applications inventory

Protecting your SaaS ecosystem requires taking inventory of all SaaS and connected OAuth apps that are in your environment. With the increasing number of applications, having a comprehensive inventory is crucial to ensure security and compliance. The Applications page provides a centralized view of all SaaS and connected OAuth apps in your organization, enabling efficient monitoring and management.

At a glance, you can see information such as app name, risk score, privilege level, publisher information, and other details for easy identification of SaaS and OAuth apps most at risk.

The Applications page includes the following tabs:

- SaaS apps: A consolidated view of all SaaS applications in your network. This tab highlights key details, including app name, status \(unprotected/protected app\) and whether the app is marked as sanctioned or unsanctioned.
- OAuth apps: A comprehensive view of OAuth apps registered on Microsoft Entra ID, Google Workspace, and Salesforce. This tab highlights OAuth app metadata, publisher information, app origin, permissions used, data accessed, and other insights.

## Navigate to the Applications page

In the Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Assets** > **Applications**. Or, go directly to the **Applications** page, by clicking on the banner links on the existing Cloud discovery and App governance pages.

[![Screenshot of the Cloud Discovery page with a banner about the new unified application inventory experience.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/banner-on-cloud-discovery-pages.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/banner-on-cloud-discovery-pages.png#lightbox)

[![Screenshot of the App Governance page with a banner about the new unified application inventory experience for managing OAuth and SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/media/banner-message-on-app-governance-pages.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/banner-message-on-app-governance-pages.png#lightbox)

There are several options you can choose from to customize the SaaS apps and OAuth apps list view. In the top navigation panel you can:

- Add or remove columns.
- Export the entire list in CSV format.
- Select the number of items to show per page.
- Apply filters.

Note

When exporting the applications list to a CSV file, a maximum of 1000 SaaS or OAuth apps are displayed.

The following image depicts the SaaS apps list:  [![Screenshot of the applications tab in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/applications-tab-in-the-defender-portal.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/applications-tab-in-the-defender-portal.png#lightbox)

## SaaS app details

At the top of the SaaS apps tab, you can find actionable insights that allow you to quickly identify apps that need your attention. The following details are displayed:

- **Untagged high-risk apps** - Shows apps that aren't tagged and have a high risk score.
- **Untagged high-traffic apps** - Shows apps that aren't tagged and have high usage traffic \(greater than 1 GB of data traffic\).
- **Untagged GenAI apps** - Shows apps that aren't tagged and are based on generative AI.

## Sort and filter the SaaS apps list

Use sorting and filtering to focus the SaaS apps list on the applications you want to assess and manage. For filter descriptions and query options, see [Filter and query discovered apps](https://learn.microsoft.com/en-us/defender-cloud-apps/discovered-app-queries#discovered-app-filters).

## OAuth app details

The OAuth apps tab provides visibility into OAuth apps from Microsoft Entra ID, Salesforce, and Google Workspace. Admins can review applications and decide to disable the apps or apply policies to monitor their behavior in their environment.

The OAuth app inventory includes the following app types:

- **Entra ID**: Service principals registered in Microsoft Entra ID. These apps access resources through API permissions or Microsoft Entra role assignments.
- **Salesforce**: OAuth apps connected through Salesforce. The inventory includes both Connected Apps and External Client Apps \(ECAs\).
- **Google Workspace**: OAuth apps connected through Google Workspace. Users authorize these apps, which have varying levels of access to Google Workspace resources.

Actionable insights appear at the top of the OAuth apps tab. Select an insight to filter the list to the matching apps so you can quickly identify apps that need review.

| Insight | Description | Available for |
| --- | --- | --- |
| **New apps** | Apps added in the last 30 days. | Microsoft 365 |
| **Highly privileged apps** | Apps with powerful permissions that allow them to access data or change important settings. For Salesforce, includes Connected Apps and External Client Apps \(ECAs\) whose granted permissions are classified as **High**. | Microsoft 365, Google Workspace, Salesforce |
| **Risky apps** | Apps with a high risk score. | Microsoft 365, Google Workspace, Salesforce |
| **Unused apps** | Apps that haven't signed in within the last 90 days. For Salesforce, includes Connected Apps and ECAs that haven't been used for more than 90 days based on the last used date. | Microsoft 365, Google Workspace, Salesforce |
| **Overprivileged apps** | Apps with unused permissions. | Microsoft 365 |
| **Apps from external unverified publishers** | Apps that originated from an external unverified publisher tenant. | Microsoft 365 |
| **Used by AI Agents** | Apps identified as being used by AI agent platforms. | Microsoft 365 |

For more information on how to create app policies, see [Create app policies in app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create).

The following image shows the OAuth apps list:

[![Screenshot of the OAuth apps inventory showing Entra ID, Salesforce, and Google Workspace app types.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/oauth-tab-in-the-applications-page.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/oauth-tab-in-the-applications-page.png#lightbox)

## Sort and filter the OAuth apps list

Use sorting and filtering to focus the OAuth apps list on the applications you want to investigate. For the available columns and filters, see [View your OAuth app details with app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps#view-the-apps-in-your-tenant) and [View app insights](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-overview#view-app-insights).

## Next steps

[Best practices for protecting your organization](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices)

## Related content

- [View the Identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory)
- [Investigate a non-human identity](https://learn.microsoft.com/en-us/defender-xdr/investigate-non-human-identities)
- [View your app details with app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps)
- [Create app policies in app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
