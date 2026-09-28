<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/localadminpasswordsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# localAdminPasswordSettings resource type

Namespace: microsoft.graph

Represents the policy scope of the Microsoft Entra tenant that controls the Local Admin Password Solution \(LAPS\) setting. Configured in the **localAdminPassword** property of [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Specifies whether LAPS is enabled. The default value is `false`. An admin can set it to true to enable Local Admin Password Solution \(LAPS\) within their organization. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.localAdminPasswordSettings",
  "isEnabled": "Boolean"
}
```
