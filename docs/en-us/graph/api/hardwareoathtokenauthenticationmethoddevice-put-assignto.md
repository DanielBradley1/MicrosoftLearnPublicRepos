<!-- Source: https://learn.microsoft.com/en-us/graph/api/hardwareoathtokenauthenticationmethoddevice-put-assignto?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Assign user a hardware OATH token

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Assign a hardware OATH token, represented by a [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object, to a user. Self-service operations are supported.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

## Permissions acting on self

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthenticationMethod.ReadWrite | UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## Permissions acting on another user

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthenticationMethod.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthenticationMethod.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Administrator
- Privileged Authentication Administrator

When users manage their own authentication methods, the system prompts them to complete multi-factor authentication \(MFA\) if they last authenticated more than 10 minutes ago in the current session.

## HTTP request

Assign a hardware OATH authentication method for yourself.

```http
PUT /me/authentication/hardwareOathMethods/{hardwareOathAuthenticationMethodId}/device/assignTo/$ref
```

Assign a hardware OATH authentication method for another user.

```http
PUT /users/{usersId}/authentication/hardwareOathMethods/{hardwareOathAuthenticationMethodId}/device/assignTo/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) object.

You can specify the following properties when creating a **user**.

| Property | Type | Description |
| :--- | :--- | :--- |
| odata.id | String | A link to the user entity with using objectId as key. Example: `https://graph.microsoft.com/beta/users/{usersId}` |

## Response

If successful, this method returns a `204 No Content` response code and a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/beta/users/{usersId}/authentication/hardwareOathMethods/{hardwareOathAuthenticationMethodId}/device/assignTo/$ref
Content-Type: application/json

{
    "@odata.id": "https://graph.microsoft.com/beta/users/0cadbf92-####-####-####-############"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const user = {
    '@odata.id': 'https://graph.microsoft.com/beta/users/0cadbf92-####-####-####-############'
};

await client.api('/users/{usersId}/authentication/hardwareOathMethods/{hardwareOathAuthenticationMethodId}/device/assignTo/$ref')
	.version('beta')
	.put(user);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
