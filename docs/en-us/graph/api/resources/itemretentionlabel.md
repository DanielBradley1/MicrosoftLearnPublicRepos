<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemretentionlabel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# itemRetentionLabel resource type

Namespace: microsoft.graph

Groups retention and compliance-related properties on an item into a single structure. Currently, supported only for [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isLabelAppliedExplicitly | Boolean | Specifies whether the label is applied explicitly on the item. `True` indicates that the label is applied explicitly; otherwise, the label is inherited from its parent. Read-only. |
| labelAppliedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user who applied the label. Read-only. |
| labelAppliedDateTime | DateTimeOffset | The date and time when the label was applied on the item. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| name | String | The retention label on the document. Read-write. |
| retentionSettings | [retentionLabelSettings](https://learn.microsoft.com/en-us/graph/api/resources/retentionlabelsettings?view=graph-rest-1.0) | The retention settings enforced on the item. Read-write. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isLabelAppliedExplicitly": "Boolean",
  "labelAppliedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "labelAppliedDateTime": "String (timestamp)",
  "name": "String",
  "retentionSettings": { "@odata.type": "microsoft.graph.retentionLabelSettings" }
}
```
