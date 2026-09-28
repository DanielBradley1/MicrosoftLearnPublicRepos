<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-exchange-web-services-api-mapping -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Exchange Web Services \(EWS\) to Microsoft Graph API mappings

This article lists the Microsoft Graph APIs that map to Exchange Web Services \(EWS\) APIs.

## Utility APIs

| EWS API | Microsoft Graph API |
| --- | --- |
| [ConvertId](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/convertid-operation) | [Translate Exchange IDs](https://learn.microsoft.com/en-us/graph/api/user-translateexchangeids) |
| [ResolveNames](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/resolvenames-operation) | [List people](https://learn.microsoft.com/en-us/graph/api/user-list-people) |
| [GetServerTimeZones](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getservertimezones-operation) | [Get time zone choices](https://learn.microsoft.com/en-us/graph/api/outlookuser-supportedtimezones) |

## Mail APIs

### Messages

| EWS API | Microsoft Graph API |
| --- | --- |
| [CreateItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/createitem-operation) | [Create message](https://learn.microsoft.com/en-us/graph/api/user-post-messages) |
| [CopyItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/copyitem-operation) | [Copy message](https://learn.microsoft.com/en-us/graph/api/message-copy) |
| [DeleteItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/deleteitem-operation) | [Delete message](https://learn.microsoft.com/en-us/graph/api/message-delete) |
| [FindItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/finditem-operation) | [List messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages) |
| [GetItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getitem-operation) | [Get message](https://learn.microsoft.com/en-us/graph/api/message-get) |
| [MoveItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/moveitem-operation) | [Move message](https://learn.microsoft.com/en-us/graph/api/message-move) |
| [SendItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/senditem-operation) | [Send message](https://learn.microsoft.com/en-us/graph/api/message-send) or [Send mail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) |
| [UpdateItem](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/updateitem-operation) | [Update message](https://learn.microsoft.com/en-us/graph/api/message-update) |

### Folders

| EWS API | Microsoft Graph API |
| --- | --- |
| [CreateFolder](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/createfolder-operation) | [Create mail folder](https://learn.microsoft.com/en-us/graph/api/user-post-mailfolders) |
| [CopyFolder](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/copyfolder-operation) | [Copy mail folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-copy) |
| [DeleteFolder](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/deletefolder-operation) | [Delete mail folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-delete) |
| [GetFolder](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getfolder-operation) | [Get mail folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-get) |
| [MoveFolder](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/movefolder-operation) | [Move mail folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-move) |
| [UpdateFolder](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/updatefolder-operation) | [Update mail folder](https://learn.microsoft.com/en-us/graph/api/mailfolder-update) |

### Attachments

| EWS API | Microsoft Graph API |
| --- | --- |
| [CreateAttachment](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/createattachment-operation) | [Add attachment](https://learn.microsoft.com/en-us/graph/api/message-post-attachments) |
| [GetAttachment](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getattachment-operation) | [Get attachment](https://learn.microsoft.com/en-us/graph/api/attachment-get) |
| [DeleteAttachment](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/deleteattachment-operation) | [Delete attachment](https://learn.microsoft.com/en-us/graph/api/attachment-delete) |

### Rules

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetInboxRules](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getinboxrules-operation) | [List rules](https://learn.microsoft.com/en-us/graph/api/mailfolder-list-messagerules) |
| [UpdateInboxRules](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/updateinboxrules-operation) | [Create rule](https://learn.microsoft.com/en-us/graph/api/mailfolder-post-messagerules)  <br>[Update rule](https://learn.microsoft.com/en-us/graph/api/messagerule-update)  <br>[Delete rule](https://learn.microsoft.com/en-us/graph/api/messagerule-delete) |

### MailTips

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetMailTips](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getmailtips-operation) | [Get MailTips](https://learn.microsoft.com/en-us/graph/api/user-getmailtips) |

### Out of Office \(OOF\) settings

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetUserOofSettings](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getuseroofsettings-operation) | [Get user mailbox settings](https://learn.microsoft.com/en-us/graph/api/user-get-mailboxsettings) |
| [SetUserOofSettings](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/setuseroofsettings-operation) | [Update user mailbox settings](https://learn.microsoft.com/en-us/graph/api/user-update-mailboxsettings) |

### Notifications

Note

Microsoft Graph only requires a subscription for push notifications. If you are currently using [EWS pull notifications](https://learn.microsoft.com/en-us/exchange/client-developer/exchange-web-services/how-to-pull-notifications-about-mailbox-events-by-using-ews-in-exchange), see [Get messages delta](https://learn.microsoft.com/en-us/graph/api/message-delta).

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetEvents](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getevents-operation) | [Get messages delta](https://learn.microsoft.com/en-us/graph/api/message-delta) |
| [Subscribe](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/subscribe-operation) \(Push notifications\) | [Create subscription](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions) |
| [Unsubscribe](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/unsubscribe-operation) \(Push notifications\) | [Delete subscription](https://learn.microsoft.com/en-us/graph/api/subscription-delete) |

### Synchronization

| EWS API | Microsoft Graph API |
| --- | --- |
| [SyncFolderHierarchy](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/syncfolderhierarchy-operation) | [Get mail folder delta](https://learn.microsoft.com/en-us/graph/api/mailfolder-delta) |
| [SyncFolderItems](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/syncfolderitems-operation) | [Get messages delta](https://learn.microsoft.com/en-us/graph/api/message-delta) |

## Calendar APIs

### Availability

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetUserAvailability](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getuseravailability-operation)  <br>FindAvailableMeetingTimes | [Get free/busy schedule](https://learn.microsoft.com/en-us/graph/api/calendar-getschedule) |

### Reminders

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetReminders](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getreminders-operation) | [Reminder view](https://learn.microsoft.com/en-us/graph/api/user-reminderview) |
| [PerformReminderAction](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/performreminderaction-operation) | [Dismiss reminder](https://learn.microsoft.com/en-us/graph/api/event-dismissreminder)  <br>[Snooze reminder](https://learn.microsoft.com/en-us/graph/api/event-snoozereminder) |

### Permissions

| EWS API | Microsoft Graph API |
| --- | --- |
| [GetReminders](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/getreminders-operation) | [Reminder view](https://learn.microsoft.com/en-us/graph/api/user-reminderview) |
| [PerformReminderAction](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/performreminderaction-operation) | [Dismiss reminder](https://learn.microsoft.com/en-us/graph/api/event-dismissreminder)  <br>[Snooze reminder](https://learn.microsoft.com/en-us/graph/api/event-snoozereminder) |
| CreateSharingPermission,GetSharingPermission | [Calendar owner: Get sharing or delegation information and permissions](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar#calendar-owner-get-sharing-or-delegation-information-and-permissions) |
| UpdateSharingPermission | [Get calendar information about sharees and delegates, and update individual permissions](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar#get-calendar-information-about-sharees-and-delegates-and-update-individual-permissions) |
| DeleteSharingPermission | [Delete a sharee or delegate of a calendar](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar#delete-a-sharee-or-delegate-of-a-calendar) |
| GetSharingPermissionInfo | [Calendar owner: Get properties of a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar#get-properties-of-a-shared-or-delegated-calendar) |

### Invitations

| EWS API | Microsoft Graph API |
| --- | --- |
| ActivateSharingInvitation | [Share or delegate a calendar in Outlook](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar) |
| GetSharingInvitation | [Sharee: Get a shared calendar or its events directly from calendar owner's mailbox](https://learn.microsoft.com/en-us/graph/outlook-get-shared-events-calendars#sharee-get-a-shared-calendar-or-its-events-directly-from-calendar-owners-mailbox) |
| DeleteSharingInvitation | [Calendar owner: Update permissions for an existing sharee or delegate on a calendar](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar#calendar-owner-update-permissions-for-an-existing-sharee-or-delegate-on-a-calendar) |
| CreateSharingInvitation | [Create Outlook events in a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-create-event-in-shared-delegated-calendar#step-2-adele-creates-and-sends-an-invitation-on-alex-behalf) |

### Shared Information

| EWS API | Microsoft Graph API |
| --- | --- |
| GetCalendarSharedInformation,GetConsumerCalendarSharedInformation | [List calendars](https://learn.microsoft.com/en-us/graph/api/user-list-calendars) |

## Groups APIs

| EWS API | Microsoft Graph API |
| --- | --- |
| GetUserUnifiedGroups | [List memberof](https://learn.microsoft.com/en-us/graph/api/user-list-memberof) |
| GetUnifiedGroupsSettings | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting) |
| GetUnifiedGroupDetails | [Get group](https://learn.microsoft.com/en-us/graph/api/group-get) |
| GetUnifiedGroupMembers | [List members](https://learn.microsoft.com/en-us/graph/api/group-list-members) |
| GetUnifiedGroupUnseenCount | [Get group](https://learn.microsoft.com/en-us/graph/api/group-get) |
| SetUnifiedGroupMembershipState | [Add/remove member/owner](https://learn.microsoft.com/en-us/graph/api/resources/group) |
| FindUnifiedGroups | [List groups](https://learn.microsoft.com/en-us/graph/api/group-list) |
| SetUnifiedGroupUserSubscribeState | [Subscribe/unsubscribeByMail](https://learn.microsoft.com/en-us/graph/api/group-subscribebymail) |
| UpdateUnifiedGroup | [Update group](https://learn.microsoft.com/en-us/graph/api/group-update) |
| CreateUnifiedGroup | [Create group](https://learn.microsoft.com/en-us/graph/api/group-post-groups) |
| RemoveUnifiedGroup | [Delete group](https://learn.microsoft.com/en-us/graph/api/group-delete) |
| SetUnifiedGroupFavoriteState | [Group addFavorite](https://learn.microsoft.com/en-us/graph/api/group-addfavorite) |
| JoinPrivateUnifiedGroup | [Subscribe/unsubscribeByMail](https://learn.microsoft.com/en-us/graph/api/group-subscribebymail) |
| GetDlMembersForUnifiedGroup | [List group members](https://learn.microsoft.com/en-us/graph/api/group-list-members) |
