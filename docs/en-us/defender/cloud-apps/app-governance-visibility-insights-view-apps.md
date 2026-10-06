<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# View your OAuth app details with app governance

Use app governance to gain visibility and meaningful insights on your app ecosystem.

For example, view a list of apps in your tenant, together with relevant app metadata and usage data. Select a specific app to open its details pane and view more data and insights.

## Prerequisites

Your sign-in account must have one of the [required app governance roles](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-get-started#roles) to view app governance data.

## View the apps in your tenant

For a summary of apps in your tenant, in Microsoft 365, go to **Cloud app > App governance** and select any of the apps tabs.

By default, the app governance page sorts the grid alphabetically, by **Display name**. To sort the list by another attribute, select the column name. You can also select **Search** to search for an app by name.

[![Screenshot of the Microsoft 365 apps tab on the App governance page.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-list-view.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-list-view.png#lightbox)

On the **Microsoft 365** tab, the apps in your tenant are listed with the following details:

| Column name | Description |
| --- | --- |
| **Display name** | The display name of the app as registered on Microsoft Entra ID |
| **Status** | Shows whether the app is enabled or disabled, and if disabled by whom |
| **Risk score** | Shows the identity risk score \(1-100\). Higher values indicate greater risk. |
| **Graph API access** | Shows whether the app has at least one Graph API permission |
| **Permission type** | Shows the app's permission type:<br><br>- **Delegated**: Delegated API permissions only, no roles.<br>- **Application**: Application API permissions only, no roles.<br>- **Microsoft Entra roles**: Microsoft Entra roles only, no API permissions.<br>- **Mixed**: A combination of any two or more of the above.<br>- **None**: No API permissions or Entra roles assigned. |
| **Origin** | Shows whether the app originated within the tenant or was registered in an external tenant |
| **Consent type** | Shows whether the app consent is given at the user or the admin level, and the number of users whose data is accessible to the app |
| **Publisher** | Publisher of the app and their verification status |
| **Last used** | Shows the last time when the app signed in. Tracking of this data goes back to June, 2022. |
| **Used by AI Agents \(Preview\)** | Shows the AI agents that use this identity to authenticate and access Microsoft 365 resources. If the value is **N/A**, agent details are unavailable, but the identity might still be used by AI agents. |
| **Last modified** | Date and time when registration information was last updated on Microsoft Entra ID |
| **Added on** | Shows the date and time when the app was registered to Microsoft Entra ID and assigned a service principal |
| **Permission usage** | Shows whether the app has any unused Graph API permissions in the last 90 days |
| **Data usage** | Total data downloaded or uploaded by the app in the last 30 days |
| **Privilege level** | The app's privilege level |
| **Certification** | Indicates if an app meets stringent security and compliance standards set by Microsoft 365 or if its publisher has publicly attested to its safety |
| **App ID** | The app ID |
| **Sensitivity label accessed** | Sensitivity labels on content accessed by the app |
| **Service accessed** | Microsoft 365 services accessed by the app |
| **Community use** | Shows how popular the app is among all your users \(*common*, *uncommon*, *rare*\) |
| **Consent grants** | Shows all app consent grants in the last 30 days |
| **App activities** | Shows all app activities in the last 30 days |

## Get detailed information about an app

Select a specific app in the grid to view more details on an app details pane. Some tabs are available only for specific app types.

Company administrators can use the **Disable app** and **Enable app** controls in the details pane to enable or disable an app.

### Review app details on the Summary tab

The **Summary** tab shows more data about the app, such as the date first consented and the App ID. To see the properties of the app as registered in Microsoft Entra ID, select **View in Microsoft Entra ID**.

[![Screenshot of an app details pane with the Summary tab showing.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-summary.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-summary.png#lightbox)

### Review risk details on the Risk score tab

The **Risk score** tab shows a 1-100 risk score for the app, where higher values mean greater risk. The risk score helps you quickly prioritize which apps need attention first. The **Risk score** tab also shows the risk summary, including the factors behind the app's risk score.

[![Screenshot of an app details pane with the Risk score tab showing.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-risk-score.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-risk-score.png#lightbox)

### Review app connections on the Graph tab

The **Graph** tab shows a visual identity graph that illustrates how the app connects to other entities in your organization, like users, resources, SaaS workloads, and critical assets. Select any node or edge in the graph to open a details pane with deeper context. When applicable, the graph details pane also shows attack paths involving the selected nodes or edges. To explore further, select **View in map** below the graph to open the full Attack Map experience in a new window.

The graph can also surface the AI agent behind an app. For OAuth apps tied to Microsoft Copilot Studio agents, expand the OAuth app node to view the connected agent.

Note

The Graph tab is available only for OAuth apps registered in Microsoft Entra ID.

[![Screenshot of an app details pane with the Graph tab showing.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-graph.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-graph.png#lightbox)

### Review app activity on the Data usage tab

The **Data usage** tab shows a graph of data usage over time, for Exchange, SharePoint, OneDrive, and Teams resources via Microsoft Graph and Exchange Web Services \(EWS\) APIs. The **Data usage** tab supports filtering usage insights by priority accounts only.

[![Screenshot of the Data usage tab.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-data-usage.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-data-usage.png#lightbox)

### Review user access on the Users tab

The **Users** tab shows a list of users who are using the app, whether they're a priority account, and the amount of data downloaded and uploaded.

If an app has been granted admin consent \(approved for the entire organization by an administrator\), the **Total consented users** are all users in the tenant.

[![Screenshot of an app details pane with the Users tab showing.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-users.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-users.png#lightbox)

### Review app permissions on the Permissions tab

The **Permissions** tab shows a summary and list of the Graph API and legacy permissions granted to the app, consent type, privilege level, and whether they're in use. This also shows the Microsoft Entra roles granted to the app, including its type \(built-in or custom\), privilege level, and whether it grants tenant-wide access. Select a role to view its granular permissions, descriptions, and privilege levels.

Note

Only directly assigned Microsoft Entra roles are shown. Roles inherited through group membership and Azure role-based access control \(Azure RBAC\) roles aren't included.

[![Screenshot of the Permissions tab.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-permissions.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-permissions.png#lightbox)

For more information, see the [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Review sensitivity labels on the Sensitivity labels tab

The **Sensitivity labels** tab shows how frequently items with certain sensitivity labels were accessed by the app on Microsoft 365.

[![Screenshot of the Sensitivity labels tab.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-sensitive-labels-details.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/app-governance-app-sensitive-labels-details.png#lightbox)

## Manage Google Workspace and Salesforce OAuth apps

Enable the [Google Workspace](https://learn.microsoft.com/en-us/defender-cloud-apps/connect-google-workspace) or [Salesforce](https://learn.microsoft.com/en-us/defender-cloud-apps/connect-salesforce) connector to view connected app permissions on the **App governance** page. For Salesforce, the inventory includes both Connected Apps and External Client Apps \(ECAs\). You can view the permissions granted to each app and revoke or block apps as needed.

On the **App governance** page, select the **Google apps** or **Salesforce apps** tabs to view your apps. For example:

[![Screenshot of the Google apps tab](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/google-apps.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-governance-visibility-insights-view-apps/google-apps.png#lightbox)

To manage your Google Workspace or Salesforce apps on the **App governance** page, use the following options:

| Option | Description |
| --- | --- |
| **Queries** | Use the filtering options at the top of the page to define or load a saved query.  <br>  <br>By default, the **App governance** page has a set of saved, basic queries, with one applied as a default filter. Do any of the following actions to change the filter applied as needed:<br><br>- Select **Save as** to save your updated filter.<br>- Select **Select a query** to select a different saved query, such as **Apps authorized by admins** or **Apps authorized by external users**<br>- Select the **Advanced filters** toggle on the right to add more filtering options. Select a filter, an operator, and the value you want to filter by. |
| **Bulk selection** | Select to either select all listed apps, or clear the selection on all selected apps. |
| **New policy from search** | Select to create a new OAuth app policy based on the current query results, For more information, see [Create app policies in app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create). |
| **Export** | Select to export the currently listed apps to a CSV file. |

### View Google Workspace and Salesforce OAuth app details

The **Google** and **Salesforce** pages provide the following information about each OAuth app that users grant permissions to:

| Column name | Description |
| --- | --- |
| **Name** | The app's name. Select to show or hide more details about the app. |
| **Authorized by** | The number of users who authorized this app to access their app's account, and granted the app permissions.  <br>  <br>Select to view more information, including a list of user emails and whether an admin previously consented to the app.  <br>  <br>On the **Users who added...** pane, select **Export** to export the listed users to a CSV file. |
| **Permission level** | *High*, *Medium*, or *Low*.  <br>  <br>The level indicates how much access this app has to the app's data. For example, *Low* might indicate that the app only accesses user profile and name.  <br>  <br>Select the level to view more information, including permissions granted to the app, community use, or related activity in the [Governance log](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions). |
| **Last used** | The most recent date on which this app was used by anyone in your organization. |
| **Risk score** | The app's risk score from 1 through 100. Higher values indicate greater risk. |
| **Actions** | Select an option to mark an app as approved or banned. |

Select **Show details** at the top right to view more information about all of the apps displayed, including:

| Column name | Description |
| --- | --- |
| **Permissions** | A list of all permissions currently granted to the app. |
| **Community use** | *Common*, *Uncommon*, or *Rare*. Indicates how popular the app is among all your users. |
| **App ID** | The app's ID |
| **App activities** | A link to the app's activity log, which you can use to understand the app's recent usage. |
| **Last used** | The most recent date on which this app was used by anyone in your organization. |

## Next steps

[Determine your overall app security posture](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-security-posture)
