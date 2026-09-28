<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/staffavailabilityitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# staffAvailabilityItem resource type

Namespace: microsoft.graph

Represents the available and busy time slots of a Microsoft Bookings [staff member](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityItems | [availabilityItem](https://learn.microsoft.com/en-us/graph/api/resources/availabilityitem?view=graph-rest-1.0) collection | Each item in this collection indicates a slot and the status of the staff member. |
| staffId | String | The ID of the staff member. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "availabilityItems": [{"@odata.type": "microsoft.graph.availabilityItem"}],
  "staffId": "String"
}
```
