<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/includetarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# includeTarget resource type

Namespace: microsoft.graph

Defines the users and groups that are included in a set of changes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the entity targeted. |
| targetType | authenticationMethodTargetType | The kind of entity targeted. The possible values are: `user`, `group`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.includeTarget",
  "id": "String (identifier)",
  "targetType": "String"
}
```
