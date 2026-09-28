<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emergencycallerinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-14 -->

# emergencyCallerInfo resource type

Namespace: microsoft.graph

Contains information about an emergency caller.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the emergency caller. |
| location | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The location of the emergency caller. |
| phoneNumber | String | The phone number of the emergency caller. |
| tenantId | String | The tenant ID of the emergency caller. |
| upn | String | The user principal name of the emergency caller. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emergencyCallerInfo",
  "displayName": "String",
  "location": {"@odata.type": "microsoft.graph.location"},
  "phoneNumber": "String",
  "tenantId": "String",
  "upn": "String"
}
```
