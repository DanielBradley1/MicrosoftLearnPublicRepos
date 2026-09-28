<!-- Source: https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-userflowidentityproviders-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-21 -->

# Add a userFlowIdentityProvider

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Add an identity providers in a [b2cIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityUserFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityUserFlow.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identity/b2cUserFlows/{userflow-id}/userflowIdentityProviders/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON representation with the `id` of the [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta) you want to add. For more information about identity providers available for user flows, see the [identityProviders](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta) resource.

## Response

If successful, this method returns a `204 No Content` response code. If unsuccessful, a `4xx` error is returned with the specific error details.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/identity/b2cUserFlows/B2C_test_signin_signup/userflowIdentityProviders/$ref
Content-type: application/json

{
  "@odata.id": "https://graph.microsoft.com/beta/identity/identityProviders/{id}"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const identityProviderBase = {
  '@odata.id': 'https://graph.microsoft.com/beta/identity/identityProviders/{id}'
};

await client.api('/identity/b2cUserFlows/B2C_test_signin_signup/userflowIdentityProviders/$ref')
	.version('beta')
	.post(identityProviderBase);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
