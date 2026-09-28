<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventRegistration resource type

Namespace: microsoft.graph

Represents a registrant's registration record for a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualeventregistration-list?view=graph-rest-1.0) | [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) collection | Get a list of all [registration records](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) of a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinar-post-registrations?view=graph-rest-1.0) | [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) | Create a registrant's [registration record](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) for a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventregistration-get?view=graph-rest-1.0) | [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) | Get the properties and relationships of a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) object. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/virtualeventregistration-cancel?view=graph-rest-1.0) | None | Cancel a registrant's [registration record](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0) for a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |
| [List sessions](https://learn.microsoft.com/en-us/graph/api/virtualeventregistration-list-sessions?view=graph-rest-1.0) | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) collection | Get a list of [sessions](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) that a registrant registered for in a [webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) or [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cancelationDateTime | DateTimeOffset | Date and time when the registrant cancels their registration for the virtual event. Only appears when applicable. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| email | String | Email address of the registrant. |
| externalRegistrationInformation | [virtualEventExternalRegistrationInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalregistrationinformation?view=graph-rest-1.0) | The external information for a virtual event registration. |
| firstName | String | First name of the registrant. |
| id | String | Unique identifier of the registrant. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastName | String | Last name of the registrant. |
| preferredTimezone | String | The registrant's time zone details. |
| preferredLanguage | String | The registrant's preferred language. |
| registrationDateTime | DateTimeOffset | Date and time when the registrant registers for the virtual event. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| registrationQuestionAnswers | [virtualEventRegistrationQuestionAnswer](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionanswer?view=graph-rest-1.0) collection | The registrant's answer to the registration questions. |
| status | virtualEventAttendeeRegistrationStatus | Registration status of the registrant. Read-only. Possible values are `registered`, `canceled`, `waitlisted`, `pendingApproval`, `rejectedByOrganizer`, and `unknownFutureValue`. |
| userId | String | The registrant's ID in Microsoft Entra ID. Only appears when the registrant is registered in Microsoft Entra ID. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sessions | [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) collection | Sessions for a registration. |

## JSON representation

The following JSON representation shows the resource type

```json
{
  "@odata.type": "#microsoft.graph.virtualEventRegistration",
  "cancelationDateTime": "String (timestamp)",
  "email": "String",
  "externalRegistrationInformation": {"@odata.type": "microsoft.graph.virtualEventExternalRegistrationInformation"},
  "firstName": "String",
  "id": "String (identifier)",
  "lastName": "String",
  "preferredTimezone": "String",
  "preferredLanguage": "String",
  "registrationDateTime": "String (timestamp)",
  "registrationQuestionAnswers": [{"@odata.type": "microsoft.graph.virtualEventRegistrationQuestionAnswer"}],
  "status": "String",
  "userId": "String"
}
```
