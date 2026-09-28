<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/riskuseractivity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# riskUserActivity resource type

Namespace: microsoft.graph

Represents the risk activities of a Microsoft Entra user as determined by Microsoft Entra ID Protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detail | [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-1.0) | For more information, see [riskDetail](https://learn.microsoft.com/en-us/graph/api/resources/riskdetail?view=graph-rest-1.0). |
| riskEventTypes | String collection | The type of risk event detected. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.riskUserActivity",
  "riskEventTypes": [
    "String"
  ],
  "detail": "String"
}
```
