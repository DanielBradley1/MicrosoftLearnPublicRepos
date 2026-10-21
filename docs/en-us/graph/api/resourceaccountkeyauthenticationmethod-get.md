<!-- Source: https://learn.microsoft.com/en-us/graph/api/resourceaccountkeyauthenticationmethod-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-14 -->

# Get resourceAccountKeyAuthenticationMethod

Namespace: microsoft.graph

Read the properties and relationships of a [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-ResourceKey.Read.All | UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite.All, UserAuthMethod-ResourceKey.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-ResourceKey.Read.All | UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite.All, UserAuthMethod-ResourceKey.ReadWrite.All |

## HTTP request

```http
GET /users/{id | userPrincipalName}/authentication/resourceAccountKeyAuthenticationMethods/{resourceAccountKeyAuthenticationMethodId}
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) object in the response body.

If the credential ID doesn't exist, this method returns a `404 Not Found` error code with an error code of `resourceNotFound`.

## Examples

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/users/0a3e7ad0-8d1b-4e25-ad43-5b7c7c2b5f6f/authentication/resourceAccountKeyAuthenticationMethods/aB3dE5fG7hI9jK1lM3nO5pQ7rS9tU1vW3xY5zA7bC9d1
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('0a3e7ad0-8d1b-4e25-ad43-5b7c7c2b5f6f')/authentication/resourceAccountKeyAuthenticationMethods/$entity",
  "@odata.type": "#microsoft.graph.resourceAccountKeyAuthenticationMethod",
  "id": "aB3dE5fG7hI9jK1lM3nO5pQ7rS9tU1vW3xY5zA7bC9d1",
  "displayName": "Conference Room MTR-W",
  "createdDateTime": "2026-05-28T19:55:40Z",
  "isUsable": true,
  "methodUsabilityReason": "EnabledByPolicy",
  "lastUsedDateTime": "2026-06-15T08:30:00Z"
}
```
