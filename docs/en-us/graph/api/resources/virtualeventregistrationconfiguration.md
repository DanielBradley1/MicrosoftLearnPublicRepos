<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventRegistrationConfiguration resource type

Namespace: microsoft.graph

Represents the registration configuration of a virtual event, such as a webinar or town hall. Base type of [virtualEventWebinarRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinarregistrationconfiguration?view=graph-rest-1.0) and [virtualEventTownhallRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhallregistrationconfiguration?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capacity | Int32 | Total capacity of the virtual event. |
| id | String | Unique identifier for the **virtualEventRegistrationConfiguration** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isManualApprovalEnabled | Boolean | Indicates whether registrations require organizer approval before a participant is confirmed. |
| isWaitlistEnabled | Boolean | Indicates whether more registrants are automatically placed on a waitlist when capacity is reached. |
| registrationWebUrl | String | Registration URL of the virtual event. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| questions | [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0) collection | Registration questions. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationConfiguration",
  "capacity": "Int32",
  "id": "String (identifier)",
  "isManualApprovalEnabled": "Boolean",
  "isWaitlistEnabled": "Boolean",
  "registrationWebUrl": "String"
}
```
