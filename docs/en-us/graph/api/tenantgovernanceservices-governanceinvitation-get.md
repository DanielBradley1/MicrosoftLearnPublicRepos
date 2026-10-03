<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governanceinvitation-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Get governanceInvitation

Namespace: microsoft.graph

Read the properties of a [governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-Invitation.Read.All | TenantGovernance-Invitation.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TenantGovernance-Invitation.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Tenant Governance Administrator
- Tenant Governance Relationship Administrator
- Global Reader
- Tenant Governance Reader
- Tenant Governance Relationship Reader

## HTTP request

```http
GET /directory/tenantGovernance/governanceInvitations/{governanceInvitationId}
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/directory/tenantGovernance/governanceInvitations/aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.governanceInvitation",
  "id": "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb",
  "governingTenantId": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
  "governedTenantId": "bbbbcccc-1111-dddd-2222-eeee3333ffff",
  "governingTenantName": "Contoso, Inc",
  "governedTenantName": "Fabrikam",
  "createdDateTime": "2026-01-01T18:25:09.4212828Z",
  "expirationDateTime": "2026-01-31T18:25:09.4212828Z"
}
```
