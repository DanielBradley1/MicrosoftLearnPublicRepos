<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-05 -->

# resourceSpecificPermissionGrant resource type

Namespace: microsoft.graph

Declares the permission that has been granted to a specific Microsoft Entra app for an instance of a resource in Microsoft Graph.

For more information about granting apps consent to access a specific instance of a resource, see [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List permission grants of a chat](https://learn.microsoft.com/en-us/graph/api/chat-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List permissions that have been granted in a specific chat. |
| [List permission grants of a group](https://learn.microsoft.com/en-us/graph/api/group-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List resource-specific permissions that have been granted in a specific [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). |
| [List permission grants of a team](https://learn.microsoft.com/en-us/graph/api/team-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List permissions that have been granted in a specific team. |
| [List permission grants of a user](https://learn.microsoft.com/en-us/graph/api/user-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List resource-specific permissions that have been granted to a specific [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientId | string | ID of the Microsoft Entra app that has been granted access. Read-only. |
| clientAppId | string | ID of the service principal of the Microsoft Entra app that has been granted access. Read-only. |
| deletedDateTime | dateTimeOffset | Not used. |
| id | string | The unique identifier of the resource-specific permission grant. Read-only. |
| resourceAppId | string | ID of the Microsoft Entra app that is hosting the resource. Read-only. |
| permissionType | string | The type of permission. The possible values are: `Application`, `Delegated`. Read-only. |
| permission | string | The name of the resource-specific permission. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "deletedDateTime": "dateTimeOffset",
  "clientId": "string",
  "clientAppId": "string",
  "resourceAppId": "string",
  "permissionType": "string",
  "permission": "string"
}
```
