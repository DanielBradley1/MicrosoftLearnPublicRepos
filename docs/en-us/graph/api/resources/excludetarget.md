<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# excludeTarget resource type

Namespace: microsoft.graph

Represents the users or groups of users that are excluded from a policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The object identifier of a Microsoft Entra user or group. |
| targetType | authenticationMethodTargetType | The type of the authentication method target. The possible values are: `user`, `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.excludeTarget",
  "id": "String (identifier)",
  "targetType": "String"
}
```
