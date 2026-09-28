<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timecardevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-04 -->

# timeCardEvent resource type

Namespace: microsoft.graph

Represents a specific [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) event.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dateTime | DateTimeOffset | The time the entry is recorded. |
| isAtApprovedLocation | Boolean | Indicates whether this action happens at an approved location. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Notes about the **timeCardEvent**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.timeCardEvent",
  "dateTime": "String (timestamp)",
  "isAtApprovedLocation": "Boolean",
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  }
}
```
