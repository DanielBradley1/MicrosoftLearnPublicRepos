<!-- Source: https://learn.microsoft.com/en-us/graph/change-notifications-overview -->
<!-- Sitemap-Last-Modified: 2025-03-05 -->

# Set up notifications for changes in resource data

Change notifications enable applications to receive alerts when a Microsoft Graph resource they're interested in changes; that is, created, updated, or deleted. Microsoft Graph sends notifications to the specified client endpoint, and the client service processes the notifications according to the business requirements. For example, the service might fetch more data, update its cache and views, and so on.

Important

The change notifications feature isn't supported in Microsoft Entra External ID in external tenants and Azure AD B2C tenants.

## Why get change notifications?

Change notifications follow an event-driven model where customers receive alerts when changes occur instead of them polling Microsoft Graph. Depending on your business logic, change notifications are suitable when:

- You're subscribing to a resource that changes frequently.
- You need to react to changes in near real-time.
- You want to avoid frequently polling Microsoft Graph which might cause you to hit the throttling limits.

The following image shows how change notifications works and compares with [change tracking](https://learn.microsoft.com/en-us/graph/delta-query-overview).

![Illustration of change notifications and delta query services](https://learn.microsoft.com/en-us/graph/images/change-notifications/change-notifications-vs-delta-query.png)

The following video provides an overview of change notifications in Microsoft Graph.

<iframe src="https://www.youtube-nocookie.com/embed/rC1bunenaq4" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Types of change notifications

Microsoft Graph supports three types of change notifications:

- **Basic notifications**: Change notifications that don't contain resource data other than the **id** of the resource that changed. When an app receives a basic notification, the service can use the **id** to query the changed object.
- **Rich notifications**: Change notifications that include the resource data of the object that changed. For more information about rich notifications, see [Rich notifications](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data).
- **Lifecycle notifications**: Notifications that alert the customer when they are at risk of missing change notifications due to the lifecycle of their subscription. For more information about lifecycle notifications, see [Lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events).

## Receiving change notifications

Microsoft Graph can deliver change notifications to clients via the following channels.

- **Webhooks**. For more information, see [Receive change notifications through webhooks](https://learn.microsoft.com/en-us/graph/change-notifications-delivery-webhooks).
- **Azure Event Hubs**. For more information, see [Receive change notifications through Azure Event Hubs](https://learn.microsoft.com/en-us/graph/change-notifications-delivery-event-hubs).
- **Azure Event Grid**. For more information, see [Receive change notifications through Azure Event Grid](https://learn.microsoft.com/en-us/azure/event-grid/subscribe-to-graph-api-events?context=graph%2Fcontext).

## Managing subscriptions

Clients can create subscriptions, renew subscriptions, and delete subscriptions. While the subscription is active and when changes occur in the subscribed resource, Microsoft Graph sends change notifications to the specified notification endpoint.

You manage the subscription using the [subscription resource type](https://learn.microsoft.com/en-us/graph/api/resources/subscription) and its related methods. Microsoft Graph sends change notifications in a structure defined in the [changeNotificationCollection resource type](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationcollection).

## Supported resources

An app can subscribe to changes on the Microsoft Graph resources listed in the table. Subscriptions to resources marked with an asterisk \(`*`\) are only available on the `/beta` endpoint.

Note

For Microsoft Teams resources, the **per-organization limit of 10,000 total subscriptions** is shared cumulatively across **all Teams change notification subscriptions** in the tenant. It includes subscriptions created for different Teams resources—such as chats, chat messages, call transcripts, call recordings, channels, teams, and conversation members—which **all count toward the same organizational quota**. When the combined number of active Teams subscriptions reaches this limit, **any additional subscription creation request for a Teams resource fails** with a `403 Forbidden` error.

| Resource | Supported resource paths | Limitations |
| --- | --- | --- |
| Cloud printing [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer) | Changes when a print job is ready to be downloaded \(jobFetchable event\): `/print/printers/{id}/jobs` | - |
| Cloud printing [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition) | Changes when there's a valid job in the queue \(jobStarted event\): `/print/printtaskdefinition/{id}/tasks` | - |
| Copilot [aiInsights](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight) | Copilot AI insights from meetings that a particular user is part of: `/copilot/users/{userId}/onlineMeetings/getAllAiInsights`  <br>  <br>Copilot AI insights for a particular meeting: `/copilot/users/{userId}/onlineMeetings/{onlineMeetingId}/aiInsights` | Maximum subscription quotas for AI insights across all meetings for a user:<br><br>- Per app and user combination: 1<br>- Per user \(delegated\): 10<br>- Per organization: 10,000 total subscriptions.<br><br>  <br>  <br>Maximum subscription quotas for AI insights of a specific meeting:<br><br>- Per app and user + meeting combination: 1<br>- Per user and meeting combination \(delegated\): 1<br>- Per organization: 10,000 total subscriptions \(shared\) |
| Copilot [aiInteraction](https://learn.microsoft.com/en-us/graph/api/resources/aiinteraction) | Copilot AI interactions that a particular user is part of: `copilot/users/{userId}/interactionHistory/getAllEnterpriseInteractions`  <br>  <br>Copilot AI interactions in an organization: `copilot/interactionHistory/getAllEnterpriseInteractions` | Maximum subscription quotas:<br><br>- Per app and tenant combination \(for subscriptions tracking AI interactions across a tenant\): 1<br>- Per app and user combination \(for subscriptions tracking AI interactions a particular user is part of\): 1<br>- Per user \(for subscriptions tracking AI interactions a particular user is part of\): 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) on OneDrive \(personal\) | Changes to content within the hierarchy of *any folder*: `/users/{id}/drive/root` | - |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) on OneDrive for work or school | Changes to content within the hierarchy of the *root folder*: `/drives/{id}/root` , `/users/{id}/drive/root` | - |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group) | Changes to all groups: `/groups`  <br>  <br>Changes to a specific group: `/groups/{id}`  <br>  <br>Changes to owners of a specific group: `/groups/{id}/owners`  <br>  <br>Changes to members of a specific group: `/groups/{id}/members` | Maximum subscription quotas:<br><br>- Per app \(for all tenants combined\): 50,000 total subscriptions.<br>- Per tenant \(for all applications combined\): 1,000 total subscriptions across all apps.<br>- Per app and tenant combination: 100 total subscriptions.<br><br>  <br>  <br>Not supported for Azure AD B2C tenants.  <br>  <br>**NOTE:** Creation and soft-deletion of groups also trigger the `updated` **changeType**. |
| Microsoft Entra Health Monitoring [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert) | Changes to all health monitoring alerts: `/reports/healthmonitoring/alerts`  <br>  <br>Changes to a specific type of alert: `/reports/healthmonitoring/alert` with the `notificationQueryOptions` property in request payload set as `$filter=alertType eq '{alertType}'` | - |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list) under a SharePoint [site](https://learn.microsoft.com/en-us/graph/api/resources/site) | Changes to content within the *list*: `/sites/{site-id}/lists/{list-id}` | - |
| Microsoft 365 group [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation) | Changes to a group's conversations: `groups/{id}/conversations` | - |
| Outlook [message](https://learn.microsoft.com/en-us/graph/api/resources/message) | Changes to all messages in a user's mailbox: `/users/{id}/messages` , `/me/messages`  <br>  <br>Changes to messages in a user's Inbox: `/users/{id}/mailFolders('inbox')/messages` , `/me/mailFolders('inbox')/messages` | A maximum of 1,000 active subscriptions per mailbox for all applications is allowed. |
| Outlook [event](https://learn.microsoft.com/en-us/graph/api/resources/event) | Changes to all events in a user's mailbox: `/users/{id}/events` , `/me/events` | A maximum of 1,000 active subscriptions per mailbox for all applications is allowed. |
| Outlook personal [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) | Changes to all personal contacts in a user's mailbox: `/users/{id}/contacts` , `/me/contacts` | A maximum of 1,000 active subscriptions per mailbox for all applications is allowed. |
| Security [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert) | Changes to a specific alert: `/security/alerts/{id}`  <br>  <br>Changes to filtered alerts: `/security/alerts/?$filter={parameters}` | For more information, see [Security API alerts](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview?view=graph-rest-beta#alerts&preserve-view=true). |
| Teams [approvals](https://learn.microsoft.com/en-us/graph/api/resources/approvalItem) | Changes to all approvals in a tenant: `/solutions/approval/approvalItems` | Maximum subscription quotas:<br><br>- Per tenant \(for all applications combined\): 1000 total subscriptions across all apps<br>- Per app and tenant combination: 1 subscription. |
| Teams [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) | Changes to all call records: `/communications/callRecords`  <br>  <br>Changes to filtered call records: `/communications/callRecords?$filter={parameters}` | For more information, see [Change notifications for Call Records](https://learn.microsoft.com/en-us/graph/changenotifications-for-callrecords).  <br>  <br>Maximum subscription quotas:<br><br>- Per organization: 100 total subscriptions.<br><br>  <br>  <br>**NOTE:** Creation of call records also triggers the `updated` **changeType**. |
| Teams [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording) | All recordings in an organization: `communications/onlineMeetings/getAllRecordings`  <br>  <br>All recordings for a specific meeting: `communications/onlineMeetings/{onlineMeetingId}/recordings`  <br>  <br>A call recording that becomes available in a meeting organized by a specific user: `users/{id}/onlineMeetings/getAllRecordings`  <br>  <br>A call recording that becomes available in a meeting where a particular Teams app is installed: `appCatalogs/teamsApps/{id}/installedToOnlineMeetings/getAllRecordings` \* | Maximum subscription quotas:<br><br>- Per app and online-meeting combination: 1<br>- Per app and user combination: 1<br>- Per user \(for subscriptions tracking recordings in all onlineMeetings organized by the user\): 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| Teams [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript) | All transcripts in an organization: `communications/onlineMeetings/getAllTranscripts`  <br>  <br>All transcripts for a specific meeting: `communications/onlineMeetings/{onlineMeetingId}/transcripts`  <br>  <br>A call transcript that becomes available in a meeting organized by a specific user: `users/{id}/onlineMeetings/getAllTranscripts`  <br>  <br>A call transcript that becomes available in a meeting where a particular Teams app is installed: `appCatalogs/teamsApps/{id}/installedToOnlineMeetings/getAllTrancripts` \* | Maximum subscription quotas:<br><br>- Per app and online-meeting combination: 1<br>- Per app and user combination: 1<br>- Per user \(for subscriptions tracking transcripts in all onlineMeetings organized by the user\): 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| Teams [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat) | Changes to any chat in the tenant: `/chats`  <br>  <br>Changes to a specific chat: `/chats/{id}`  <br>  <br>Changes to a specific chat with the [notifyOnUserSpecificProperties](https://learn.microsoft.com/en-us/graph/teams-changenotifications-chat#notification-payloads-for-user-specific-properties) query parameter: `/chats/{id}?notifyOnUserSpecificProperties={Boolean}`  <br>  <br>Changes to all chats in an organization where a particular Teams app is installed: `/appCatalogs/teamsApps/{id}/installedToChats`  <br>  <br>Changes to all chats that a particular user is part of: `/users/{id}/chats`  <br>  <br>Changes to all chats that a particular user is part of with the [notifyOnUserSpecificProperties](https://learn.microsoft.com/en-us/graph/teams-changenotifications-chat#notification-payloads-for-user-specific-properties) query parameter: `/users/{id}/chats?notifyOnUserSpecificProperties={Boolean}` | Maximum subscription quotas:<br><br>- Per app and chat combination: 1 subscription.<br>- Per organization: 10,000 total subscriptions.<br>- Per user \(for subscriptions tracking all chats that a particular user is part of\): 10 subscriptions. |
| Teams [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage) | Changes to chat messages in all channels in all teams: `/teams/getAllMessages`  <br>  <br>Changes to chat messages in a specific channel: `/teams/{id}/channels/{id}/messages`  <br>  <br>Changes to chat messages in all chats: `/chats/getAllMessages`  <br>  <br>Changes to chat messages in a specific chat: `/chats/{id}/messages`  <br>  <br>Changes to chat messages in all chats a particular user is part of: `/users/{id}/chats/getAllMessages`  <br>  <br>Changes to chat messages for all chats in an organization where a particular Teams app is installed: `/appCatalogs/teamsApps/{id}/installedToChats/getAllMessages` | Maximum subscription quotas:<br><br>- Per app and channel or chat combination: 1 subscription.<br>- Per user \(for subscriptions tracking chat messages in all chats the user is part of\): 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| Teams [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel) | Changes to channels in all teams: `/teams/getAllChannels`  <br>  <br>Changes to channel in a specific team: `/teams/{id}/channels` | Maximum subscription quotas:<br><br>- Per app and team combination: 1 subscription.<br>- Per organization: 10,000 total subscriptions. |
| Teams [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember) | Changes to membership in a specific team: `/teams/{id}/members`  <br>  <br>Changes to membership in all channels under a specific team: `teams/{id}/channels/getAllMembers`  <br>  <br>Changes to membership in a specific chat: `/chats/{id}/members`  <br>  <br>Changes to membership for all chats in an organization where a particular Teams app is installed: `/appCatalogs/teamsApps/{id}/installedToChats/getAllMembers`  <br>  <br>Changes to membership in all chats: `/chats/getAllMembers` | Maximum subscription quotas:<br><br>- Per app and team combination: 1 subscription.<br>- Per organization: 10,000 total subscriptions. |
| Teams [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) <sup>\*</sup> | Changes to an online meeting: `/communications/onlineMeetings(joinWebUrl='{encodedJoinWebUrl}')/meetingCallEvents` | Doesn't support using `$select` to return only selected properties. The rich notification consists of all the properties of the changed instance. One subscription allowed per application per online meeting. For more information, see [Get change notifications for Microsoft Teams meeting call event updates](https://learn.microsoft.com/en-us/graph/changenotifications-for-onlinemeeting). |
| Teams [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence) | Changes to a single user's presence: `/communications/presences/{id}`  <br>  <br>Changes to multiple users' presence: `/communications/presences?$filter=id in ({id},{id}...)` | The subscription for multiple users' presence is limited to 650 distinct users. Doesn't support using `$select` to return only selected properties. The rich notification consists of all the properties of the changed instance. One subscription allowed per application per delegated user. For more information, see [Get change notifications for presence updates in Microsoft Teams](https://learn.microsoft.com/en-us/graph/changenotifications-for-presence). |
| Teams [team](https://learn.microsoft.com/en-us/graph/api/resources/team) | Changes to any team in the tenant: `/teams`  <br>  <br>Changes to a specific team: `/teams/{id}` | Maximum subscription quotas:<br><br>- Per app and team combination: 1 subscription.<br>- Per organization: 10,000 total subscriptions. |
| Teams Shifts [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest) | Changes to any offer shift request in a team: `/teams/{id}/schedule/offerShiftRequests` | Maximum subscription quotas:<br><br>- Per app and resource path combination: 1 subscription per tenant.<br>- Per resource path and user combination: 10 delegated user subscriptions per tenant. |
| Teams Shifts [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest) | Changes to any open shift request in a team: `/teams/{id}/schedule/openShiftChangeRequests` | Maximum subscription quotas:<br><br>- Per app and resource path combination: 1 subscription per tenant.<br>- Per user and resource path combination: 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| Teams Shifts [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift) | Changes to any shift in a team: `/teams/{id}/schedule/shifts` | Maximum subscription quotas:<br><br>- Per app and resource path combination: 1 subscription per tenant.<br>- Per user and resource path combination: 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| Teams Shifts [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest) | Changes to any swap shift request in a team: `/teams/{id}/schedule/swapShiftsChangeRequests` | Maximum subscription quotas:<br><br>- Per app and resource path combination: 1 subscription per tenant.<br>- Per user and resource path combination: 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| Teams Shifts [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest) | Changes to any time off request in a team: `/teams/{id}/schedule/timeOffRequests` | Maximum subscription quotas:<br><br>- Per app and resource path combination: 1 subscription per tenant.<br>- Per user and resource path combination: 10 subscriptions.<br>- Per organization: 10,000 total subscriptions. |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask) | Changes to all task in a specific task list: `/me/todo/lists/{todoTaskListId}/tasks` | - |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user) | Changes to all users: `/users`  <br>  <br>Changes to a specific user: `/users/{id}` | Maximum subscription quotas:<br><br>- Per app \(for all tenants combined\): 50,000 total subscriptions.<br>- Per tenant \(for all applications combined\): 1,000 total subscriptions across all apps<br>- Per app and tenant combination: 100 total subscriptions.<br><br>  <br>  <br>Not supported for personal Microsoft accounts like outlook.com.  <br>  <br>Not supported for Azure AD B2C tenants.  <br>  <br>**NOTE:** Creation and soft-deletion of users also trigger the `updated` **changeType**. |

Note

Many resources have limits or quotas on how many subscriptions can be made against that resource. When exceeding that limit, attempts to create a subscription will result in a `403 Forbidden` error response. The **message** property of the error response will explain the limit that has been exceeded.

Some of these resources support rich notifications \(notifications with resource data\). For their details, see [Set up change notifications that include resource data](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data#supported-resources).

## Subscription lifetime

Subscriptions have a limited lifetime. Apps need to renew their subscriptions before the expiration time; Otherwise, they need to create a new subscription. Apps can also unsubscribe at any time to stop getting change notifications.

The following table shows the maximum expiration times for subscriptions per resource in Microsoft Graph.

| Resource | Maximum expiration time |
| :--- | :--- |
| Copilot [aiInteraction](https://learn.microsoft.com/en-us/graph/api/resources/aiinteraction) | 4,320 minutes \(three days\) |
| Security [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert) | 43,200 minutes \(under 30 days\) |
| Teams [approvals](https://learn.microsoft.com/en-us/graph/api/resources/approvalItem) | 43,200 minutes \(under 30 days\) |
| Teams [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) | 4,230 minutes \(under three days\) |
| Teams [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording) | 4,320 minutes \(three days\) |
| Teams [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript) | 4,320 minutes \(three days\) |
| Teams [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel) | 4,320 minutes \(three days\) |
| Teams [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat) | 4,320 minutes \(three days\) |
| Teams [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage) | 4,320 minutes \(three days\) |
| Teams [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember) | 4,320 minutes \(three days\) |
| Teams [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) | 4,320 minutes \(three days\) |
| Teams [team](https://learn.microsoft.com/en-us/graph/api/resources/team) | 4,320 minutes \(three days\) |
| Teams [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation) | 4,320 minutes \(3 days\) |
| Teams Shifts [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest) | 360 minutes \(6 hours\) |
| Teams Shifts [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest) | 360 minutes \(6 hours\) |
| Teams Shifts [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift) | 360 minutes \(6 hours\) |
| Teams Shifts [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest) | 360 minutes \(6 hours\) |
| Teams Shifts [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest) | 360 minutes \(6 hours\) |
| Group [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation) | 4,230 minutes \(under three days\) |
| OneDrive [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) | 42,300 minutes \(under 30 days\) |
| SharePoint [list](https://learn.microsoft.com/en-us/graph/api/resources/list) | 42,300 minutes \(under 30 days\) |
| Outlook [message](https://learn.microsoft.com/en-us/graph/api/resources/message), [event](https://learn.microsoft.com/en-us/graph/api/resources/event), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) | 10,080 minutes \(under seven days\)  <br>  <br>For subscriptions with resource data \(rich notification subscriptions\), subscription lifetime is 1440 minutes \(under one day\). |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user), [group](https://learn.microsoft.com/en-us/graph/api/resources/group), other directory resources | 41,760 minutes \(under 29 days\) |
| [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) | 4,230 minutes \(under three days\) |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence) | 60 minutes \(1 hour\) |
| Print [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer) | 4,230 minutes \(under three days\) |
| Print [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition) | 4,230 minutes \(under three days\) |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask) | 4,230 minutes \(under three days\)  <br>  <br>Webhooks for this resource are only available in the global endpoint and not in the national clouds. |
| Microsoft Entra Health Monitoring [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert) | 42,300 minutes \(under 30 days\) |
| **baseTask** \(deprecated\) | 4,230 minutes \(under three days\) |

> **Note:** Existing applications and new applications should not exceed the supported value. In the future, any requests to create or renew a subscription beyond the maximum value will fail.

## Latency

The following table lists the latency to expect between an event happening in the service and the delivery of the change notification.

| Resource | Average latency | Maximum latency |
| :--- | :--- | :--- |
| [aiInteraction](https://learn.microsoft.com/en-us/graph/api/resources/aiinteraction) | Less than 10 seconds | 60 minutes |
| [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert) <sup>1</sup> | Less than 3 minutes | 5 minutes |
| [approvals](https://learn.microsoft.com/en-us/graph/api/resources/approvalItem) | Less than 10 seconds | 40 seconds |
| [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar) | Less than 1 minute | 3 minutes |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) <sup>2</sup> | Less than 30 minutes | 150 minutes |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording) | Less than 10 seconds | 60 minutes |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript) | Less than 10 seconds | 60 minutes |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel) | Less than 10 seconds | 60 minutes |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat) | Less than 10 seconds | 60 minutes |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage) | Less than 10 seconds | 1 minute |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) | Less than 1 minute | 3 minutes |
| [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation) | Unknown | Unknown |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember) | Less than 10 seconds | 60 minutes |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) | Less than 1 minute | 6 hours |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event) | Unknown | Unknown |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group) | Unknown | Unknown |
| [health monitoring alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert) | Unknown | Unknown |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list) | Less than 1 minute | 6 hours |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message) | Less than 1 minute | 3 minutes |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest) | Less than 1 minute | 60 minutes |
| [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) | Less than 10 seconds | 1 minute |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest) | Less than 1 minute | 60 minutes |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence) | Less than 10 seconds | 1 minute |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer) | Less than 1 minute | 5 minutes |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition) | Less than 1 minute | 5 minutes |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift) | Less than 1 minute | 60 minutes |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest) | Less than 1 minute | 60 minutes |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team) | Less than 10 seconds | 60 minutes |
| [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation) | Less than 10 seconds | 60 minutes |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest) | Less than 1 minute | 60 minutes |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask) | Less than 2 minutes | 15 minutes |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user) | Unknown | Unknown |

