<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-secure-apps-access-non-graph-api -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Secure OAuth apps accessing non-Graph APIs using app governance

## Overview

Many apps use APIs other than Microsoft Graph to access Microsoft 365 and other resources. With visibility over such apps, you can identify and defend against risks inherent to these apps, including the APIs that the apps access. Some non-Microsoft Graph APIs might receive limited support and updates.

App governance provides visibility over OAuth apps registered on Microsoft Entra ID, regardless of whether they access Graph API or other APIs. Additionally, you can monitor these apps and automatically take action if the apps are noncompliant or exhibit suspicious behavior.

You can better protect your organization with the new functionalities and enhancements in the following ways:

- Get improved coverage of OAuth apps with powerful app governance insights and monitoring capabilities.
- Automatically get alerted for any threats or anomalies from apps using non-Graph or legacy APIs.
- Get an enhanced experience for investigation of apps with more filters, columns, and properties.

## Identify apps that use non-Graph APIs

To view Microsoft 365 apps that access non-Graph APIs:

1. Go to **Settings** > **Cloud apps** > **[Apps governance](https://security.microsoft.com/cloudapps/app-governance?viewid=allApps)** in the [Microsoft Defender portal](https://security.microsoft.com).
2. Select the **Microsoft 365** tab
3. Open the **API access** filter
4. Select one of the options:

   - Office 365 Exchange Online
   - Office 365 SharePoint Online
   - Windows Azure Active Directory
   - Other APIs

5. Select **Apply**.

[![Screenshot that shows the list of APIs plus the option to view other APIs.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-secure-apps-access-non-graph-api/other-apis-app-governance.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-secure-apps-access-non-graph-api/other-apis-app-governance.png#lightbox)

## View APIs used by an app

The **Permissions** tab in the app details pane lists all permissions granted to an app, including both Graph API and non-Graph API permissions. To view the APIs that an app uses:

1. In the App governance page, select the app you want to investigate.
2. In the app details pane, select the **Permissions** tab.

[![Screenshot that shows the list of APIs and their assigned permissions.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-secure-apps-access-non-graph-api/other-apis-permissions.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-secure-apps-access-non-graph-api/other-apis-permissions.png#lightbox)

## Create policies for apps accessing non-graph APIs

You can create app governance policies to monitor and take action on apps that access non-Graph APIs. To create a custom policy or use an existing template, follow these steps:

1. In the App governance page, select the **Policies** tab.
2. Select **+ Create policy**.
3. To create a custom policy, select **Custom policy** and then configure the policy settings as needed. Select the **Non-Graph API permissions** policy condition to identify and monitor apps that access non-Graph APIs.

   ![Screenshot that shows the option to create a custom policy.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-secure-apps-access-non-graph-api/choose-policy-template.png)
4. To use a template, select **usage** and then the template **New app with Non-Graph API permissions**.

   ![Screenshot that shows the option to use a template for a new policy.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-secure-apps-access-non-graph-api/new-policy-non-graph-api.png)
5. Configure the policy settings as follows:

   - Give the policy a name and description
   - Set the severity level to low, medium, or high.
   - Set policy scope and conditions, you can choose to apply the default settings or customize the policy.
   - Choose an action you'd like to take on apps that match the conditions in this policy. For example, disabling the app.
   - Set the policy actions to active or disabled.

## Next steps

Learn more about managing and investigating apps with app governance:

- [Secure apps with app hygiene features](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-secure-apps-app-hygiene-features)
- [View your app details with app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps#get-detailed-information-about-an-app)
