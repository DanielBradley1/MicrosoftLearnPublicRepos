<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegedaccessroot-list-customextensions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# List roleManagementCustomCalloutExtensions

Namespace: microsoft.graph

Get a list of roleManagementCustomCalloutExtension objects configured for Privileged Identity Management \(PIM\).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedAccess-CustomExt.Read.All | PrivilegedAccess-CustomExt.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedAccess-CustomExt.Read.All | PrivilegedAccess-CustomExt.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Privileged Role Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
GET /identityGovernance/privilegedAccess/customExtensions
```

## Optional query parameters

This method supports the `$filter` \(`eq`\) OData query parameter on the **resourceType** property and the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) objects in the response body.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/privilegedAccess/customExtensions
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/privilegedAccess/customExtensions",
  "value": [
    {
      "@odata.type": "#microsoft.graph.roleManagementCustomCalloutExtension",
      "id": "a1b2c3d4-e5f6-4a5b-8c9d-0e1f2a3b4c5d",
      "displayName": "Role assignment ticket validation",
      "description": "Validates ticket information against the service desk",
      "resourceType": "entraRoles",
      "type": "preApproval",
      "customAttributes": ["department", "costCenter"],
      "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://api.contoso.com/webhooks/role-assignments"
      },
      "clientConfiguration": {
        "timeoutInMilliseconds": 10000,
        "maximumRetries": 3
      },
      "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://api.contoso.com/00001111-aaaa-2222-bbbb-3333cccc4444"
      }
    }
  ]
}
```
