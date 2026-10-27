<!-- Source: https://learn.microsoft.com/en-us/graph/api/appmanagementaudit-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# Get appManagementAudit

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the properties of an [appManagementAudit](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementaudit?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AuditLog.Read.All and Directory.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AuditLog.Read.All and Directory.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Reports Reader
- Security Administrator
- Security Reader

## HTTP request

```http
GET /auditLogs/directoryAudits/microsoft.graph.appManagementAudit/{id}
```

You can also retrieve the object through the base collection:

```http
GET /auditLogs/directoryAudits/{id}
```

## Optional query parameters

This method doesn't support any OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [appManagementAudit](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementaudit?view=graph-rest-beta) object in the response body.

## Example

### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/auditLogs/directoryAudits/microsoft.graph.appManagementAudit/B2C_491230e0-ffbd-44d0-ae95-914bb5534bf8
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.appManagementAudit",
  "id": "B2C_491230e0-ffbd-44d0-ae95-914bb5534bf8",
  "category": "ApplicationManagement",
  "appliedAppManagementPolicyRestrictions": [
    {
      "restrictionType": "passwordLifetime",
      "restrictionState": "audit",
      "restrictionResult": "allowed",
      "auditResult": "wouldHaveBeenAllowed",
      "policyId": "8b653f97-8314-45ec-95d4-97de6ccd4841",
      "policyType": "app",
      "restrictionDetails": {
        "maxLifeTime": "P180D"
      },
      "attemptedChanges": {}
    }
  ]
}
```
