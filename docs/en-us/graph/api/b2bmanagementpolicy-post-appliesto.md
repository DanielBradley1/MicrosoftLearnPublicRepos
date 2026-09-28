<!-- Source: https://learn.microsoft.com/en-us/graph/api/b2bmanagementpolicy-post-appliesto?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Assign b2bManagementPolicy appliesTo

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Add [directoryObjects](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) on which [b2bManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2bmanagementpolicy?view=graph-rest-beta) object needs to be applied. The b2bManagementPolicy can only be applied to [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) and [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta) resources.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Administrator* is the only role supported for this operation.

## HTTP request

```http
POST /policies/b2bManagementPolicies/{b2bManagementPolicyId}/appliesTo/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code and a [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/policies/b2bManagementPolicies/f596ef0d-42f9-0359-1aaa-12d02b38802a/appliesTo/$ref
Content-Type: application/json

{
  "@odata.id": " https://graph.microsoft.com/beta/directoryObjects/a6c034b8-621b-dee3-6abb-52cbce801fe9"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const directoryObject = {
  '@odata.id': ' https://graph.microsoft.com/beta/directoryObjects/a6c034b8-621b-dee3-6abb-52cbce801fe9'
};

await client.api('/policies/b2bManagementPolicies/f596ef0d-42f9-0359-1aaa-12d02b38802a/appliesTo/$ref')
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
