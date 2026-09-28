<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-17 -->

# serviceUpdateMessage resource type

Namespace: microsoft.graph

Represents the announcements about changes in a service.

Represents announcements such as major updates, new features in a product; for example, the publication of a new SharePoint feature.

Inherits from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get message](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-get?view=graph-rest-1.0) | [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0) | Retrieve the properties and relationships of a [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0) object. |
| [Mark read status](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-markread?view=graph-rest-1.0) | Boolean | Mark a list of [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)s as **read** for the signed in user. |
| [Mark unread status](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-markunread?view=graph-rest-1.0) | Boolean | Mark a list of [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)s as **unread** for the signed in user. |
| [Archive status](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-archive?view=graph-rest-1.0) | Boolean | Archive a list of [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)s for the signed in user. |
| [Unarchive status](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-unarchive?view=graph-rest-1.0) | Boolean | Unarchive a list of [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)s for the signed in user. |
| [Mark favorite status](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-favorite?view=graph-rest-1.0) | Boolean | Change the status of a list of [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)s to favorite for the signed in user. |
| [Remove favorite status](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-unfavorite?view=graph-rest-1.0) | Boolean | Remove the favorite status of [serviceUpdateMessage](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessage?view=graph-rest-1.0)s for the signed in user. |
| [List message attachments](https://learn.microsoft.com/en-us/graph/api/serviceupdatemessage-list-attachments?view=graph-rest-1.0) | [serviceAnnouncementAttachment](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementattachment?view=graph-rest-1.0) collection | Get a list of attachments associated with a service message. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionRequiredByDateTime | DateTimeOffset | The expected deadline of the action for the message. |
| attachmentsArchive | Stream | The zip file that contains all attachments for a message. |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The content type and content of the service message body. The supported value for the contentType property is `html`. |
| category | serviceUpdateCategory | The service message category. The possible values are: `preventOrFixIssue`, `planForChange`, `stayInformed`, `unknownFutureValue`. |
| details | Collection\([keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0)\) | Additional details about service message. This property doesn't support filters. Inherited from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0). |
| endDateTime | DateTimeOffset | The end time of the service message. Inherited from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0). |
| hasAttachments | Boolean | Indicates whether the message has any attachment. |
| id | String | The id of the service message. Inherited from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0). |
| isMajorChange | Boolean | Indicates whether the message describes a major update for the service. |
| lastModifiedDateTime | DateTimeOffset | The last modified time of the service message. Inherited from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0). |
| services | Collection\(string\) | The affected services by the service message. |
| severity | serviceUpdateSeverity | The severity of the service message. The possible values are: `normal`, `high`, `critical`, `unknownFutureValue`. |
| startDateTime | DateTimeOffset | The start time of the service message. Inherited from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0). |
| tags | Collection\(string\) | A collection of tags for the service message. Tags are provided by the service team/support team who post the message to tell whether this message contains privacy data, or whether this message is for a service new feature update, and so on. |
| title | String | The title of the service message. Inherited from [serviceAnnouncementBase](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementbase?view=graph-rest-1.0). |
| viewPoint | [serviceUpdateMessageViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/serviceupdatemessageviewpoint?view=graph-rest-1.0) | Represents user viewpoints data of the service message. This data includes message status such as whether the user has archived, read, or marked the message as favorite. This property is null when accessed with application permissions. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | Collection\([serviceAnnouncementAttachment](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementattachment?view=graph-rest-1.0)\) | A collection of [serviceAnnouncementAttachments](https://learn.microsoft.com/en-us/graph/api/resources/serviceannouncementattachment?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceUpdateMessage",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "title": "String",
  "details": [
    {
      "@odata.type": "microsoft.graph.keyValuePair"
    }
  ],
  "id": "String (identifier)",
  "body": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "category": "String",
  "severity": "String",
  "tags": [
    "String"
  ],
  "isMajorChange": "Boolean",
  "actionRequiredByDateTime": "String (timestamp)",
  "services": [
    "String"
  ],
  "viewPoint": {
    "@odata.type": "microsoft.graph.serviceUpdateMessageViewpoint"
  },
  "hasAttachments": "Boolean",
  "attachmentsArchive": "Stream"
}
```
