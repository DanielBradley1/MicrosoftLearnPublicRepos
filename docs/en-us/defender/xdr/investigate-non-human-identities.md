<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/investigate-non-human-identities -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Non-human identities in Microsoft Defender

Non-human identities are accounts and applications that operate without direct human interaction. In Microsoft Defender, non-human identities include service principals registered in Microsoft Entra ID, Active Directory service accounts, and OAuth apps connected to Google Workspace and Salesforce. These identities often have elevated privileges and access to sensitive resources, which makes them a priority for security monitoring.

You can view and investigate non-human identities from the [Identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory) in the Microsoft Defender portal.

![Screenshot that shows the non-human identities page in the Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/investigate-non-human-identities/non-human-identities.png)

## Actionable insights

Actionable insights appear at the top of the non-human identities inventory. Select an insight to filter the list to identities that need review.

| Insight | Description | Available for |
| --- | --- | --- |
| **New identities** | Identities added in the last 30 days. | Microsoft 365 |
| **Highly privileged identities** | Identities with powerful permissions that allow them to access data or change important settings. For Salesforce, includes Connected Apps and External Client Apps \(ECAs\) whose granted permissions are classified as **High**. | Microsoft 365, Google Workspace, Salesforce |
| **Risky identities** | Identities with a high risk score. | Microsoft 365, Google Workspace, Salesforce |
| **Unused identities** | Identities that haven't signed in within the last 90 days. For Salesforce, includes Connected Apps and ECAs that haven't been used for more than 90 days based on the last used date. | Microsoft 365, Google Workspace, Salesforce |
| **Overprivileged identities** | Identities with unused permissions. | Microsoft 365 |
| **Identities from external unverified publishers** | Identities that originated from an external unverified publisher tenant. | Microsoft 365 |
| **Used by AI Agents** | Identities identified as being used by AI agent platforms. | Microsoft 365 |

## Types of non-human identities

Microsoft Defender organizes non-human identities into the following categories, each shown as a tab in the identity inventory:

- **Entra ID**: Service principals registered in Microsoft Entra ID. These apps authenticate using OAuth and access resources through Microsoft Graph and other APIs.
- **Active Directory**: Service accounts from on-premises Active Directory. These specialized accounts run applications, services, and automated tasks, and often have elevated privileges.
- **Google Workspace**: OAuth apps connected through Google Workspace. Users authorize these apps, which have varying levels of access to Google Workspace resources.
- **Salesforce**: OAuth apps connected through Salesforce. The inventory includes both Connected Apps and External Client Apps \(ECAs\).

## Investigate identity details

Each identity type shows different columns, filters, and detail tabs in the inventory. For information about inventory fields and identity details, see the following articles:

- **Entra ID, Google Workspace, and Salesforce OAuth apps**: For inventory columns, filtering options, and identity details, see [View your app details with app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps).
- **Active Directory service accounts**: For inventory columns, connections, and classification rules, see [Investigate and protect Service Accounts](https://learn.microsoft.com/en-us/defender-for-identity/service-account-discovery).

## Related content

- [View the identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory)
- [Investigate a human identity](https://learn.microsoft.com/en-us/defender-xdr/investigate-users)
- [Investigate and protect Service Accounts](https://learn.microsoft.com/en-us/defender-for-identity/service-account-discovery)
- [View your app details with app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps)
