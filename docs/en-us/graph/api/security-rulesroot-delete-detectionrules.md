<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-rulesroot-delete-detectionrules?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# Delete detectionRule

Namespace: microsoft.graph.security

Delete a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomDetection.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomDetection.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a role that grants the permissions required for this operation. Custom detection rules use the Microsoft Defender XDR Unified role-based access control \(RBAC\) model. The following roles are supported:

- **Detection tuning \(Manage\)** - A [Microsoft Defender XDR Unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/custom-permissions-details) permission that grants manage access to detections in the Microsoft Defender portal, including custom detections, alert tuning, and threat indicators of compromise.
- **Security Administrator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-administrator) that grants manage permissions across Microsoft Defender portals and services.
- **Security Operator** - A [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json#security-operator). Sufficient for managing custom detection rules only when role-based access control is turned off in Microsoft Defender for Endpoint. If RBAC is configured, the **Manage Security Settings** permission for Defender for Endpoint is also required.

Additional workload-specific permissions might be required to manage rules that target data from specific Defender workloads \(for example, Defender for Endpoint, Defender for Office 365\). For more information, see [Required permissions for managing custom detections](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules#required-permissions-for-managing-custom-detections).

## HTTP request

```http
DELETE /security/rules/detectionRules/{detectionRuleId}
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
DELETE https://graph.microsoft.com/v1.0/security/rules/detectionRules/4790e8ec-9488-3dde-c3a6-be0c4ba14cf9
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
