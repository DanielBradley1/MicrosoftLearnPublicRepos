<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-11 -->

# meetingRegistration resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The meeting registration API is deprecated and will stop returning data on **July 31, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Contains registration details of an online meeting, such as a [Microsoft Teams Webinar](https://support.microsoft.com/office/get-started-with-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3).

Inherits from [meetingRegistrationBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationbase?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/meetingregistration-post?view=graph-rest-beta) | [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) | Create and enable registration for an online meeting. |
| [Get](https://learn.microsoft.com/en-us/graph/api/meetingregistration-get?view=graph-rest-beta) | [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) | Retrieve the details of a meeting registration. |
| [Update](https://learn.microsoft.com/en-us/graph/api/meetingregistration-update?view=graph-rest-beta) | [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) | Update the details of a meeting registration. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/meetingregistration-delete?view=graph-rest-beta) | [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) | Disable and delete registration for an online meeting. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedRegistrant | [meetingAudience](#meetingaudience-values) | Specifies who can register for the meeting. |
| description | String | The description of the meeting. |
| endDateTime | DateTime | The meeting end time in UTC. |
| registrationPageViewCount | Int32 | The number of times the registration page has been visited. Read-only. |
| registrationPageWebUrl | String | The URL of the registration page. Read-only. |
| speakers | [meetingSpeaker](https://learn.microsoft.com/en-us/graph/api/resources/meetingspeaker?view=graph-rest-beta) collection | The meeting speaker's information. |
| startDateTime | DateTime | The meeting start time in UTC. |
| subject | String | The subject of the meeting. |

### meetingAudience values

| Value | Description |
| --- | --- |
| everyone | Everyone can register for the meeting. |
| organization | Everyone in the organizer’s organization can register for the meeting. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| customQuestions | [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) collection | Custom registration questions. |
| registrants | [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) collection | Registrants of the online meeting. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowedRegistrant": { "@odata.type": "microsoft.graph.meetingAudience" },
  "description": "String",
  "endDateTime": "String (timestamp)",
  "registrationPageViewCount": "Int32",
  "registrationPageWebUrl": "String",
  "speakers": [{ "@odata.type": "microsoft.graph.meetingSpeaker" }],
  "startDateTime": "String (timestamp)",
  "subject": "String"
}
```
