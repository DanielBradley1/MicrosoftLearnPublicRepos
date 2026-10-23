<!-- Source: https://learn.microsoft.com/en-us/graph/api/authentication-list-resourceaccountkeyauthenticationmethods?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-14 -->

# List resourceAccountKeyAuthenticationMethods

Namespace: microsoft.graph

Retrieve a list of the [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) objects and their properties for a resource account.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-ResourceKey.Read.All | UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite.All, UserAuthMethod-ResourceKey.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-ResourceKey.Read.All | UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite.All, UserAuthMethod-ResourceKey.ReadWrite.All |

## HTTP request

```http
GET /users/{id | userPrincipalName}/authentication/resourceAccountKeyAuthenticationMethods
```

## Optional query parameters

This method supports the `$select`, `$top`, `$skip`, and `$count` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [resourceAccountKeyAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccountkeyauthenticationmethod?view=graph-rest-1.0) objects in the response body.

If the user has no resource account key credentials, this method returns a `404 Not Found` error code with an error code of `resourceNotFound`.

## Examples

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/users/0a3e7ad0-8d1b-4e25-ad43-5b7c7c2b5f6f/authentication/resourceAccountKeyAuthenticationMethods
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('0a3e7ad0-8d1b-4e25-ad43-5b7c7c2b5f6f')/authentication/resourceAccountKeyAuthenticationMethods",
  "value": [
    {
      "@odata.type": "#microsoft.graph.resourceAccountKeyAuthenticationMethod",
      "id": "aB3dE5fG7hI9jK1lM3nO5pQ7rS9tU1vW3xY5zA7bC9d1",
      "displayName": "Conference Room MTR-W",
      "createdDateTime": "2026-05-28T19:55:40Z",
      "isUsable": true,
      "methodUsabilityReason": "EnabledByPolicy",
      "lastUsedDateTime": "2026-06-15T08:30:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.resourceAccountKeyAuthenticationMethod",
      "id": "cD5eF7gH9iJ1kL3mN5oP7qR9sT1uV3wX5yZ7aB9cD1e1",
      "displayName": "Teams Phone Room MTR-W",
      "createdDateTime": "2026-05-28T19:53:14Z",
      "isUsable": true,
      "methodUsabilityReason": "EnabledByPolicy",
      "lastUsedDateTime": "2026-06-14T14:22:10Z"
    }
  ]
}
```
