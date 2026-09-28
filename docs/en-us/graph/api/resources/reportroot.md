<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/reportroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-08 -->

# reportRoot resource type

Namespace: microsoft.graph

Represents a container for Microsoft Entra and Microsoft 365 reporting resources.

## Methods

### Microsoft Teams device usage

For details about report views and names, see [Microsoft 365 reports - Microsoft Teams device usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-teams-device-usage-preview).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsdeviceusageuserdetail?view=graph-rest-1.0) | Stream | Get details about Microsoft Teams device usage by user. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsdeviceusageusercounts?view=graph-rest-1.0) | Stream | Get the number of daily unique users by device type. |
| [Get distribution user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsdeviceusagedistributionusercounts?view=graph-rest-1.0) | Stream | Get the number of unique users by device type over the selected time period. |

### Microsoft Teams user activity

For details about report views and names, see [Microsoft 365 reports - Microsoft Teams user activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-teams-user-activity-preview).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsuseractivityuserdetail?view=graph-rest-1.0) | Stream | Get details about Microsoft Teams user activity by user. |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsuseractivitycounts?view=graph-rest-1.0) | Stream | Get the number of Microsoft Teams activities by activity type. The activities are performed by Microsoft Teams licensed users. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsuseractivityusercounts?view=graph-rest-1.0) | Stream | Get the number of users by activity type. The activity types are number of teams chat messages, private chat messages, calls, or meetings. |

### Microsoft Teams team activity

For details about report views and names, see [Microsoft 365 reports - Microsoft Teams usage activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-teams-usage-activity).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get team detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsteamactivitydetail?view=graph-rest-1.0) | Stream | Get details about Teams activity by team. The numbers include activities for both licensed and non-licensed users. |
| [Get team activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsteamactivitycounts?view=graph-rest-1.0) | Stream | Get the number of team activities across Microsoft Teams. The activity types are related to meetings and messages. |
| [Get team activity distribution counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsteamactivitydistributioncounts?view=graph-rest-1.0) | Stream | Get the number of team activities across Microsoft Teams over a selected period. |
| [Get team counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getteamsteamcounts?view=graph-rest-1.0) | Stream | Get the number of teams by type across Microsoft Teams. |

### Outlook activity

For details about report views and names, see [Microsoft 365 reports - Email Activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/email-activity-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailactivityuserdetail?view=graph-rest-1.0) | Stream | Get details about email activity users have performed. |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailactivitycounts?view=graph-rest-1.0) | Stream | Enables you to understand the trends of email activity \(like how many were sent, read, and received\) in your organization. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailactivityusercounts?view=graph-rest-1.0) | Stream | Enables you to understand trends on the number of unique users who are performing email activities like send, read, and receive. |

### Outlook app usage

[Microsoft 365 reports - Email apps usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/email-apps-usage-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailappusageuserdetail?view=graph-rest-1.0) | Stream | Get details about which activities users performed on the various email apps. |
| [Get apps user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailappusageappsusercounts?view=graph-rest-1.0) | Stream | Get the count of unique users per email app. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailappusageusercounts?view=graph-rest-1.0) | Stream | Get the count of unique users that connected to Exchange Online using any email app. |
| [Get versions user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getemailappusageversionsusercounts?view=graph-rest-1.0) | Stream | Get the count of unique users by Outlook desktop version. |

### Outlook mailbox usage

For details about report views and names, see [Microsoft 365 reports - Mailbox usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/mailbox-usage).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get mailbox detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getmailboxusagedetail?view=graph-rest-1.0) | Stream | Get details about mailbox usage. |
| [Get mailbox counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getmailboxusagemailboxcounts?view=graph-rest-1.0) | Stream | Get the total number of user mailboxes in your organization and how many are active each day of the reporting period. A mailbox is considered active if the user sent or read any email. |
| [Get quota status mailbox counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getmailboxusagequotastatusmailboxcounts?view=graph-rest-1.0) | Stream | Get the count of user mailboxes in each quota category. |
| [Get storage](https://learn.microsoft.com/en-us/graph/api/reportroot-getmailboxusagestorage?view=graph-rest-1.0) | Stream | Get the amount of storage used in your organization. |

### Microsoft 365 activations

For details about report views and names, see [Microsoft 365 reports - Microsoft Office activations](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-office-activations-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365activationsuserdetail?view=graph-rest-1.0) | Stream | Get details about users who have activated Microsoft 365. |
| [Get activation counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365activationcounts?view=graph-rest-1.0) | Stream | Get the count of Microsoft 365 activations on desktops and devices. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365activationsusercounts?view=graph-rest-1.0) | Stream | Get the count of users that are enabled and those that have activated the Office subscription on desktop or devices. |

