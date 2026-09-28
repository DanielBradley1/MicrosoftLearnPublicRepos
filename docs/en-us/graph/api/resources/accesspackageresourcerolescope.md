<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# accessPackageResourceRoleScope resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package resource role scope is a reference to both a scope within a resource, and a role in that resource for that scope. An access package has access package resource role scopes for the resources in its catalog that are relevant to that access package. When a subject receives an access package assignment, the subject is provisioned with the role in that scope of each access package resource role scope.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackage-list-resourcerolescopes?view=graph-rest-1.0) | [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) collection | Retrieve a list of **accessPackageResourceRoleScope** objects for an access package. |
| [Create](https://learn.microsoft.com/en-us/graph/api/accesspackage-post-resourcerolescopes?view=graph-rest-1.0) | [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) | Create a new **accessPackageResourceRoleScope** object for an access package. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accesspackage-delete-resourcerolescopes?view=graph-rest-1.0) | None | Delete an **accessPackageResourceRoleScope** object from an access package. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| id | String | Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| role | [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) | Read-only. Nullable. |
| scope | [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-1.0) | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "createdDateTime":"String (timestamp)",
   "id":"String (identifier)",
   "role":{
      "id":"String (identifier)",
      "displayName":"String",
      "originSystem":"String",
      "originId":"String"
   },
   "scope":{
      "id":"String (identifier)",
      "displayName":"String",
      "description":"String",
      "originId":"String (identifier)",
      "originSystem":"String"
   }
}
```
