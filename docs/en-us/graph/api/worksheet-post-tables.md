<!-- Source: https://learn.microsoft.com/en-us/graph/api/worksheet-post-tables?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Create table

Namespace: microsoft.graph

Use this API to create a new Table.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/drive/items/{id}/workbook/worksheets/{id|name}/tables/add
POST /me/drive/root:/{item-path}:/workbook/worksheets/{id|name}/tables/add
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Workbook-Session-Id | Workbook session ID that determines if changes are persisted or not. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| Address | string | Range address. If you're calling this API off of `worksheets/{id or name}/tables/add` path, there's no need to for sheet name prefix in the address. However, if you're calling this off of `workbook/tables/add` path, then supply the sheet name on which the table needs to be created \(example: `sheet1!A1:D4`\) |
| hasHeaders | Boolean | Boolean value that indicates whether the range has column labels. If the source doesn't contain headers \(when this property set to false\), Excel will automatically generate header shifting the data down by one row. |

## Response

If successful, this method returns `201 Created` response code and [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/worksheets/{id|name}/tables/{id}/add
Content-type: application/json

{
  "address": "A1:D8",
  "hasHeaders": false
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "99",
  "name": "name-value",
  "showHeaders": true,
  "showTotals": true,
  "style": "style-value"
}
```
