<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourceaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# unifiedRbacResourceAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an operation that an authorized principal is allowed to perform.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedrbacresourcenamespace-list-resourceactions?view=graph-rest-beta) | [unifiedRbacResourceAction](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourceaction?view=graph-rest-beta) collection | Get a list of the [unifiedRbacResourceAction](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourceaction?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedrbacresourceaction-get?view=graph-rest-beta) | [unifiedRbacResourceAction](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourceaction?view=graph-rest-beta) | Read the properties and relationships of an [unifiedRbacResourceAction](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourceaction?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionVerb | String | HTTP method for the action, such as `DELETE`, `GET`, `PATCH`, `POST`, `PUT`, or `null`. Supports `$filter` \(`eq`\) but not for `null` values. |
| description | String | Description for the action. Supports `$filter` \(`eq`\). |
| id | String | Unique identifier for an action within the resource namespace, such as `microsoft.insights-programs-update-patch`. can't include slash character \(`/`\). Case insensitive. Required. Supports `$filter` \(`eq`\). |
| isPrivileged | Boolean | Flag indicating if the action is a sensitive resource action. Applies only for actions in the `microsoft.directory` resource namespace. Read-only. Supports `$filter` \(`eq`\). |
| name | String | Name for the action within the resource namespace, such as `microsoft.insights/programs/update`. Can include slash character \(`/`\). Case insensitive. Required. Supports `$filter` \(`eq`\). |
| resourceScopeId | String | Not implemented. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRbacResourceAction",
  "id": "String (identifier)",
  "actionVerb": "String",
  "description": "String",
  "isPrivileged": "Boolean",
  "name": "String",
  "resourceScopeId": "String"
}
```
