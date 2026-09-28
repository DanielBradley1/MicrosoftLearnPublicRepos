<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingRegistrant resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a meeting registrant who enrolled in an [online meeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-beta).

Inherits from [meetingRegistrantBase](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrantbase?view=graph-rest-beta).

Caution

The meeting registrant API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/meetingregistration-list-registrants?view=graph-rest-beta) | [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) | List all registrants who enrolled in the meeting. |
| [Create](https://learn.microsoft.com/en-us/graph/api/meetingregistration-post-registrants?view=graph-rest-beta) | [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) | Enroll a registrant in an online meeting. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/meetingregistrant-delete?view=graph-rest-beta) | [meetingRegistrant](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrant?view=graph-rest-beta) | Unenroll a registrant from an online meeting. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customQuestionAnswers | [customQuestionAnswer](https://learn.microsoft.com/en-us/graph/api/resources/customquestionanswer?view=graph-rest-beta) collection | The registrant's answer to custom questions. |
| email | String | The email address of the registrant. |
| firstName | String | The first name of the registrant. |
| id | String | The unique identifier of the registrant. Read-only. |
| joinWebUrl | String | A unique web URL for the registrant to join the meeting. Read-only. |
| lastName | String | The family name of the registrant. |
| registrationDateTime | String | Time in UTC when the registrant registers for the meeting. Read-only. |
| status | [meetingRegistrantStatus](#meetingregistrantstatus-values) | The registration status of the registrant. Read-only. |

### meetingRegistrantStatus values

| Value | Description |
| --- | --- |
| registered | Registrant has enrolled in the meeting. |
| canceled | Registrant has canceled their registration. |
| processing | Interim status indicating the status is processing. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String",
  "firstName": "String (timestamp)",
  "email": "String",
  "lastName": "String",
  "joinWebUrl": "String",
  "registrationDateTime": "String (timestamp)",
  "status": { "@odata.type": "microsoft.graph.meetingRegistrantStatus" },
  "customQuestionAnswers": [{ "@odata.type": "microsoft.graph.customQuestionAnswer" }]
}
```
