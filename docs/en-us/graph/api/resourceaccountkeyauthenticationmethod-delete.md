<!-- Source: https://learn.microsoft.com/en-us/graph/api/resourceaccountkeyauthenticationmethod-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-14 -->

# Delete resourceAccountKeyAuthenticationMethod

Namespace: microsoft.graph

Delete a [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) object.

Warning

Deleting a resource account key authentication method cannot be undone. After deletion, the shared device will no longer be able to authenticate silently using this credential.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-ResourceKey.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-ResourceKey.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |

## HTTP request

```http
DELETE /users/{id | userPrincipalName}/authentication/resourceAccountKeyAuthenticationMethods/{resourceAccountKeyAuthenticationMethodId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

If the credential ID doesn't exist, this method returns a `404 Not Found` error code with an error code of `resourceNotFound`.

## Examples

#### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/users/0a3e7ad0-8d1b-4e25-ad43-5b7c7c2b5f6f/authentication/resourceAccountKeyAuthenticationMethods/aB3dE5fG7hI9jK1lM3nO5pQ7rS9tU1vW3xY5zA7bC9d1
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
