<!-- Source: https://learn.microsoft.com/en-us/graph/api/workbookrange-resizedrange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-05 -->

# workbookRange: resizedRange

Namespace: microsoft.graph

Get a range object similar to the current range object, but with its bottom-right corner expanded \(or contracted\) by some number of rows and columns.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/drive/items/{id}/workbook/worksheets/{id}/range/resizedRange(deltaRows={n}, deltaColumns={n})
POST /me/drive/root:/{item-path}:/workbook/worksheets/{id}/range/resizedRange(deltaRows={n}, deltaColumns={n})
```

## Function parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| deltaRows | Int32 | The number of rows by which to expand the bottom-right corner, relative to the current range. Use a positive number to expand the range, or a negative number to decrease it |
| deltaColumns | Int32 | The number of columns by which to expand the bottom-right corner, relative to the current range. Use a positive number to expand the range, or a negative number to decrease it. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Workbook-Session-Id | Workbook session ID that determines if changes are persisted or not. Optional. |

## Request body

Don't supply a request body for this method.

### Response

If successful, this method returns a `200 OK` response code and a [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/drive/root/workbook/worksheets/{id}/range/resizedRange(deltaRows={n}, deltaColumns={n})
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "address": "address-value",
  "addressLocal": "addressLocal-value",
  "cellCount": 99,
  "columnCount": 99,
  "columnHidden": true,
  "columnIndex": 99
}
```
