<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinarregistrationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventWebinarRegistrationConfiguration resource type

Namespace: microsoft.graph

Contains information about a webinar registration configuration.

Inherits from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/virtualeventwebinarregistrationconfiguration-get?view=graph-rest-1.0) | [virtualEventWebinarRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinarregistrationconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a [virtualEventWebinarRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinarregistrationconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capacity | Int32 | Total capacity of the virtual event. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| id | String | Unique identifier for the **virtualEventRegistrationConfiguration** object. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| isManualApprovalEnabled | Boolean | Indicates whether registrations require organizer approval before a participant is confirmed. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| isWaitlistEnabled | Boolean | Indicates whether more registrants are automatically placed on a waitlist when capacity is reached. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |
| registrationWebUrl | String | Registration portal URL of the webinar. Inherited from [virtualEventRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationconfiguration?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventWebinarRegistrationConfiguration",
  "id": "String (identifier)",
  "registrationWebUrl": "String",
  "capacity": "Int32",
  "isWaitlistEnabled": "Boolean",
  "isManualApprovalEnabled": "Boolean"
}
```
