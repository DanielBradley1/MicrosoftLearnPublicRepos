<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-get -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Get Copilot package details

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Retrieves detailed information for a specific agent by ID.

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
| Delegated \(work or school account\) | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |

## HTTP request

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages/{id}
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}.` Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [copilotPackageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagedetail) object in the response body.

### Example

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages/abc
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages/abc
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#copilot/admin/catalog/packages/$entity",
  "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
  "displayName": "Contoso Sales Agent",
  "type": "custom",
  "shortDescription": "Short description for package abc",
  "isBlocked": false,
  "supportedHosts": ["teams", "outlook", "sharePoint"],
  "lastModifiedDateTime": "2025-10-06T00:07:20.146Z",
  "publisher": "Contoso",
  "availableTo": "all",
  "deployedTo": "some",
  "elementTypes": ["declarativeAgent"],
  "platform": "teams",
  "version": "1.2.3",
  "manifestVersion": "2.0",
  "manifestId": "contoso-sales-agent",
  "appId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
  "assetId": "asset-00042",
  "longDescription": "This is a detailed description for package abc. It provides comprehensive information about the package functionality, features, and usage scenarios.",
  "categories": [
    "Development",
    "Productivity",
    "Tools"
  ],
  "sensitivity": "general",
  "allowedUsersAndGroups": [
    {
      "resourceId": "user-123",
      "resourceType": "user"
    },
    {
      "resourceId": "group-456",
      "resourceType": "group"
    }
  ],
  "acquireUsersAndGroups": [],
  "elementDetails": [
    {
      "elementType": "bot",
      "elements": [
        {
          "id": "bot-001",
          "definition": "{\"botId\":\"303e399a-cecc-4511-ad38-82970baa288b\",\"scopes\":[\"personal\"],\"isNotificationOnly\":true,\"supportsCalling\":false,\"supportsVideo\":false,\"supportsFiles\":false}"
        }
      ]
    },
    {
      "elementType": "declarativeAgent",
      "elements": [
        {
          "id": "dcp-001",
          "definition": "{\"id\":\"dcp-001\",\"version\":\"v2.1\",\"name\":\"Contoso Sales Agent\"}"
        }
      ]
    }
  ]
}
```
