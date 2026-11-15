<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicylink-list-policy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Get policy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) associated with a web filtering policy link.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policy
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

If successful, this method returns a `200 OK` response code and a [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/filteringProfiles/d734d2de-f2df-4b4a-8c4c-5111f8878275/policies/70405a6c-b823-4521-8981-de9d08a21f8f/policy
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicy",
  "id": "283f06b1-1d6a-c2f9-b285-4974e1c7c7b1",
  "name": "Block social networking sites",
  "description": "Blocks access to selected social networking destinations",
  "version": "1.0"
}
```
