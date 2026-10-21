<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-post-workbooks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create workbook

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) with a server-generated ID.

To deploy a workbook with a stable, client-selected GUID, use [Update workbook](https://learn.microsoft.com/en-us/graph/api/security-workbook-update?view=graph-rest-beta) instead.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Workbooks.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Workbooks.ReadWrite.All | Not available. |

The tenant must be active and onboarded to use the Workbooks APIs. The delegated work or school and application permissions require administrator consent. Delegated access also requires the signed-in user to have the applicable Microsoft Defender XDR Unified RBAC authorization. Personal Microsoft accounts aren't supported.

## HTTP request

```http
POST /security/workbooks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.security.workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) object.

You can specify the following properties when creating a **workbook**.

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [microsoft.graph.security.workbookContent](https://learn.microsoft.com/en-us/graph/api/resources/security-workbookcontent?view=graph-rest-beta) | The workbook's complete JSON document. Supply a JSON object, not a JSON-encoded string. Required. |
| name | String | The display name of the workbook. Maximum length is 256 characters. Required. |

Don't supply **id**, **etag**, **createdByUpn**, **lastUpdatedByUpn**, **createdAtDateTime**, or **updatedAtDateTime**. The service generates the ID and sets the concurrency and audit properties.

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.workbook](https://learn.microsoft.com/en-us/graph/api/resources/security-workbook?view=graph-rest-beta) object in the response body.

The `Location` header contains the new workbook's Microsoft Graph URL. The `ETag` header contains the current concurrency token, which you can use unchanged as the `If-Match` value in a subsequent [update](https://learn.microsoft.com/en-us/graph/api/security-workbook-update?view=graph-rest-beta).

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/security/workbooks
Content-Type: application/json

{
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
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: https://graph.microsoft.com/beta/security/workbooks/ba989c62-af63-b8de-286d-7474ec579357
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
