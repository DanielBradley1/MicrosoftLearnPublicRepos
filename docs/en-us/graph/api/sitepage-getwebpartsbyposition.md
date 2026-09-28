<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-getwebpartsbyposition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# sitePage: getWebPartsByPosition

Namespace: microsoft.graph

Get a collection of [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) by providing [webPartPosition](https://learn.microsoft.com/en-us/graph/api/resources/webpartposition?view=graph-rest-1.0) information.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP request

```http
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitepage/getWebPartsByPosition
```

## Function parameters

In the request URL, provide one or more following parameters with a valid value.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| columnId | Double | Indicates the identifier of the column where the WebPart located. Only works if `horizontalSectionId` is provided. |
| horizontalSectionId | Double | Indicates the horizontal section where the WebPart located. |
| isInVerticalSection | Boolean | Indicate whether the WebPart is contained in the current vertical section. |
| webPartIndex | Double | The index of the current WebPart. Represents the order of WebPart in the current column or section. Only works if either `columnId` or `isInVerticalSection` is provided. |

## Optional query parameters

This method supports the `$expand`, `$filter`, and `$select` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following is an example of a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/getWebPartsByPosition?isInVerticalSection=true
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getWebPartsByPosition = await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage/getWebPartsByPosition?isInVerticalSection=true')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.textWebPart",
      "id": "d79d70af-27ea-4208-8dce-23c3bf678664",
      "innerHtml": "<h2>How do you get started?</h2>"
    }
  ]
}
```
