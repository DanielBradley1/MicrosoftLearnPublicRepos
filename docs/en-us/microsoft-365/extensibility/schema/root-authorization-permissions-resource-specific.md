<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization-permissions-resource-specific?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.authorization.permissions.resourceSpecific object

Permissions that guard data access on a resource instance level.

Properties that reference this object type:

- [root.authorization.permissions.resourceSpecific](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-authorization-permissions?view=m365-app-1.30#resourceSpecific-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "name": "{string}",
  "type": "Application | Delegated"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the resource-specific permission.",
      "maxLength": 128
    },
    "type": {
      "type": "string",
      "enum": [
        "Application",
        "Delegated"
      ],
      "description": "The type of the resource-specific permission."
    }
  },
  "required": [
    "name",
    "type"
  ]
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "name": "{string}",
  "type": "Application | Delegated"
}
```

```json
{
  "type": "object",
  "additionalProperties": false,
  "properties": {
    "name": {
      "type": "string",
      "description": "The name of the resource-specific permission.",
      "maxLength": 128
    },
    "type": {
      "type": "string",
      "enum": [
        "Application",
        "Delegated"
      ],
      "description": "The type of the resource-specific permission: delegated vs application."
    }
  },
  "required": [
    "name",
    "type"
  ]
}
```

## Properties

#### name

The name of the resource-specific consent \(RSC\) or Office permission to be granted.

For information about the available permissions, see the following:

- [Resource-specific consent for your Teams app](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent#supported-rsc-permissions)
- [Requesting permissions for API use in add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins)
- [Understanding Outlook add-in permissions](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/understanding-outlook-add-in-permissions)

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### type

The type of the resource-specific consent \(RSC\) permission.

**Type**  
string

**Required**  
✅

**Constraints**  


**Supported values**  
Allowed values: `Application`, `Delegated`.

## Remarks

*Application* permissions enable the app to access data without the presence of a signed-in user. For information on application permissions, see [RSC permissions for your Teams app](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

### RSC delegated permissions

*Delegated* permissions enable the app to access data only in the context of a signed-in user's sessions; it doesn't allow access in the absence of a signed-in user.

- **RSC delegated permissions for a team**
  | **Name** | **Description** |
  | --- | --- |
  | `ChannelMeetingParticipant.Read.Group` | Allows the app to read participant information, including name, role, id, joined, and left times, of channel meetings associated with this team, on behalf of the signed-in user. |
  | `ChannelMeetingIncomingAudio.Detect.Group` | Allows the app to detect incoming audio in channel meetings associated with the team. |
  | `ChannelMeetingActiveSpeaker.Read.Group` | Allows the app to read the participants who are sending audio into the channel meetings associated with the team. |
  | `ChannelMeetingAudioVideo.Stream.Group` | Allows the app to stream audio-video content from channel meetings associated with the team. |
  | `InAppPurchase.Allow.Group` | Allows the app to show marketplace offers to users in the team and complete their purchases within the app, on behalf of the signed-in user. |
  | `ChannelMeetingStage.Write.Group` | Allows the app to show content on the meeting stage in channel meetings associated with the team, on behalf of the signed-in user. |
  | `LiveShareSession.ReadWrite.Group` | Allows the app to create and synchronize Live Share sessions for the team and get access related information, such as name and role, about the team's roster and any associated meetings, on behalf of the signed-in user. |
  | `MeetingParticipantReaction.Read.Group` | Allows the app to read reactions of participants in channel meetings associated with the team. |
- **RSC delegated permissions for chats or meetings**
  | **Name** | **Description** |
  | --- | --- |
  | `InAppPurchase.Allow.Chat` | Allows the app to show marketplace offers to the users in the chat, and any associated meeting, and complete their purchases within the app, on behalf of the signed-in user. |
  | `MeetingStage.Write.Chat` | Allows the app to show content on the meeting stage in meetings associated with the chat, on behalf of the signed-in user. |
  | `OnlineMeetingParticipant.Read.Chat` | Allows the app to read participant information, including name, role, id, joined, and left times, of meeting associated with the chat, on behalf of the signed-in user. |
  | `OnlineMeetingParticipant.ToggleIncomingAudio.Chat` | Allows the app to toggle incoming audio for participants in meetings associated with the chat, on behalf of the signed-in user. |
  | `LiveShareSession.ReadWrite.Chat` | Allows the app to create and synchronize Live Share sessions for the chat and get access related information, such as name and role, about the chat's roster and any associated meetings, on behalf of the signed-in user. |
  | `MeetingParticipantReaction.Read.Chat` | Allows the app to read reactions of participants in meetings associated with the chat. |
  | `OnlineMeetingIncomingAudio.Detect.Chat` | Allows the app to detect changes in the status of incoming audio in meetings associated with the chat, on behalf of the signed-in user. |
  | `OnlineMeetingActiveSpeaker.Read.Chat` | Allows the app to read participants who are sending audio into the meetings associated with the chat. |
  | `OnlineMeetingAudioVideo.Stream.Chat` | Allows the app to stream audio-video content of meetings associated with the chat. |
- **RSC delegated permissions for users**
  | **Name** | **Description** |
  | --- | --- |
  | `CameraStream.Read.User` | Allows the app to read user's camera stream. |
  | `InAppPurchase.Allow.User` | Allows the app to show the user marketplace offers and complete the user's purchases within the app, on behalf of the signed-in user. |
  | `OutgoingVideoStream.Write.User` | Allows the app to modify the user's outgoing video. |
  | `MicrophoneStream.Read.User` | Allows the app to read user's microphone stream. |
  | `MeetingParticipantReaction.Read.User` | Allows the app to read user's reactions while participating in a meeting. |
- **Office delegated permissions for users**

  For the permissions and their meaning, see [Requesting permissions for API use in Office add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/requesting-permissions-for-api-use-in-content-and-task-pane-add-ins) and [Permission model for Outlook add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/outlook/privacy-and-security#permissions-model).

## Examples

```json
{
    "authorization": {
        "permissions": {
            "resourceSpecific": [
                {
                    "type": "Application",
                    "name": "ChannelSettings.Read.Group"
                },
                {
                    "type": "Delegated",
                    "name": "ChannelMeetingParticipant.Read.Group"
                }
            ]
        }
    }
}
```

```json
{
    "authorization": {
        "permissions": {
            "resourceSpecific": [
                {
                    "name": "Document.Read.User",
                    "type": "Delegated"
                },
            ]
        }
    }
}
```
