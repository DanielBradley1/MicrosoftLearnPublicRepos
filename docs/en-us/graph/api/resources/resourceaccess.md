<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourceaccess?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# resourceAccess resource type

Namespace: microsoft.graph

Object used to specify an OAuth 2.0 permission scope or an app role that an application requires, through the **resourceAccess** property of the [requiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | Guid | The unique identifier of an [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) or [delegated permission](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) exposed by the resource application. For delegated permissions, this should match the **id** property of one of the [delegated permissions](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) in the **oauth2PermissionScopes** collection of the resource application's [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). For app roles \(application permissions\), this should match the **id** property of an [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) in the **appRoles** collection of the resource application's [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |
| type | String | Specifies whether the **id** property references a [delegated permission](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) or an [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) \(application permission\). The possible values are: `Scope` \(for delegated permissions\) or `Role` \(for app roles\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "Guid",
  "type": "String"
}
```
