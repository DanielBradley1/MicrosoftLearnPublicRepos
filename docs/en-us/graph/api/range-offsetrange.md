<!-- Source: https://learn.microsoft.com/en-us/graph/api/range-offsetrange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# Range: OffsetRange

Namespace: microsoft.graph

Gets an object that represents a range that's offset from the specified range. The dimension of the returned range matches this range. If the resulting range is forced outside the bounds of the worksheet grid, an exception is thrown.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/drive/items/{id}/workbook/names/{name}/range/offsetRange
GET /me/drive/root:/{item-path}:/workbook/names/{name}/range/offsetRange
GET /me/drive/items/{id}/workbook/worksheets/{id|name}/range(address='<address>')/offsetRange
GET /me/drive/root:/{item-path}:/workbook/worksheets/{id|name}/range(address='<address>')/offsetRange
GET /me/drive/items/{id}/workbook/tables/{id|name}/columns/{id|name}/range/offsetRange
GET /me/drive/root:/{item-path}:/workbook/tables/{id|name}/columns/{id|name}/range/offsetRange
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Workbook-Session-Id | Workbook session Id that determines if changes are persisted or not. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| rowOffset | Int32 | The number of rows \(positive, negative, or 0\) by which the range is to be offset. Positive values are offset downward, and negative values are offset upward. |
| columnOffset | Int32 | The number of columns \(positive, negative, or 0\) by which the range is to be offset. Positive values are offset to the right, and negative values are offset to the left. |

## Response

If successful, this method returns `200 OK` response code and [Range](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) object in the response body.

## Example

Here's an example of how to call this API.

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/names/{name}/range/offsetRange
Content-type: application/json

{
  "rowOffset": 3,
  "columnOffset": 5
}
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
  "columnIndex": 99,
  "valueTypes": "valueTypes-value"
}
```
