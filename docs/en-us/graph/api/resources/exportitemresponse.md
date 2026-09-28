<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exportitemresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# exportItemResponse resource type

Namespace: microsoft.graph

Represents the result of an export operation performed by the [exportItems](https://learn.microsoft.com/en-us/graph/api/mailbox-exportitems?view=graph-rest-1.0) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeKey | String | The version of the item. |
| data | Stream | Data that represents an item in a Base64-encoded opaque stream. |
| error | [mailTipsError](https://learn.microsoft.com/en-us/graph/api/resources/mailtipserror?view=graph-rest-1.0) | An error that occurs during an action. |
| itemId | String | The unique identifier of the item. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exportItemResponse",
  "changeKey": "String",
  "data": "String",
  "error": {"@odata.type": "microsoft.graph.mailTipsError"},
  "itemId": "String"
}
```
