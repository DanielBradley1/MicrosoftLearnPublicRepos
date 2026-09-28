<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookformatprotection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookFormatProtection resource type

Namespace: microsoft.graph

Represents the format protection of a range object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookformatprotection-get?view=graph-rest-1.0) | [workbookFormatProtection](https://learn.microsoft.com/en-us/graph/api/resources/workbookformatprotection?view=graph-rest-1.0) | Read the properties and relationships of a workbookFormatProtection object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/workbookformatprotection-update?view=graph-rest-1.0) | [workbookFormatProtection](https://learn.microsoft.com/en-us/graph/api/resources/workbookformatprotection?view=graph-rest-1.0) | Update a workbookFormatProtection object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| formulaHidden | Boolean | Indicates whether Excel hides the formula for the cells in the range. A null value indicates that the entire range doesn't have uniform formula hidden setting. |
| locked | Boolean | Indicates whether Excel locks the cells in the object. A null value indicates that the entire range doesn't have uniform lock setting. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "formulaHidden": true,
  "locked": true
}
```
