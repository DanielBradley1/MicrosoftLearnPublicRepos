<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-workbook-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Get workbook

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a [workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) by its ID.

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
GET /security/workbooks/{workbookId}
```

## Optional query parameters

This method supports the `$select` OData query parameter to choose the properties to return. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.security.workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) object in the response body.

The response's `ETag` header identifies the current version of the workbook. For a conditional [update](https://learn.microsoft.com/en-us/graph/api/security-workbook-update?view=graph-rest-beta), copy this value unchanged into the `If-Match` header, including the `W/` prefix and quotation marks.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/security/workbooks/ba989c62-af63-b8de-286d-7474ec579357
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json
ETag: W/"0x8DE000000000001"

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
  },
  "createdByUpn": "adelev@contoso.com",
  "lastUpdatedByUpn": "adelev@contoso.com",
  "createdAtDateTime": "2026-09-22T10:00:00Z",
  "updatedAtDateTime": "2026-09-22T10:00:00Z"
}
```
