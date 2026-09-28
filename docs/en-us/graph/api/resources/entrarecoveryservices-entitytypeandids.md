<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-entitytypeandids?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# entityTypeAndIds resource type

Namespace: microsoft.graph.entraRecoveryServices

Specifies an entity type and a list of entity IDs to scope recovery operations. Used within [recoveryJobEntityNameAndIdsFilter](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobentitynameandidsfilter?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| entityIds | String collection | The list of entity IDs for the specified entity type. |
| entityType | [microsoft.graph.entraRecoveryServices.resourceTypeName](https://learn.microsoft.com/en-us/graph/api/resources/enums-entrarecoveryservices?view=graph-rest-1.0) | The type of directory entity. The possible values are: `user`, `group`, `conditionalAccessPolicy`, `namedLocationPolicy`, `authenticationMethodPolicy`, `authorizationPolicy`, `authenticationStrengthPolicy`, `application`, `servicePrincipal`, `unknownFutureValue`, `oAuth2PermissionGrant`, `appRoleAssignment`, `organization`. You must use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `oAuth2PermissionGrant`, `appRoleAssignment`, `organization`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.entityTypeAndIds",
  "entityType": "String",
  "entityIds": [
    "String"
  ]
}
```
