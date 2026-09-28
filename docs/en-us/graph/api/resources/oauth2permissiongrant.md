<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# oAuth2PermissionGrant resource type

Namespace: microsoft.graph

Represents the delegated permissions that have been granted to an application's service principal.

Delegated permissions grants can be created as a result of a user consenting an application's request to access an API, or created directly.

Delegated permissions are sometimes referred to as "OAuth 2.0 scopes" or "scopes".

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-list?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Retrieve a list of delegated permission grants. |
| [Get](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-get?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) | Read a single delegated permission grant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-post?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) | Create a delegated permission grant. |
| [Update](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-update?view=graph-rest-1.0) | None | Update oAuth2PermissionGrant object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-delete?view=graph-rest-1.0) | None | Delete a delegated permission grant. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-delta?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) | Get newly created, updated, or deleted **oauth2permissiongrant** objects without performing a full read of the entire resource collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientId | String | The object **id** \(*not* **appId**\) of the client [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) for the application that's authorized to act on behalf of a signed-in user when accessing an API. Required. Supports `$filter` \(`eq` only\). |
| consentType | String | Indicates if authorization is granted for the client application to impersonate all users or only a specific user. *AllPrincipals* indicates authorization to impersonate all users. *Principal* indicates authorization to impersonate a specific user. Consent on behalf of all users can be granted by an administrator. Nonadmin users might be authorized to consent on behalf of themselves in some cases, for some delegated permissions. Required. Supports `$filter` \(`eq` only\). |
| id | String | Unique identifier for the **oAuth2PermissionGrant**. Read-only. |
| principalId | String | The **id** of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) on behalf of whom the client is authorized to access the resource, when **consentType** is *Principal*. If **consentType** is *AllPrincipals* this value is null. Required when **consentType** is *Principal*. Supports `$filter` \(`eq` only\). |
| resourceId | String | The **id** of the resource [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) to which access is authorized. This identifies the API that the client is authorized to attempt to call on behalf of a signed-in user. Supports `$filter` \(`eq` only\). |
| scope | String | A space-separated list of the claim values for delegated permissions that should be included in access tokens for the resource application \(the API\). For example, `openid User.Read GroupMember.Read.All`. Each claim value should match the **value** field of one of the delegated permissions defined by the API, listed in the **oauth2PermissionScopes** property of the resource [service principal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). Must not exceed 3,850 characters in length. |

## Relationships

None.

This resource supports using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/oauth2permissiongrant-delta?view=graph-rest-1.0) function.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientId": "string",
  "consentType": "string",
  "id": "string (identifier)",
  "principalId": "string",
  "resourceId": "string",
  "scope": "string"
}
```

## Related content

- [Grant or revoke delegated permissions using Microsoft Graph](https://learn.microsoft.com/en-us/graph/permissions-grant-via-msgraph?pivots=grant-delegated-permissions)
