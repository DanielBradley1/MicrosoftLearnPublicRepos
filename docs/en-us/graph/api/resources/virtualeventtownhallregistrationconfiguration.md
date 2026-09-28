<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhallregistrationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventTownhallRegistrationConfiguration resource type

Namespace: microsoft.graph

Contains information about a town hall registration configuration.

Inherits from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhallregistrationconfiguration-get?view=graph-rest-1.0) | [virtualEventTownhallRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhallregistrationconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a [virtualEventTownhallRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhallregistrationconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capacity | Int32 | Total capacity of the town hall. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| id | String | Unique identifier for the **virtualEventRegistrationConfiguration** object. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| isManualApprovalEnabled | Boolean | Indicates whether registrations require organizer approval before a participant is confirmed. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| isWaitlistEnabled | Boolean | Indicates whether more registrants are automatically placed on a waitlist when capacity is reached. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| registrationWebUrl | String | Registration portal URL of the town hall. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| questions | [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0) collection | Registration questions. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventTownhallRegistrationConfiguration",
  "id": "String (identifier)",
  "registrationWebUrl": "String",
  "capacity": "Int32",
  "isWaitlistEnabled": "Boolean",
  "isManualApprovalEnabled": "Boolean"
}
```
