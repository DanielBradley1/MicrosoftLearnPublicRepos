<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-26 -->

# appRoleAssignment resource type

Namespace: microsoft.graph

Used to record when a user, group, or service principal is assigned an app role for an app.

An app role assignment is a relationship between the assigned principal \(a user, a group, or a service principal\), a resource application \(the app's service principal\) and an app role defined on the resource application.

When the [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) that has been assigned to a principal has a nonempty **value** property, it's included in the **roles** claim of tokens where the subject is the assigned principal \(for example, SAML responses, ID tokens, access tokens identifying a signed-in user, or an access token identifying a service principal\). Applications and APIs use these claims as part of their authorization logic.

A user can be assigned an app role directly. If an app role is assigned to a group, direct members of the group are also considered to have been assigned the app role. When a user is assigned an app role for an application, a tile for that application is displayed in the user's [MyApps portal](https://learn.microsoft.com/en-us/azure/active-directory/user-help/my-apps-portal-end-user-access) and [Microsoft 365 app launcher](https://support.office.com/article/meet-the-office-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a).

An app role assignment where the assigned principal is a service principal is an [app-only permission](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent#permission-types) grant. When a user or admin consents to an app-only permission, an app role assignment is created where the assigned principal is the service principal for the client application, and the resource is the target API's service principal.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List app role assignments for a group](https://learn.microsoft.com/en-us/graph/api/group-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get a list of the [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) objects and their properties for a group. |
| [List app role assignments for a user](https://learn.microsoft.com/en-us/graph/api/user-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get a list of the [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) objects and their properties for a user. |
| [List app role assignments for a client service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get a list of the [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) objects and their properties for a client service principal. |
| [List app role assignments for users, groups, and client service principals for a resource service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get a list of the [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) objects and their properties for users, groups, and client service principals for a specified resource service principal. |
| [Grant app role to a group](https://learn.microsoft.com/en-us/graph/api/group-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Create a new [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object for a group. |
| [Grant app role to a user](https://learn.microsoft.com/en-us/graph/api/user-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Create a new [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object for a user. |
| [Grant app role to a client service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Create a new [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object for a client service principal. |
| [Grant app role assignment to user, group, or client service principal for a resource service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Create a new [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object to a user, group, or client service principal for a specified resource service principal. |
| [Get app role assignment](https://learn.microsoft.com/en-us/graph/api/approleassignment-get?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Get an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object assigned to a user, group, or client service principal for a resource service principal. |
| [Delete app role assignment for a group](https://learn.microsoft.com/en-us/graph/api/group-delete-approleassignments?view=graph-rest-1.0) | None | Delete an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object from a group. |
| [Delete app role assignment for a user](https://learn.microsoft.com/en-us/graph/api/user-delete-approleassignments?view=graph-rest-1.0) | None | Delete an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object from a user. |
| [Delete app role assignment for a client service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignments?view=graph-rest-1.0) | None | Delete an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object from a client service principal. |
| [Delete app role assignment for user, group, or client service principal to a resource service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignedto?view=graph-rest-1.0) | None | Delete an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object from a user, group, or client service principal for a specified resource service principal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appRoleId | Guid | The identifier \(**id**\) for the [app role](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) that's assigned to the principal. This app role must be exposed in the **appRoles** property on the resource application's service principal \(**resourceId**\). If the resource application hasn't declared any app roles, a default app role ID of `00000000-0000-0000-0000-000000000000` can be specified to signal that the principal is assigned to the resource app without any specific app roles. Required on create. |
| createdDateTime | DateTimeOffset | The time when the app role assignment was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| deletedDateTime | DateTimeOffset | The date and time when the app role assignment was deleted. Always `null` for an appRoleAssignment object that hasn't been deleted. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| id | String | A unique identifier for the **appRoleAssignment** key. Not nullable. Read-only. Supports `$filter` \(`eq` only\). |
| principalDisplayName | String | The display name of the user, group, or service principal that was granted the app role assignment. Maximum length is 256 characters. Read-only. Supports `$filter` \(`eq` and `startswith`\). |
| principalId | Guid | The unique identifier \(**id**\) for the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [security group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), or [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) being granted the app role. Security groups with dynamic memberships are supported. Required on create. |
| principalType | String | The type of the assigned principal. This can either be `User`, `Group`, or `ServicePrincipal`. Read-only. |
| resourceDisplayName | String | The display name of the resource app's service principal to which the assignment is made. Maximum length is 256 characters. |
| resourceId | Guid | The unique identifier \(**id**\) for the resource [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) for which the assignment is made. Required on create. Supports `$filter` \(`eq` only\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appRoleId": "Guid",
  "createdDateTime": "String (timestamp)",
  "deletedDateTime": "String (timestamp)",
  "id": "String",
  "principalDisplayName": "String",
  "principalId": "Guid",
  "principalType": "String",
  "resourceDisplayName": "String",
  "resourceId": "Guid"
}
```

## Related content

- [Grant or revoke app roles using Microsoft Graph](https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph?pivots=grant-application-permissions)
