<!-- Source: https://learn.microsoft.com/en-us/graph/api/bundle-removeitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# Remove item from bundle

Namespace: microsoft.graph

Remove an item from a [bundle](https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Files.ReadWrite.All |
| Application | Not supported. | Not supported. |

## HTTP request

```http
DELETE /drive/bundles/{bundle-id}/children/{item-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body with for method.

## Response

If successful, this method returns a `204 No Content` response code.

For information about error responses, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/v1.0/drive/bundles/{bundle-id}/children/{item-id}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/drive/bundles/{bundle-id}/children/{item-id}')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
