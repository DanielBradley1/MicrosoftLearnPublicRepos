<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# eventMessageDetail resource type

Namespace: microsoft.graph

Represents details of a system event message.

System messages are messages generated for events such as [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) added to a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), **members** added to a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0), and [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) description updated.

### Supported events

| Event | Description |
| :--- | :--- |
| [callEndedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/callendedeventmessagedetail?view=graph-rest-1.0) | A call has ended. |
| [callRecordingEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/callrecordingeventmessagedetail?view=graph-rest-1.0) | Call recording is available. |
| [callStartedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/callstartedeventmessagedetail?view=graph-rest-1.0) | A call has started. |
| [callTranscriptEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/calltranscripteventmessagedetail?view=graph-rest-1.0) | Call transcript is available. |
| [channelAddedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/channeladdedeventmessagedetail?view=graph-rest-1.0) | A **channel** has been added. |
| [channelDeletedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/channeldeletedeventmessagedetail?view=graph-rest-1.0) | A **channel** has been deleted. |
| [channelDescriptionUpdatedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/channeldescriptionupdatedeventmessagedetail?view=graph-rest-1.0) | **Channel's** description has been updated. |
| [channelRenamedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/channelrenamedeventmessagedetail?view=graph-rest-1.0) | A **channel** has been renamed. |
| [channelSetAsFavoriteByDefaultEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/channelsetasfavoritebydefaulteventmessagedetail?view=graph-rest-1.0) | A **channel** has been set as favorite by default. |
| [channelUnsetAsFavoriteByDefaultEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/channelunsetasfavoritebydefaulteventmessagedetail?view=graph-rest-1.0) | A **channel** has been unset as favorite by default. |
| [chatRenamedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/chatrenamedeventmessagedetail?view=graph-rest-1.0) | A chat has been renamed. |
| [conversationMemberRoleUpdatedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/conversationmemberroleupdatedeventmessagedetail?view=graph-rest-1.0) | Role has been updated for a **member**. |
| [meetingPolicyUpdatedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/meetingpolicyupdatedeventmessagedetail?view=graph-rest-1.0) | Meeting policy has been updated. |
| [membersAddedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/membersaddedeventmessagedetail?view=graph-rest-1.0) | **Members** have been added. |
| [membersDeletedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/membersdeletedeventmessagedetail?view=graph-rest-1.0) | **Members** have been removed. |
| [membersJoinedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/membersjoinedeventmessagedetail?view=graph-rest-1.0) | **Members** have joined. |
| [membersLeftEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/memberslefteventmessagedetail?view=graph-rest-1.0) | **Members** have left. |
| [messagePinnedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/messagepinnedeventmessagedetail?view=graph-rest-1.0) | A message has been pinned. |
| [messageUnpinnedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/messageunpinnedeventmessagedetail?view=graph-rest-1.0) | A message has been unpinned. |
| [tabUpdatedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/tabupdatedeventmessagedetail?view=graph-rest-1.0) | A tab has been updated. |
| [teamArchivedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamarchivedeventmessagedetail?view=graph-rest-1.0) | A **team** has been archived. |
| [teamCreatedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamcreatedeventmessagedetail?view=graph-rest-1.0) | A **team** has been created. |
| [teamDescriptionUpdatedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamdescriptionupdatedeventmessagedetail?view=graph-rest-1.0) | **Team's** description has been updated. |
| [teamJoiningDisabledEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamjoiningdisabledeventmessagedetail?view=graph-rest-1.0) | **Team** joining has been disabled. |
| [teamJoiningEnabledEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamjoiningenabledeventmessagedetail?view=graph-rest-1.0) | **Team** joining has been enabled. |
| [teamRenamedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamrenamedeventmessagedetail?view=graph-rest-1.0) | A **team** has been renamed. |
| [teamsAppInstalledEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstalledeventmessagedetail?view=graph-rest-1.0) | [Teams app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) has been installed. |
| [teamsAppRemovedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamsappremovedeventmessagedetail?view=graph-rest-1.0) | **Teams app** has been removed. |
| [teamsAppUpgradedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamsappupgradedeventmessagedetail?view=graph-rest-1.0) | **Teams app** has been upgraded. |
| [teamUnarchivedEventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/teamunarchivedeventmessagedetail?view=graph-rest-1.0) | A **team** has been unarchived. |

## Properties

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.eventMessageDetail"
}
```
