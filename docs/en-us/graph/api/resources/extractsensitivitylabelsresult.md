<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/extractsensitivitylabelsresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# extractSensitivityLabelsResult resource type

Namespace: microsoft.graph

Represents the response format for the [extractSensitivityLabels](https://learn.microsoft.com/en-us/graph/api/driveitem-extractsensitivitylabels?view=graph-rest-1.0) API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| labels | [sensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/sensitivitylabelassignment?view=graph-rest-1.0) collection | List of sensitivity labels assigned to a file. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.extractSensitivityLabelsResult",
  "labels": [
    {
      "@odata.type": "microsoft.graph.sensitivityLabelAssignment"
    }
  ]
}
```
