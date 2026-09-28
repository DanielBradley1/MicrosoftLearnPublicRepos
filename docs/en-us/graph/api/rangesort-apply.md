<!-- Source: https://learn.microsoft.com/en-us/graph/api/rangesort-apply?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# RangeSort: apply

Namespace: microsoft.graph

Perform a sort operation.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/drive/items/{id}/workbook/names/{name}/range/sort/apply
POST /me/drive/root:/{item-path}:/workbook/names/{name}/range/sort/apply
POST /me/drive/items/{id}/workbook/worksheets/{id|name}/range(address='<address>')/sort/apply
POST /me/drive/root:/{item-path}:/workbook/worksheets/{id|name}/range(address='<address>')/sort/apply
POST /me/drive/items/{id}/workbook/tables/{id|name}/columns/{id|name}/range/sort/apply
POST /me/drive/root:/{item-path}:/workbook/tables/{id|name}/columns/{id|name}/range/sort/apply
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
| fields | WorkbookSortField collection | The list of conditions to sort on. |
| matchCase | Boolean | Optional. Indicates whether to have the casing determine string ordering. |
| hasHeaders | Boolean | Optional. Indicates whether the range has a header. |
| orientation | string | Optional. Indicates whether the operation is sorting rows or columns. The possible values are: `Rows`, `Columns`. |
| method | string | Optional. Indicates the ordering method used for Chinese characters. The possible values are: `PinYin`, `StrokeCount`. |

## Response

If successful, this method returns `200 OK` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/names/{name}/range/sort/apply
Content-type: application/json

{
  "fields": [
    {
      "key": 99,
      "sortOn": "sortOn-value",
      "ascending": true,
      "color": "color-value",
      "dataOption": "dataOption-value",
      "icon": {
        "set": "set-value",
        "index": 99
      }
    }
  ],
  "matchCase": true,
  "hasHeaders": true,
  "orientation": "orientation-value",
  "method": "method-value"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const apply = {
  fields: [
    {
      key: 99,
      sortOn: 'sortOn-value',
      ascending: true,
      color: 'color-value',
      dataOption: 'dataOption-value',
      icon: {
        set: 'set-value',
        index: 99
      }
    }
  ],
  matchCase: true,
  hasHeaders: true,
  orientation: 'orientation-value',
  method: 'method-value'
};

await client.api('/me/drive/items/{id}/workbook/names/{name}/range/sort/apply')
	.post(apply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
