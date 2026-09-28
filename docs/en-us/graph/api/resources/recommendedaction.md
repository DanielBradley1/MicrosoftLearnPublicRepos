<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recommendedaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# recommendedAction resource type

Namespace: microsoft.graph

Represents recommended actions for a tenant based on the attack simulation and training campaign to improve its security posture.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionWebUrl | String | Web URL to the recommended action. |
| potentialScoreImpact | Double | Potential improvement in the tenant security score from the recommended action. |
| title | String | Title of the recommended action. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.recommendedAction",
  "actionWebUrl": "String",
  "potentialScoreImpact": "Double",
  "title": "String"
}
```
