<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/featuretarget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# featureTarget resource type

Namespace: microsoft.graph

Defines a single group, Microsoft Entra role, or administrative unit that is included or excluded in the settings specified in the [authenticationMethodFeatureConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodfeatureconfiguration?view=graph-rest-1.0) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the entity that's targeted in the include or exclude rule, or `all_users` to target all users. |
| targetType | featureTargetType | The kind of entity that's targeted. The possible values are: `group`, `administrativeUnit`, `role`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.featureTarget",
  "id": "String (identifier)",
  "targetType": "String"
}
```
