<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# List packages

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Retrieves a list of all packages available in the tenant.

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
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}.` Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

### Optional query parameters

This method supports the `$filter` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. The following properties are supported with the `$filter` OData query parameter. For examples of using the `$filter` query parameter, see [Examples](#examples).

| Parameter | Type | Description |
| --- | --- | --- |
| `supportedHosts` | string | Filter by supported host \(`Copilot`, `Outlook`, `Teams`, `M365`\) |
| `elementTypes` | string | Filter by element type \(`Bots`, `DeclarativeAgent`, `CustomEngineAgent`\) |
| `lastModifiedDateTime` | datetime | Filter by last updated date/time |
| `platform` | string | Filter by platform \(`Copilot Studio`, `Microsoft 365 Copilot Agent Builder`\) |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [copilotPackage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage) objects in the response body.

### Examples

#### Example 1: List all packages

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Diligent Teams Document Uploader",
      "type": "external",
      "shortDescription": "Allows direct upload of documents from Microsoft Office into Diligent Teams for sharing",
      "isBlocked": false,
      "supportedHosts": ["outlook", "word", "excel", "powerPoint"],
      "lastModifiedDateTime": "2023-11-20T19:02:02.241Z",
      "publisher": "Diligent Corporation",
      "availableTo": "all",
      "deployedTo": "none",
      "elementTypes": ["officeAddIn"],
      "platform": "web",
      "version": "1.0.0",
      "manifestVersion": "1.1",
      "manifestId": "diligent-teams-uploader",
      "appId": "aaaaaaaa-1111-2222-3333-bbbbbbbbbbbb",
      "assetId": "asset-00001"
    }
  ]
}
```

#### Example 2: List packages filtered by supported host

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Word')
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Word')
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-cb65-505a-3d42-156df75a4xxy",
      "displayName": "Contoso Document Formatter",
      "type": "external",
      "shortDescription": "Formats Word documents according to company style guide",
      "isBlocked": false,
      "supportedHosts": ["Word"],
      "lastModifiedDateTime": "2025-10-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 3: List packages filtered by element type

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=elementTypes/any(h:h eq 'OfficeAddIns')
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=elementTypes/any(h:h eq 'OfficeAddIns')
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-505a-3492-9871-134df75a4xxy",
      "displayName": "Northwind Traders Account Lookup",
      "type": "external",
      "shortDescription": "Look up customer account details in Outlook and add them to email",
      "isBlocked": false,
      "supportedHosts": ["Outlook"],
      "lastModifiedDateTime": "2025-10-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 4: List packages by last updated date/time

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=lastModifiedDateTime gt 2026-01-01T00:00:00.0000000Z
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=lastModifiedDateTime gt 2026-01-01T00:00:00.0000000Z
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-01-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```

#### Example 5: List all agents

To list all agents, use a filter for `supportedHosts` that contains `Copilot`

##### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Copilot')
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/packages?$filter=supportedHosts/any(h:h eq 'Copilot')
```

##### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "P_19ae1zz1-56bc-505a-3d42-156df75a4xxy",
      "displayName": "Contoso HR Agent",
      "type": "custom",
      "shortDescription": "Agent that can answer HR questions",
      "isBlocked": false,
      "supportedHosts": ["Copilot"],
      "lastModifiedDateTime": "2026-01-06T00:07:20.1467852Z",
      "availableTo": "all",
      "deployedTo": "all"
    }
  ]
}
```
