<!-- Source: https://learn.microsoft.com/en-us/graph/api/pagetemplate-delete?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-31 -->

# Delete pageTemplate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a [pageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/pagetemplate?view=graph-rest-beta) from the templates folder in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /sites/{site-id}/pageTemplates/{pageTemplate-id}/microsoft.graph.pageTemplate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token} Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| *if-match* | etag. If this request header is included and the eTag provided doesn't match the current tag on the item, a `412 Precondition Failed` response is returned and the item isn't deleted. |

## Request body

Don't supply a request body with this method.

## Response

If successful, this method returns a `204 No Content` HTTP response. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/beta/sites/dd00d52e-0db7-4d5f-8269-90060ac688d1/pageTemplates/7bf14f9b-8764-4e54-bc5a-ee7d83dd09f7/microsoft.graph.pageTemplate
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/sites/dd00d52e-0db7-4d5f-8269-90060ac688d1/pageTemplates/7bf14f9b-8764-4e54-bc5a-ee7d83dd09f7/microsoft.graph.pageTemplate')
	.version('beta')
	.delete();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
