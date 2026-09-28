<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# accessPackageResourceRequest resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package resource request is a request to add a [resource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) to a catalog so that the roles of the resource can be used in one or more of the catalog's access packages, update a resource in a catalog to have different attribute requirements, or to remove a resource from a catalog that is no longer needed by the access packages.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-resourcerequests?view=graph-rest-1.0) | [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0) collection | Retrieve a list of **accessPackageResourceRequest** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-resourcerequests?view=graph-rest-1.0) | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0) | Add, update, or remove a **accessPackageResource** from a catalog. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | Read-only. |
| requestType | accessPackageRequestType | The type of the request. Use `adminAdd` to add a resource, if the caller is an administrator or resource owner, `adminUpdate` to update a resource, or `adminRemove` to remove a resource. |
| state | accessPackageRequestState | The outcome of whether the service was able to add the resource to the catalog. The value is `delivered` if the resource was added or removed, and `deliveryFailed` if it couldn't be added or removed. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| catalog | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | Read-only. |
| resource | [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) | Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "requestType": "String",
  "state": "String"
}
```
