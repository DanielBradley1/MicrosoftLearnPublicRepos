<!-- Source: https://learn.microsoft.com/en-us/graph/api/print-list-recentprintershares?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# List recentPrinterShares

Namespace: microsoft.graph

Get a list of [printerShares](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) recently used by the signed-in user.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrinterShare.ReadBasic.All | PrinterShare.Read.All, PrinterShare.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/print/recentPrinterShares
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

### Exceptions

The following operators are not supported: `$count`, `$orderby`, and `$search`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) objects in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/me/print/recentPrinterShares
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let recentPrinterShares = await client.api('/me/print/recentPrinterShares')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('74157b7f-9fa7-41b6-9ee9-97c382ba1189')/print/recentPrinterShares",
    "value": [
        {
            "id": "04ccb929-9e71-4aef-9f83-36e4a7fd53e3",
            "name": "4c1cf503-efde-48fb-9db7-12c159da0ab3_FTPrinter",
            "displayName": "4c1cf503-efde-48fb-9db7-12c159da0ab3_FTPrinter",
            "viewPoint": {
                "lastUsedDateTime": "2023-06-12T05:11:07Z"
            }
        }
  ]
}
```
