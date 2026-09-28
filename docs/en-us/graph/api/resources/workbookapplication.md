<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookapplication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# workbookApplication resource type

Namespace: microsoft.graph

Represents the Excel application that manages the workbook.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookapplication-get?view=graph-rest-1.0) | [workbookApplication](https://learn.microsoft.com/en-us/graph/api/resources/workbookapplication?view=graph-rest-1.0) | Read properties and relationships of workbookApplication object. |
| [Calculate](https://learn.microsoft.com/en-us/graph/api/workbookapplication-calculate?view=graph-rest-1.0) | None | Recalculate all currently opened workbooks in Excel. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calculationMode | string | Returns the calculation mode used in the workbook. The possible values are: `Automatic`, `AutomaticExceptTables`, `Manual`. |

## Relationships

None.

## JSON representation

```json
{
  "calculationMode": "string"
}
```
