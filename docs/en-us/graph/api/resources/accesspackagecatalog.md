<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# accessPackageCatalog resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package catalog is a container for zero or more access packages. Microsoft Entra entitlement management includes a built-in catalog named **General**.

An access package catalog might also have linked resources that are used in those access packages to provide access. To view or change the membership of catalog-scoped roles, use the [role assignments](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) API with the entitlement management RBAC provider.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-catalogs?view=graph-rest-1.0) | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) collection | Retrieve a list of accessPackageCatalog objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-catalogs?view=graph-rest-1.0) | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | Create a new accessPackageCatalog object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-get?view=graph-rest-1.0) | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | Read properties and relationships of an accessPackageCatalog object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-update?view=graph-rest-1.0) | None | Update the properties of an accessPackageCatalog object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-delete?view=graph-rest-1.0) | None | Delete accessPackageCatalog. |
| **Access package catalog resources** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0) | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) collection | Retrieve a list of accessPackageResource objects in a catalog. |
| **Access package catalog resource roles** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resourceroles?view=graph-rest-1.0) | [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) collection | Retrieve a list of accessPackageResourceRole objects in a catalog. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogType | accessPackageCatalogType | Whether the catalog is created by a user or entitlement management. The possible values are: `userManaged`, `serviceDefault`, `serviceManaged`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | The description of the access package catalog. |
| displayName | String | The display name of the access package catalog. |
| id | String | Read-only. |
| isExternallyVisible | Boolean | Whether the access packages in this catalog can be requested by users outside of the tenant. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| state | accessPackageCatalogState | Has the value `published` if the access packages are available for management. The possible values are: `unpublished`, `published`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackages | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) collection | The access packages in this catalog. Read-only. Nullable. |
| resources | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) collection | Access package resources in this catalog. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageCatalog",
  "catalogType": "String",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isExternallyVisible": "Boolean",
  "modifiedDateTime": "String (timestamp)",
  "state": "String",
}
```
