<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/averagecomparativescore?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# averageComparativeScore resource type

Namespace: microsoft.graph

Contains tenant-level scores for [Microsoft Secure Score](https://learn.microsoft.com/en-us/graph/api/resources/securescore?view=graph-rest-1.0) based on scopes such as average by industry vertical and average by company seat size, and on control categories like identity, data, device, apps, and infrastructure.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| averageScore | Double | Average score within specified basis. |
| basis | String | Scope type. The possible values are: `AllTenants`, `TotalSeats`, `IndustryTypes`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "averageScore": "Double",
  "basis": "String"
}
```
