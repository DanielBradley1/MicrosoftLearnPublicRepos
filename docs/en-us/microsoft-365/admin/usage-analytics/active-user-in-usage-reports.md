<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/active-user-in-usage-reports?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Active users in Microsoft 365 usage reports

## Active users in usage reports

An active user of Microsoft 365 products for [Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics?view=o365-worldwide) and the [Activity Reports in the admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports?view=o365-worldwide) is defined as follows.

| **Product** | **Definition of an active user** | **Notes** |
| --- | --- | --- |
| **Exchange Online** | Any user who performs any of the following actions:<br><br>- Marks as read.<br>- Sends messages.<br>- Creates appointments.<br>- Sends meeting requests.<br>- Accepts \(as tentative\) or declines meeting requests.<br>- Cancels meetings. | No calendar information is represented. |
| **SharePoint in Microsoft 365** | Any user who interacts with a file by:<br><br>- Creating.<br>- Modifying.<br>- Viewing.<br>- Deleting.<br>- Sharing internally or externally.<br>- Synchronizing to clients on any site.<br>- Viewed a page on any site. | The active user metrics for SharePoint in Microsoft 365 Usage Analytics template app only reflect users who filed activity against a SharePoint Team site or a Group site. The template app is updated to synchronize the definition to the same as on the usage reports in the admin center. |
| **OneDrive for Business** | Any user who interacts with a file by:<br><br>- Creating.<br>- Modifying.<br>- Viewing.<br>- Deleting.<br>- Sharing internally or externally.<br>- Synchronizing to clients. |  |
| **Microsoft Viva Engage** | Any user who:<br><br>- Reads a message.<br>- Posts a message.<br>- Likes a message. |  |
| **Skype for Business** | Any user who participates in a peer-to-peer session including:<br><br>- Instant messaging.<br>- Audio and video calls.<br>- Application sharing.<br>- File transfers.<br>- Organized or participated in a conference. |  |
| **Microsoft 365** | Any user who activates their Microsoft 365 Apps for enterprise, Visio Pro, or Project Pro subscription on at least one device. |  |
| **Microsoft 365 Groups** | Any group member that has mailbox activity \(if a message was sent to the group\) | This definition is enhanced with group site file activity and Viva Engage group activity. For example, file activity on group site and message posted to Viva Engage group associated with the group. This data is currently not available in the Microsoft 365 Usage Analytics template app |
| **Microsoft Teams** | Any user who participates in:<br><br>- Chat messages.<br>- Private chat messages.<br>- Calls.<br>- Meetings.<br>- Other activity.<br><br>Other activity is defined as the number of other team activities by the user including:<br><br>- Liking messages.<br>- Using apps.<br>- Working on files.<br>- Searching.<br>- Following teams and channels.<br>- Adding a team or channel as a favorite. |  |

## Adoption metrics for Microsoft 365 active users

[Microsoft 365 usage analytics](https://learn.microsoft.com/en-us/microsoft-365/admin/usage-analytics/usage-analytics?view=o365-worldwide) includes more adoption metrics related to active users to show adoption of the products over time. These metrics are valid for the month, year, and product you select. They're defined as follows.

| **Metric** | **Description** |
| --- | --- |
| **EnabledUsers** | Number of users enabled to use the product in the month. |
| **ActiveUsers** | Number of users active in the month. |
| **MoMReturningUsers** | Number of users active in the month that were also active in the preceding month. |
| **FirstTimeUsers** | Number of users active in the month that never used the service before. |
| **CumulativeActiveUsers** | Number of users active in the month plus any preceding month. |
| **ActiveUsers\(%\)** | Percent of users, rounded to the nearest tenth, active in the month compared to the number of users enabled in that month. |
| **MoMReturningUsers\(%\)** | Percent of users, rounded to the nearest tenth, active in the month that were also active in the preceding month compared to the number of active users. |
