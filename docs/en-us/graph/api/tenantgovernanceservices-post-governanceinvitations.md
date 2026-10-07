<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-post-governanceinvitations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Create governanceInvitation

Namespace: microsoft.graph

Create a new [governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) to establish a governance relationship with a governed tenant. Invitations provide an alternative mechanism to governance requests for initiating relationships.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-Invitation.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). *Tenant Governance Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /directory/tenantGovernance/governanceInvitations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) object.

You can specify the following properties when creating a **governanceInvitation**.

| Property | Type | Description |
| :--- | :--- | :--- |
| governingTenantId | String | The Microsoft Entra tenant ID of the governing tenant. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.governanceInvitation](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governanceinvitation?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/directory/tenantGovernance/governanceInvitations
Content-Type: application/json

{
  "governingTenantId": "aaaabbbb-0000-cccc-1111-dddd2222eeee"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
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