### Microsoft 365 active users

For details about report views and names, see [Microsoft 365 reports - Active Users](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/active-users-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365activeuserdetail?view=graph-rest-1.0) | Stream | Get details about Microsoft 365 active users. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365activeusercounts?view=graph-rest-1.0) | Stream | Get the count of daily active users in the reporting period by product. |
| [Get services user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365servicesusercounts?view=graph-rest-1.0) | Stream | Get the count of users by activity type and service. |

### Microsoft 365 apps usage

For details about report views and names, see [Microsoft 365 reports - Microsoft 365 Apps usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft365-apps-usage).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getm365appuserdetail?view=graph-rest-1.0) | Stream | Get details about the usage of Microsoft 365 Apps by user. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getm365appusercounts?view=graph-rest-1.0) | Stream | Get the number of daily unique users by app. |
| [Get platform user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getm365appplatformusercounts?view=graph-rest-1.0) | Stream | Get the number of daily unique users by platform. |

### Microsoft 365 groups activity

For details about report views and names, see [Microsoft 365 reports - Microsoft 365 groups](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/office-365-groups-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get group detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365groupsactivitydetail?view=graph-rest-1.0) | Stream | Get details about Microsoft 365 groups activity by group. |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365groupsactivitycounts?view=graph-rest-1.0) | Stream | Get the number of group activities across group workloads. |
| [Get group counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365groupsactivitygroupcounts?view=graph-rest-1.0) | Stream | Get the daily total number of groups and how many of them were active based on email conversations, Viva Engage posts, and SharePoint file activities. |
| [Get storage](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365groupsactivitystorage?view=graph-rest-1.0) | Stream | Get the total storage used across all group mailboxes and group sites. |
| [Get file counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getoffice365groupsactivityfilecounts?view=graph-rest-1.0) | Stream | Get the total number of files and how many of them were active across all group sites associated with a Microsoft 365 group. |

### OneDrive activity

For details about report views and names, see [Microsoft 365 reports - OneDrive for Business activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/onedrive-for-business-activity-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveactivityuserdetail?view=graph-rest-1.0) | Stream | Get details about OneDrive activity by user. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveactivityusercounts?view=graph-rest-1.0) | Stream | Get the trend in the number of active OneDrive users. |
| [Get file counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveactivityfilecounts?view=graph-rest-1.0) | Stream | Get the number of unique, licensed users that performed file interactions against any OneDrive account. |

### OneDrive usage

For details about report views and names, see [Microsoft 365 reports - OneDrive for Business usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/onedrive-for-business-usage-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get account detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveusageaccountdetail?view=graph-rest-1.0) | Stream | Get details about OneDrive usage by account. |
| [Get account counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveusageaccountcounts?view=graph-rest-1.0) | Stream | Get the trend in the number of active OneDrive for Business sites. Any site on which users viewed, modified, uploaded, downloaded, shared, or synced files is considered an active site. |
| [Get file counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveusagefilecounts?view=graph-rest-1.0) | Stream | Get the total number of files across all sites and how many are active files. A file is considered active if it has been saved, synced, modified, or shared within the specified time period. |
| [Get storage](https://learn.microsoft.com/en-us/graph/api/reportroot-getonedriveusagestorage?view=graph-rest-1.0) | Stream | Get the trend on the amount of storage you are using in OneDrive for Business. |

### SharePoint activity

For details about report views and names, see [Microsoft 365 reports - SharePoint activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/sharepoint-activity-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointactivityuserdetail?view=graph-rest-1.0) | Stream | Get details about SharePoint activity by user. |
| [Get file counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointactivityfilecounts?view=graph-rest-1.0) | Stream | Get the number of unique, licensed users who interacted with files stored on SharePoint sites. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointactivityusercounts?view=graph-rest-1.0) | Stream | Get the trend in the number of active users. A user is considered active if he or she has executed a file activity \(save, sync, modify, or share\) or visited a page within the specified time period. |
| [Get pages](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointactivitypages?view=graph-rest-1.0) | Stream | Get the number of unique pages visited by users. |

