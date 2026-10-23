<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-list-workbooks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List workbook objects

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [workbooks](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) in the tenant.

The response omits **content** by default. To retrieve workbook documents in the collection response, explicitly select **content**, for example, `$select=id,name,content`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Workbooks.Read.All | Workbooks.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Workbooks.Read.All | Workbooks.ReadWrite.All |

The tenant must be active and onboarded to use the Workbooks APIs. The delegated work or school and application permissions require administrator consent. Delegated access also requires the signed-in user to have the applicable Microsoft Defender XDR Unified RBAC authorization. Personal Microsoft accounts aren't supported.

## HTTP request

```http
GET /security/workbooks
```

## Optional query parameters

This method supports the `$select` OData query parameter to choose the properties to return. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

If a response contains `@odata.nextLink`, request that complete URL unchanged to retrieve the next page. Continue until the response no longer contains `@odata.nextLink`. Treat the skip token in the URL as opaque; don't decode it or construct a token yourself.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: List workbook metadata

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/security/workbooks
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.workbook",
      "id": "ba989c62-af63-b8de-286d-7474ec579357",
      "name": "Threat hunting overview",
      "createdByUpn": "adelev@contoso.com",
      "lastUpdatedByUpn": "adelev@contoso.com",
      "createdAtDateTime": "2026-09-22T10:00:00Z",
      "updatedAtDateTime": "2026-09-22T10:00:00Z"
    }
  ]
}
```

### Example 2: Include workbook content

#### Request

The following example selects the workbook ID, name, and complete content document.

```http
GET https://graph.microsoft.com/beta/security/workbooks?$select=id,name,content
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.workbook",
      "id": "ba989c62-af63-b8de-286d-7474ec579357",
      "name": "Threat hunting overview",
      "content": {
        "version": "1.0",
        "title": "Threat hunting overview",
        "items": [
          {
            "type": "text",
            "text": "Investigate recent security activity."
          }
        ],
        "settings": {
          "showTitle": true
        }
      }
    }
  ]
}
```
