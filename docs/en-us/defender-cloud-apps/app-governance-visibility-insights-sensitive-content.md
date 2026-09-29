<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-sensitive-content -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# View and regulate OAuth app access to sensitive content

App governance lets you quickly identify the Microsoft 365 services apps have accessed and if these apps have accessed content with sensitivity labels. This article explains how to view app access details, review sensitivity label exposure across services like SharePoint, OneDrive, and Exchange Online, and set up policies to regulate access to sensitive content.

## View apps that access sensitive content

To view apps that have accessed data across Microsoft 365 services, select **View apps** from the relevant card on the **Overview** tab. For example

![Screenshot of the Apps that accessed Microsoft Entra services card.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-sensitive-content/image7.png)

You can also select a label listed under **Sensitivity labels access** on any app tab, such as the **Microsoft Entra apps** tab. App governance then shows how many times the app accessed that label in the last 30 days for each service type. For example:

![Screenshot of the Sensitivity labels tab on the Microsoft Entra apps tab.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-sensitive-content/sensitive-labels-details.png)

In this example, the app accessed *Highly confidential* content seven times on SharePoint, 15 times on OneDrive, and 25 times on Exchange Online in the last 30 days.

## Regulate access to sensitive content

The built-in **Access to sensitive data** policy sends alerts when an app accesses sensitive content.

You can change this policy to:

- Select **Disable app** as the action so that apps that trigger alerts are turned off.
- Change the policy scope to include or exclude specific apps.

For more options, create a custom policy. Use the **Sensitivity labels accessed** condition with other [custom policy conditions](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create#custom-policies).

## Next step

[Get detailed insights on a specific app](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps).
