<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# alertComment resource type

Namespace: microsoft.graph.security

An analyst-generated comment that is associated with an alert or incident.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment text. |
| createdByDisplayName | String | The person or app name that submitted the comment. |
| createdDateTime | DateTimeOffset | The time when the comment was submitted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.alertComment",
  "comment": "String",
  "createdByDisplayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
