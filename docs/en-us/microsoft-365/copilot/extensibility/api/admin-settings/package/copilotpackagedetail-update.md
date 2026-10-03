<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-update -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Update Copilot package

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Update a [copilotPackageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagedetail) object.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotPackages.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not available. | Not available. |

## HTTP request

```http
PATCH https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}.` Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |

## Request body

In the request body, supply a JSON representation of a [copilotPackageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagedetail) object.

The following properties can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| `allowedUsersAndGroups` | [packageAccessEntity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageaccessentity) collection | Users/groups for whom the package is available. |
| `acquireUsersAndGroups` | [packageAccessEntity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageaccessentity) collection | Users/groups for whom the package is deployed. |
| `availableTo` | [packageAllowStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#packageallowstatus-enumeration) | Enum value specifying which users or groups within the tenant can access this package. Required if updating `allowedUsersAndGroups`. |
| `deployedTo` | [packageAcquireStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#packageacquirestatus-enumeration) | Enum value indicating the deployment scope of the package. Required if updating `acquireUsersAndGroups`. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/copilot/admin/catalog/packages/P_19ae1zz1-56bc-505a-3d42-156df75a4xxy
Content-Type: application/json

{
  "allowedUsersAndGroups": [
    {
      "resourceType": "user",
      "resourceId": "5d9fa31e-626e-45fb-b6e7-d8f1f11933a9"
    },
    {
      "resourceType": "group",
      "resourceId": "65d7d8fb-1e24-4ba8-92cd-8c502d830113"
    }
  ],
  "acquireUsersAndGroups": [
    {
      "resourceType": "user",
      "resourceId": "5d9fa31e-626e-45fb-b6e7-d8f1f11933a9"
    },
    {
      "resourceType": "group",
      "resourceId": "65d7d8fb-1e24-4ba8-92cd-8c502d830113"
    }
  ],
  "availableTo": "allowedForSome",
  "deployedTo" : "acquiredForSome"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
