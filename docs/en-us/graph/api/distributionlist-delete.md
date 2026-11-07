<!-- Source: https://learn.microsoft.com/en-us/graph/api/distributionlist-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# Delete distributionList

Namespace: microsoft.graph

Delete a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Contacts.ReadWrite | Not available. |
| Application | Contacts.ReadWrite | Not available. |

## HTTP request

```http
DELETE /me/distributionLists/{distributionList-id}
DELETE /users/{id | userPrincipalName}/distributionLists/{distributionList-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/me/distributionLists/AAMkAGI2THVSAAA=
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