<sup>1</sup> The latency provided for the **alert** resource is only applicable after the alert is created. It doesn't include the time it takes for a rule to create an alert from the data. <sup>2</sup> The latency provided for the **callRecord** resource is only applicable to the first version of a call record. Subsequent versions of a call record might be updated beyond the stated latencies.

## Code samples

The following code samples are available on GitHub.

- [Microsoft Graph Training Module - Using Change Notifications and Track Changes with Microsoft Graph](https://github.com/microsoftgraph/msgraph-training-changenotifications)
- [Microsoft Graph Webhooks Sample for Node.js](https://github.com/microsoftgraph/nodejs-webhooks-rest-sample)
- [Microsoft Graph Webhooks Sample for ASP.NET Core](https://github.com/microsoftgraph/aspnetcore-webhooks-sample)
- [Microsoft Graph Webhooks Sample for Java Spring](https://github.com/microsoftgraph/java-spring-webhooks-sample)

## Related content

- [Rich notifications \(notifications with resource data\)](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data)
- [Lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events)
- [Change notifications for cloud printing](https://learn.microsoft.com/en-us/graph/universal-print-webhook-notifications)
- [Change notifications for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-change-notifications-overview)
- [Change notifications for Microsoft Teams resources](https://learn.microsoft.com/en-us/graph/teams-change-notification-in-microsoft-teams-overview)
