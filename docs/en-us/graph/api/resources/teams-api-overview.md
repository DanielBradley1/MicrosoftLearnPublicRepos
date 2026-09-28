<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# Use the Microsoft Graph API to work with Microsoft Teams

Microsoft Teams is a chat-based workspace in Microsoft 365 that provides built-in access to team-specific calendars, files, OneNote notes, Planner plans, Shifts schedules, and more. You can use the Microsoft Graph API to integrate with Microsoft Teams features.

## Common use cases

The following table lists common use cases for Microsoft Teams APIs in Microsoft Graph.

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| Create and manage teams, groups, and channels | [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0), [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | [create team](https://learn.microsoft.com/en-us/graph/api/team-put-teams?view=graph-rest-1.0), [list teams](https://learn.microsoft.com/en-us/graph/api/user-list-joinedteams?view=graph-rest-1.0), [create channel](https://learn.microsoft.com/en-us/graph/api/channel-post?view=graph-rest-1.0) |
| Add tabs, manage, or install apps in the Microsoft Teams app catalog | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0), [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) | [create teamsTab](https://learn.microsoft.com/en-us/graph/api/channel-post-tabs?view=graph-rest-1.0), [list teamsTab](https://learn.microsoft.com/en-us/graph/api/channel-list-tabs?view=graph-rest-1.0), [list apps](https://learn.microsoft.com/en-us/graph/api/appcatalogs-list-teamsapps?view=graph-rest-1.0) |
| Create channels and chats to send and receive chat messages | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0), [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | [create channel](https://learn.microsoft.com/en-us/graph/api/channel-post?view=graph-rest-1.0), [list channel](https://learn.microsoft.com/en-us/graph/api/channel-list?view=graph-rest-1.0), [send chatMessage](https://learn.microsoft.com/en-us/graph/api/chatmessage-post?view=graph-rest-1.0) |
| Use tags to classify users or groups based on common attributes within a team | [teamworkTag](https://learn.microsoft.com/en-us/graph/api/resources/teamworktag?view=graph-rest-1.0), [teamworkTagMember](https://learn.microsoft.com/en-us/graph/api/resources/teamworktagmember?view=graph-rest-1.0) | [list teamworkTag](https://learn.microsoft.com/en-us/graph/api/teamworktag-list?view=graph-rest-1.0), [create teamworkTag](https://learn.microsoft.com/en-us/graph/api/teamworktag-post?view=graph-rest-1.0) |
| Create and receive calls, call records or retrieve meeting coordinates | [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0), [callRecords](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-api-overview?view=graph-rest-1.0) | [answer](https://learn.microsoft.com/en-us/graph/api/call-answer?view=graph-rest-1.0), [invite participants](https://learn.microsoft.com/en-us/graph/api/participant-invite?view=graph-rest-1.0) |
| Connect bots to calls and implement interactive voice response \(IVR\) | [call](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) | [IVR scenarios](#ivr-scenarios) |
| Create and retrieve online meetings or check users presence and activity | [onlineMeetings](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0), [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | [create onlineMeetings](https://learn.microsoft.com/en-us/graph/api/application-post-onlinemeetings?view=graph-rest-1.0), [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) |
| Create and manage workforce integration with shifts, schedules, time cards, or time off in your organization | [workforceIntegration](https://learn.microsoft.com/en-us/graph/api/resources/workforceintegration?view=graph-rest-1.0), [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0), [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0), [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) | [create workforceIntegration](https://learn.microsoft.com/en-us/graph/api/workforceintegration-post?view=graph-rest-1.0), [create schedule](https://learn.microsoft.com/en-us/graph/api/schedule-post-schedulinggroups?view=graph-rest-1.0), [create shift](https://learn.microsoft.com/en-us/graph/api/schedule-post-shifts?view=graph-rest-1.0), [create timeOff](https://learn.microsoft.com/en-us/graph/api/schedule-post-timesoff?view=graph-rest-1.0) |
| Use the employee learning API to integrate with Viva Learning | [employee learning](https://learn.microsoft.com/en-us/graph/api/resources/viva-learning-api-overview?view=graph-rest-1.0), [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0), [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) | [list learningProviders](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-learningproviders?view=graph-rest-1.0), [list learningContents](https://learn.microsoft.com/en-us/graph/api/learningprovider-list-learningcontents?view=graph-rest-1.0) |

### IVR scenarios

The following are the Interactive Voice Response \(IVR\) scenarios that the calling APIs in Microsoft Graph support:

- [Play an audio prompt](https://learn.microsoft.com/en-us/graph/api/call-playprompt) - for example, when a call is placed in a customer service agent's queue.
- [Record a response](https://learn.microsoft.com/en-us/graph/api/call-record) - for example, to record the caller's audio, usually after they heard a prompt with options.
- [Subscribe to tones](https://learn.microsoft.com/en-us/graph/api/call-subscribetotone) - for example, when you want to know what DTMF tones the caller selected, usually after hearing the audio prompt.
- [Cancel media processing](https://learn.microsoft.com/en-us/graph/api/call-cancelmediaprocessing) - for example, when you want to cancel any **playPrompt** or **recordResponse** operations that might be in process.

## Microsoft Teams limits

The tested performance and capacity limits of Microsoft Teams are documented in [Limits and specifications for Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/limits-specifications-teams). These limits apply whether using Microsoft Teams directly or using Microsoft Graph APIs. Because every team has a corresponding group, and every group is a directory object, limits on the [number of groups](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/office-365-groups#group-limits) and the [number of directory objects \("resources"\)](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-service-limits-restrictions) can also come into play.

Files inside channels are stored in SharePoint; [SharePoint online limits](https://learn.microsoft.com/en-us/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) apply.

See also [throttling limits for Microsoft Teams services](https://learn.microsoft.com/en-us/graph/throttling#microsoft-teams-service-limits).

## Teams and groups

In Microsoft Graph, Microsoft Teams is represented by a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) resource. Both Microsoft Teams and Microsoft 365 groups address the various needs of group collaboration. Almost all the group-based features apply to Microsoft Teams and Microsoft 365 groups, such as group calendar, files, notes, photo, plans, and so on. The main difference between a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) and a Microsoft 365 group is the mode of communication between members. Team members communicate by persistent chat in the context of a specific team. Microsoft 365 group members communicate by group conversations, which are email conversations that occur in the context of a group in Outlook.

Any group that has a team has a **resourceProvisioningOptions** property that contains "Team".

> **Note:** The **Group.resourceProvisioningOptions** property can be changed. Do not add or remove "Team" from that collection; otherwise, you'll get incorrect results when you list all teams.

The following are the differences at the API level between teams and groups:

- Persistent chat is available only to Microsoft Teams. This feature is hierarchically represented by the [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) and [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) resources.
- Group conversations are available only to Microsoft 365 groups. This feature is hierarchically represented by the [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0), [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0), and [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) resources.
- The [List joined teams](https://learn.microsoft.com/en-us/graph/api/user-list-joinedteams?view=graph-rest-1.0) method applies only to Microsoft Teams.
- [Calling](https://learn.microsoft.com/en-us/graph/api/resources/call?view=graph-rest-1.0) and [online meeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) APIs apply only to Microsoft Teams.
- See also the [known issues](https://developer.microsoft.com/en-us/graph/known-issues) for these APIs.

## Membership changes in Microsoft Teams

| Use case | Verb | URL |
| --- | --- | --- |
| [Add member](https://learn.microsoft.com/en-us/graph/api/team-post-members?view=graph-rest-1.0) | POST | /teams/{team-id}/members |
| [Remove member](https://learn.microsoft.com/en-us/graph/api/team-delete-members?view=graph-rest-1.0) | DELETE | /teams/{team-id}/members/{membership-id} |
| [Update member's role](https://learn.microsoft.com/en-us/graph/api/team-update-members?view=graph-rest-1.0) | PATCH | /teams/{team-id}/members/{membership-id} |
| [Update team](https://learn.microsoft.com/en-us/graph/api/team-update?view=graph-rest-1.0) | PATCH | /teams/{team-id} |

## Polling requirements

If your app polls to see whether a resource has changed, you can only do that once per day. \([teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) is an exception in that it's intended to be polled frequently.\) If you need to hear about changes more frequently than that, you should [create a subscription](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0) to that resource and receive change notifications \(webhooks\). If you don't find support for the type of subscription you need, we encourage you to provide feedback via the [Microsoft 365 Developer Platform ideas forum](https://techcommunity.microsoft.com/t5/microsoft-365-developer-platform/idb-p/Microsoft365DeveloperPlatform/label-name/Microsoft%20Graph).

When polling for new messages, you must specify a date range where supported. For more information, see [get delta chat messages for a user](https://learn.microsoft.com/en-us/graph/api/chatmessage-delta?view=graph-rest-1.0).

Polling is doing a GET operation on a resource over and over again to see if that resource has changed. You're allowed to GET the same resource multiple times a day, as long as it's not polling. For example, it's okay to GET /me/joinedTeams every time the user visits/refreshes your web page, but it isn't okay to GET /me/joinedTeams in a loop every 30 seconds to refresh that web page.

Apps that don't follow these polling requirements will be considered in violation of the [Microsoft APIs Terms of Use](https://learn.microsoft.com/en-us/legal/microsoft-apis/terms-of-use). This may result in additional [throttling](https://learn.microsoft.com/en-us/graph/throttling) or the suspension or termination of your use of the Microsoft APIs.

## Related content

- [Overview for using Microsoft Teams, Shifts, and Viva Learning to foster teamwork](https://learn.microsoft.com/en-us/graph/teams-concept-overview)
- Sample code: [Contoso Airlines](https://github.com/microsoftgraph/contoso-airlines-teams-sample), [C# mini-samples](https://github.com/microsoftgraph/csharp-teams-sample-graph)
