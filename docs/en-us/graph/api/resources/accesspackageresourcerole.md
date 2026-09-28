<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# accessPackageResourceRole resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package resource role is a reference to a role defined in a resource. These roles are automatically present after a resource is added to an access package catalog. A group can have two roles, one for the owner and another for the member. An application's roles are defined the application manifest. The roles along with the scopes of a resource in a catalog can be retrieved by [listing the catalog resources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0) and expanding the `roles` and `scopes` of the resource. Those references to the role and scope can be used after creating an access package in that catalog, to specify the roles of each of the catalog's resources into which an access package should deliver, by [creating an access package resource role scope](https://learn.microsoft.com/en-us/graph/api/accesspackage-post-resourcerolescopes?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resourceroles?view=graph-rest-1.0) | [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) collection | Retrieve a list of accessPackageResourceRole objects for a catalog. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description for the resource role. |
| displayName | String | The display name of the resource role such as the role defined by the application. |
| id | String | Read-only. |
| originId | String | The unique identifier of the resource role in the origin system. For a SharePoint Online site, the originId is the sequence number of the role in the site. |
| originSystem | String | The type of the resource in the origin system, such as `SharePointOnline`, `AadApplication`, `AzureResources`, or `AadGroup`. |
| type | roleType | The role type for the Azure resource role. The possible values are: `active`, `eligible`, `application`, `delegated`, `unknownFutureValue`. The values `active` and `eligible` are only supported where **originSystem** is `AzureResources` while `application` and `delegated` aren't currently implemented. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resource | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource.

```json
{
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "originId": "String",
  "originSystem": "String",
  "type": "String"
}
```
