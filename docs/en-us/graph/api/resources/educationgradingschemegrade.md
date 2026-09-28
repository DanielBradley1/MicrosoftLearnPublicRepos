<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationgradingschemegrade?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-30 -->

# educationGradingSchemeGrade resource type

Namespace: microsoft.graph

Represents an individual grade range that contributes to a grading scheme.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultPercentage | Int32 | The midpoint of the grade range. |
| displayName | String | The name of this individual grade. |
| minPercentage | Int32 | The minimum percentage of the total points needed to achieve this grade. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationGradingSchemeGrade",
  "defaultPercentage": "Int32",
  "displayName": "String",
  "minPercentage": "Int32"
}
```
