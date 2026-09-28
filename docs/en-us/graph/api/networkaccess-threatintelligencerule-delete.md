<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencerule-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Delete threatIntelligenceRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a [threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
DELETE /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policyRules/{id}
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
DELETE https://graph.microsoft.com/beta/networkAccess/filteringProfiles/ab4f3459-c39d-4e99-b8d0-b1aee4726b84/policies/ac253559-37a0-4f72-b666-103420b94e38/policyRules/0823cb1e-644b-4585-80db-1c1055894ec7
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
