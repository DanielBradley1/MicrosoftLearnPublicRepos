<!-- Source: https://learn.microsoft.com/en-us/graph/api/devicetemplate-post-owners?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-17 -->

# Add deviceTemplate owner

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Add a new owner to a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object. Owners are granted permissions to enable or disable devices and update properties, such as **alternativeNames**, for the devices created from the device template. As an owner, no other administrator roles are necessary to create, update, or delete devices from this template, as well as to add or remove template owners. Owners added via this API are returned in a [list device owners](https://learn.microsoft.com/en-us/graph/api/devicetemplate-list-owners?view=graph-rest-beta) request. There can be a maximum of 100 owners on a device template.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DeviceTemplate.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DeviceTemplate.ReadWrite.All | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Cloud Device Administrator
- IoT Device Administrator
- Users - owners of the device template object

## HTTP request

```http
POST /directory/templates/deviceTemplates/{id}/owners/$ref
```

> **Note:** The `{id}` in the request URL is the value of the **id** property of the **deviceTemplate**.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.id | String | The object identifier of the target user or service principal, in the following format: `https://graph.microsoft.com/beta/users/{id}` or `https://graph.microsoft.com/beta/serviceprincipals/{id}`. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

For more information, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/directory/templates/deviceTemplates/2d62b12a-0163-457d-9796-9602e9807e1/owners/$ref
Content-Type: application/json

{
  "@odata.id": "https://graph.microsoft.com/beta/users/00001111-aaaa-2222-bbbb-3333cccc4444"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
  '@odata.id': 'https://graph.microsoft.com/beta/users/00001111-aaaa-2222-bbbb-3333cccc4444'
};

await client.api('/directory/templates/deviceTemplates/2d62b12a-0163-457d-9796-9602e9807e1/owners/$ref')
	.version('beta')
	.post(directoryObject);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
