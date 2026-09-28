<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# externalMeetingRegistrant resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an external meeting registrant who enrolled in an online meeting.

Inherits from [meetingRegistrantBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrantbase?view=graph-rest-beta).

Caution

The external meeting registrant API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/externalmeetingregistrant-list?view=graph-rest-beta) | [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) collection | Get a list of the [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalmeetingregistrant-post?view=graph-rest-beta) | [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) | Read the properties and relationships of an [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalmeetingregistrant-delete?view=graph-rest-beta) | None | Delete an [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the registrant in the external registration system. Inherited from [meetingRegistrantBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrantbase?view=graph-rest-beta). |
| joinWebUrl | String | A unique web URL for the registrant to join the meeting. Inherited from [meetingRegistrantBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrantbase?view=graph-rest-beta). Read-only. |
| tenantId | String | The tenant ID of this registrant if in Microsoft Entra ID. |
| userId | String | The user ID of this registrant if in Microsoft Entra ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalMeetingRegistrant",
  "id": "String (identifier)",
  "joinWebUrl": "String",
  "userId": "String",
  "tenantId": "String"
}
```