### SharePoint site usage

For details about report views and names, see [Microsoft 365 reports - SharePoint site usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/sharepoint-site-usage-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get site detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointsiteusagedetail?view=graph-rest-1.0) | Stream | Get details about SharePoint site usage. |
| [Get file counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointsiteusagefilecounts?view=graph-rest-1.0) | Stream | Get the total number of files across all sites and the number of active files. A file \(user or system\) is considered active if it has been saved, synced, modified, or shared within the specified time period. |
| [Get site counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointsiteusagesitecounts?view=graph-rest-1.0) | Stream | Get the trend of total and active site count during the reporting period. |
| [Get storage](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointsiteusagestorage?view=graph-rest-1.0) | Stream | Get the trend of storage allocated and consumed during the reporting period. |
| [Get pages](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointsiteusagepages?view=graph-rest-1.0) | Stream | Get the number of pages viewed across all sites. |

### Skype for Business activity

For details about report views and names, see [Skype for Business activity](https://learn.microsoft.com/en-us/skypeforbusiness/skype-for-business-online-reporting/activity-report).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessactivityuserdetail?view=graph-rest-1.0) | Stream | Get details about Skype for Business activity by user. |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessactivitycounts?view=graph-rest-1.0) | Stream | Get the trends on how many users organized and participated in conference sessions held in your organization through Skype for Business. The report also includes the number of peer-to-peer sessions. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessactivityusercounts?view=graph-rest-1.0) | Stream | Get the trends on how many unique users organized and participated in conference sessions held in your organization through Skype for Business. The report also includes the number of peer-to-peer sessions. |

### Skype for Business device usage

For details about report views and names, see [Skype for Business clients used](https://learn.microsoft.com/en-us/skypeforbusiness/skype-for-business-online-reporting/device-usage-report).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessdeviceusageuserdetail?view=graph-rest-1.0) | Stream | Get details about Skype for Business device usage by user. |
| [Get distribution user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessdeviceusagedistributionusercounts?view=graph-rest-1.0) | Stream | Get the number of users using unique devices in your organization. The report shows you the number of users per device including Windows, Windows phone, Android phone, iPhone, and iPad. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessdeviceusageusercounts?view=graph-rest-1.0) | Stream | Get the usage trends on how many users in your organization have connected using the Skype for Business app. You also get a breakdown by the type of device \(Windows, Windows phone, Android phone, iPhone, or iPad\) on which the Skype for Business client app is installed and used across your organization. |

### Skype for Business organizer activity

For details about report views and names, see [Skype for Business conference organizer activity](https://learn.microsoft.com/en-us/skypeforbusiness/skype-for-business-online-reporting/conference-organizer-activity-report).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessorganizeractivitycounts?view=graph-rest-1.0) | Stream | Get usage trends on the number and type of conference sessions held and organized by users in your organization. Types of conference sessions include IM, audio/video, application sharing, web, dial-in/out - third party, and dial-in/out Microsoft. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessorganizeractivityusercounts?view=graph-rest-1.0) | Stream | Get usage trends on the number of unique users and type of conference sessions held and organized by users in your organization. Types of conference sessions include IM, audio/video, application sharing, web, dial-in/out - third party, and dial-in/out Microsoft. |
| [Get minute counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessorganizeractivityminutecounts?view=graph-rest-1.0) | Stream | Get usage trends on the length in minutes and type of conference sessions held and organized by users in your organization. Types of conference sessions include audio/video, and dial-in and dial-out - Microsoft. |

### Skype for Business participant activity

For details about report views and names, see [Skype for Business conference participant activity](https://learn.microsoft.com/en-us/skypeforbusiness/skype-for-business-online-reporting/conference-participant-activity-report).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessparticipantactivitycounts?view=graph-rest-1.0) | Stream | Get usage trends on the number and type of conference sessions that users from your organization participated in. Types of conference sessions include IM, audio/video, application sharing, web, and dial-in/out - third party. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessparticipantactivityusercounts?view=graph-rest-1.0) | Stream | Get usage trends on the number of unique users and type of conference sessions that users from your organization participated in. Types of conference sessions include IM, audio/video, application sharing, web, and dial-in/out - third party. |
| [Get minute counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinessparticipantactivityminutecounts?view=graph-rest-1.0) | Stream | Get usage trends on the length in minutes and type of conference sessions that users from your organization participated in. Types of conference sessions include audio/video. |

### Skype for Business peer-to-peer activity

For details about report views and names, see [Skype for Business peer-to-peer activity](https://learn.microsoft.com/en-us/skypeforbusiness/skype-for-business-online-reporting/peer-to-peer-activity-report).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinesspeertopeeractivitycounts?view=graph-rest-1.0) | Stream | Get usage trends on the number and type of sessions held in your organization. Types of sessions include IM, audio, video, application sharing, and file transfer. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinesspeertopeeractivityusercounts?view=graph-rest-1.0) | Stream | Get usage trends on the number of unique users and type of peer-to-peer sessions held in your organization. Types of sessions include IM, audio, video, application sharing, and file transfers in peer-to-peer sessions. |
| [Get minute counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getskypeforbusinesspeertopeeractivityminutecounts?view=graph-rest-1.0) | Stream | Get usage trends on the length in minutes and type of peer-to-peer sessions held in your organization. Types of sessions include audio and video. |

### Viva Engage activity

For details about report views and names, see [Microsoft 365 reports - Viva Engage Activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/viva-engage-activity-report-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammeractivityuserdetail?view=graph-rest-1.0) | Stream | Get details about Viva Engage activity by user. |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammeractivitycounts?view=graph-rest-1.0) | Stream | Get the trends on the amount of Viva Engage activity in your organization by how many messages were posted, read, and liked. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammeractivityusercounts?view=graph-rest-1.0) | Stream | Get the trends on the number of unique users who posted, read, and liked Viva Engage messages. |

### Viva Engage device usage

For details about report views and names, see [Microsoft 365 reports - Viva Engage device usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/viva-engage-device-usage-report-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get user detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammerdeviceusageuserdetail?view=graph-rest-1.0) | Stream | Get details about Viva Engage device usage by user. |
| [Get distribution user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammerdeviceusagedistributionusercounts?view=graph-rest-1.0) | Stream | Get the number of users by device type. |
| [Get user counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammerdeviceusageusercounts?view=graph-rest-1.0) | Stream | Get the number of daily users by device type. |

### Viva Engage groups activity

For details about report views and names, see [Microsoft 365 reports - Viva Engage groups activity](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/viva-engage-groups-activity-report-ww).

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get group detail](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammergroupsactivitydetail?view=graph-rest-1.0) | Stream | Get details about Viva Engage groups activity by group. |
| [Get group counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammergroupsactivitygroupcounts?view=graph-rest-1.0) | Stream | Get the total number of groups that existed and how many included group conversation activity. |
| [Get activity counts](https://learn.microsoft.com/en-us/graph/api/reportroot-getyammergroupsactivitycounts?view=graph-rest-1.0) | Stream | Get the number of Viva Engage messages posted, read, and liked in groups. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authenticationMethods | [authenticationMethodsRoot](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodsroot?view=graph-rest-1.0) | Container for navigation properties for Microsoft Entra authentication methods resources. |
| dailyPrintUsageByPrinter | [printUsageByPrinter](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyprinter?view=graph-rest-1.0) collection | Retrieve a list of daily print usage summaries, grouped by printer. |
| dailyPrintUsageByUser | [printUsageByUser](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyuser?view=graph-rest-1.0) collection | Retrieve a list of daily print usage summaries, grouped by user. |
| monthlyPrintUsageByPrinter | [printUsageByPrinter](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyprinter?view=graph-rest-1.0) collection | Retrieve a list of monthly print usage summaries, grouped by printer. |
| monthlyPrintUsageByUser | [printUsageByUser](https://learn.microsoft.com/en-us/graph/api/resources/printusagebyuser?view=graph-rest-1.0) collection | Retrieve a list of monthly print usage summaries, grouped by user. |
| partners | [partners](https://learn.microsoft.com/en-us/graph/api/resources/partners?view=graph-rest-1.0) | Represents billing details for a Microsoft direct partner. |
| security | [securityReportsRoot](https://learn.microsoft.com/en-us/graph/api/resources/securityreportsroot?view=graph-rest-1.0) | Represents an abstract type that contains resources for attack simulation and training reports. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.reportRoot"
}
```
