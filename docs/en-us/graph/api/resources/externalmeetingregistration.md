<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-15 -->

# externalMeetingRegistration resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The external meeting registration API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Represents external registration details of an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-beta).

Inherits from [meetingRegistrationBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationbase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/externalmeetingregistration-post?view=graph-rest-beta) | [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) | Create a new [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalmeetingregistration-get?view=graph-rest-beta) | [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) | Read the properties and relationships of an [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/externalmeetingregistration-delete?view=graph-rest-beta) | None | Delete an [externalMeetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedRegistrant | [meetingAudience](#meetingaudience-values) | Specifies who can register for the meeting. Inherited from [meetingRegistrationBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationbase?view=graph-rest-beta). |

### meetingAudience values

| Value | Description |
| --- | --- |
| everyone | Everyone can register for the meeting. |
| organization | Everyone in the organizer’s organization can register for the meeting. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| registrants | [externalMeetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/externalmeetingregistrant?view=graph-rest-beta) collection | Registrants of the online meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalMeetingRegistration",
  "allowedRegistrant": "String"
}
```
