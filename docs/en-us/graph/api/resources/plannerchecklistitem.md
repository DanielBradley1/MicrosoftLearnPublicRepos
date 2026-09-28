<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-08 -->

# plannerChecklistItem resource type

Namespace: microsoft.graph

The **plannerChecklistItem** resource represents an item in the checklist of a task. The checklist on a task is represented by the [checklistItems object](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitems?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isChecked | Boolean | Value is `true` if the item is checked and `false` otherwise. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Read-only. User ID by which this is last modified. |
| lastModifiedDateTime | DateTimeOffset | Read-only. Date and time at which this is last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| orderHint | String | Used to set the relative order of items in the checklist. The format is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| title | String | Title of the checklist item |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isChecked": true,
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "orderHint": "String",
  "title": "String"
}
```
