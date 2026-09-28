<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/report?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-23 -->

# Working with Microsoft 365 usage reports in Microsoft Graph

With Microsoft Graph, you can access Microsoft 365 usage reports resources to get the information about how people in your business are using Microsoft 365 services. For example, you can identify who is using a service a lot and reaching quotas, or who might not need a Microsoft 365 license at all.

For details about the settings that govern identification/de-identification of information in the Microsoft 365 usage reports data, see [Microsoft 365 Reports in the admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports) .

## Authorization

Microsoft Graph controls access to resources via permissions. You must specify the permissions you need in order to access Reports resources. Typically, you specify permissions in the Microsoft Entra admin center. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference) and [Reports permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#reports-permissions).

## Settings

In Microsoft 365 reports, user information such as usernames, groups, and sites is concealed; actual values aren't displayed. You can use the [adminReportSettings](https://learn.microsoft.com/en-us/graph/api/resources/adminreportsettings?view=graph-rest-1.0) API to control the display of user information in the reports.

## Cloud deployments

The following table shows the availability for each API across all cloud deployments.

| APIs | Microsoft Graph global service | Microsoft Cloud for US Government | Microsoft Cloud China operated by 21Vianet |
| --- | --- | --- | --- |
| [Admin report settings](https://learn.microsoft.com/en-us/graph/api/resources/adminreportsettings?view=graph-rest-1.0) | ✔ | ➖ | ➖ |
| [Microsoft 365 activations](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-365-activations) | ✔ | ➖ | ➖ |
| [Microsoft 365 active users](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-365-active-users) | ✔ | ➖ | ➖ |
| [Microsoft 365 apps usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-365-apps-usage) | ✔ | ➖ | ➖ |
| [Microsoft 365 groups activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-365-groups-activity) | ✔ | ➖ | ➖ |
| [Microsoft Teams device usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-teams-device-usage) | ✔ | ➖ | ➖ |
| [Microsoft Teams team activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-teams-team-activity) | ✔ | ➖ | ➖ |
| [Microsoft Teams user activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#microsoft-teams-user-activity) | ✔ | ➖ | ➖ |
| [Outlook activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#outlook-activity) | ✔ | ➖ | ➖ |
| [Outlook app usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#outlook-app-usage) | ✔ | ➖ | ➖ |
| [Outlook mailbox usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#outlook-mailbox-usage) | ✔ | ➖ | ➖ |
| [OneDrive activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#onedrive-activity) | ✔ | ➖ | ➖ |
| [OneDrive usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#onedrive-usage) | ✔ | ➖ | ➖ |
| [SharePoint activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#sharepoint-activity) | ✔ | ➖ | ➖ |
| [SharePoint site usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#sharepoint-site-usage) | ✔ | ➖ | ➖ |
| [Skype for Business activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#skype-for-business-activity) | ✔ | ➖ | ➖ |
| [Skype for Business device usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#skype-for-business-device-usage) | ✔ | ➖ | ➖ |
| [Skype for Business organizer activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#skype-for-business-organizer-activity) | ✔ | ➖ | ➖ |
| [Skype for Business participant activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#skype-for-business-participant-activity) | ✔ | ➖ | ➖ |
| [Skype for Business peer-to-peer activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#skype-for-business-peer-to-peer-activity) | ✔ | ➖ | ➖ |
| [Viva Engage activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#viva-engage-activity) | ✔ | ➖ | ➖ |
| [Viva Engage device usage](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#viva-engage-device-usage) | ✔ | ➖ | ➖ |
| [Viva Engage groups activity](https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0#viva-engage-groups-activity) | ✔ | ➖ | ➖ |

## Next steps

Reports resources and APIs can open up new ways for you to engage with users and manage their experiences with Microsoft Graph. To learn more:

- Drill down on the methods and properties of the resources most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
