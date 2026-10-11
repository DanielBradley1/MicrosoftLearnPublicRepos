<!-- Source: https://learn.microsoft.com/en-us/graph/api/permission-revokegrants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-08 -->

# permission: revokeGrants

Namespace: microsoft.graph

Revoke access to a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) or [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) granted via a sharing link by removing the specified [driveRecipient](https://learn.microsoft.com/en-us/graph/api/resources/driverecipient?view=graph-rest-1.0) entries from the link.

Recipients who already redeemed the link and recipients who only received an invitation both lose access. Revoking a grant removes the recipient from this sharing link only; it doesn't remove any access the recipient has through a different sharing link, a direct grant, or membership in a group that has access.

Note

This action is only supported on sharing links that are scoped to specific users.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

## HTTP request

```http
POST /drives/{drive-id}/items/{item-id}/permissions/{perm-id}/revokeGrants
POST /groups/{group-id}/drive/items/{item-id}/permissions/{perm-id}/revokeGrants
POST /me/drive/items/{item-id}/permissions/{perm-id}/revokeGrants
POST /sites/{site-id}/drive/items/{item-id}/permissions/{perm-id}/revokeGrants
POST /sites/{site-id}/lists/{list-id}/items/{listItem-id}/driveItem/permissions/{perm-id}/revokeGrants
POST /users/{user-id}/drive/items/{item-id}/permissions/{perm-id}/revokeGrants
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| grantees | [driveRecipient](https://learn.microsoft.com/en-us/graph/api/resources/driverecipient?view=graph-rest-1.0) collection | Required. A collection of recipients whose access to the sharing link is revoked. |

## Response

If successful, this action returns a `200 OK` response code and a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) in the response body that represents the updated state of the sharing link.

The **grantedToIdentitiesV2** property of the returned permission lists the recipients on the link after the specified grants are revoked.

This action applies only to sharing links. It can't be used to revoke a direct grant on an item; use [Delete permission](https://learn.microsoft.com/en-us/graph/api/permission-delete?view=graph-rest-1.0) instead. Supplying the identifier of a permission that isn't a sharing link returns a `400 Bad Request` response code.

The sharing link must be scoped to specific users. Links whose **scope** is `anonymous` or `organization` don't track individual grantees. Because these links have no individual grants to revoke, the request returns a `400 Bad Request` response code.

For more information about how errors are returned, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Request

The following example shows how to revoke access for a single user on a sharing link.

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/016GVDAP3RCQS5VBQHORFIVU2ZMOSBL25U/permissions/2687a7e0-1b4d-4656-ae32-a4ea393321e1/revokeGrants
Content-Type: application/json

{
  "grantees": [
    {
      "email": "ryan@contoso.com"
    }
  ]
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "2687a7e0-1b4d-4656-ae32-a4ea393321e1",
  "roles": ["write"],
  "grantedToIdentitiesV2": [
    {
      "user": {
        "id": "e6842c7e-33a1-4207-8b5a-2710922ac2b2",
        "displayName": "Megan Bowen"
      },
      "siteUser": {
        "id": "12",
        "displayName": "Megan Bowen",
        "loginName": "Megan Bowen"
      }
    }
  ],
  "link": {
    "type": "edit",
    "scope": "users",
    "webUrl": "https://contoso-my.sharepoint.com/personal/ellen_contoso_com/..."
  }
}
```
