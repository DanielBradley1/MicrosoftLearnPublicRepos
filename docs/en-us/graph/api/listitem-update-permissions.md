<!-- Source: https://learn.microsoft.com/en-us/graph/api/listitem-update-permissions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# Update permission on a listItem

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-beta) object on a [list item](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-beta).

> **Note:** You can't use this method to update a user listitem permission.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All |

## HTTP request

```http
PATCH /sites/{site-id}/lists/{list-id}/items/{item-id}/permissions/{permission-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-beta) object.

## Response

If successful, this method returns a `200 OK` response code and a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

---

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "2",
  "@deprecated.GrantedToIdentities": "GrantedToIdentities has been deprecated. Refer to GrantedToIdentitiesV2",
  "roles": [
    "read"
  ],
  "grantedToIdentities": [
    {
      "application": {
        "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
        "displayName": "Fabrikam Dashboard App"
      }
    }
  ],
  "grantedToIdentitiesV2": [
    {
      "application": {
        "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
        "displayName": "Fabrikam Dashboard App"
      }
    }
  ]
}
```
