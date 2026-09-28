<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageResourceScope resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package resource scope is a reference to a scope within a resource, for those resources that have multiple scopes.

You can determine the access package resource scope, for a resource that has roles already added to an access package, by using [list accessPackageResourceRoleScopes](https://learn.microsoft.com/en-us/graph/api/accesspackage-list-resourcerolescopes?view=graph-rest-1.0) to return a collection of [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) objects.

If the resource is in an access package catalog but hasn't yet had its roles added to an access package, you can determine the access package resource scope by using [list accessPackageResources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0) and including `$expand=scopes` in the query.

In entitlement management, this object is configured in the following properties and relationships:

- **resourceScopes** relationship of [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0)
- **scopes** relationship of \[[accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the scope. |
| displayName | String | The display name of the scope. |
| id | String | Read-only. |
| isRootScope | Boolean | True if the scopes are arranged in a hierarchy and this is the top or root scope of the resource. |
| originId | String | The unique identifier of the resource in the origin system. If a Microsoft Entra group, originId is the identifier of the group. Supports `$filter` \(`eq`\). |
| originSystem | String | The type of the resource in the origin system, such as `SharePointOnline`, `AadApplication`, `AadGroup`, `AzureResources`, or `CustomDataProvidedResource`. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resource | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isRootScope": true,
  "originId": "String",
  "originSystem": "String"
}
```
