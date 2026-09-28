<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooksortfield?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# workbookSortField resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a condition in a sorting operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ascending | Boolean | Represents whether the sorting is done in an ascending fashion. |
| color | string | Represents the color that is the target of the condition if the sorting is on font or cell color. |
| dataOption | string | Represents additional sorting options for this field. The possible values are: `Normal`, `TextAsNumber`. |
| icon | [workbookIcon](https://learn.microsoft.com/en-us/graph/api/resources/workbookicon?view=graph-rest-beta) | Represents the icon that is the target of the condition if the sorting is on the cell's icon. |
| key | int | Represents the column \(or row, depending on the sort orientation\) that the condition is on. Represented as an offset from the first column \(or row\). |
| sortOn | string | Represents the type of sorting of this condition. The possible values are: `Value`, `CellColor`, `FontColor`, `Icon`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "ascending": true,
  "color": "string",
  "dataOption": "string",
  "key": 1024,
  "sortOn": "string"
}
```
