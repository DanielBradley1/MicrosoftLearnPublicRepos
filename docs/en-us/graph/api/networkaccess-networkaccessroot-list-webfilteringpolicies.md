<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-webfilteringpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# List webFilteringPolicy objects

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of [webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) objects.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.Read.All | NetworkAccess.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.Read.All | NetworkAccess.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/webFilteringPolicies
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/webFilteringPolicies
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicy",
      "id": "252156ed-6901-389c-4cba-f4aa8856a307",
      "name": "Block social networking sites",
      "description": "Blocks access to selected social networking destinations",
      "version": "1.0",
      "lastModifiedDateTime": "2026-09-09T08:53:02Z",
      "settings": {
        "@odata.type": "microsoft.graph.networkaccess.webFilteringPolicySettings"
      }
    }
  ]
}
```
