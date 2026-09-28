<!-- Source: https://learn.microsoft.com/en-us/graph/api/federatedidentitycredential-upsert?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# Upsert federatedIdentityCredential

Namespace: microsoft.graph

Create a new [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object for an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) if it doesn't exist, or update the properties of an existing [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. By [configuring a trust relationship](https://learn.microsoft.com/en-us/azure/active-directory/develop/workload-identity-federation-create-trust) between your Microsoft Entra application registration and the identity provider for your compute platform, you can use tokens issued by that platform to authenticate with Microsoft identity platform and call APIs in the Microsoft ecosystem. Maximum of 20 objects can be added to an application.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Application.ReadWrite.All | Not available. |
| Application | Application.ReadWrite.OwnedBy | Application.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- A non-admin member user with default user permissions - for applications they own
- Application Developer - for applications they own
- Cloud Application Administrator
- Application Administrator

## HTTP request

You can address the application using either its **id** or **appId**. **id** and **appId** are referred to as the **Object ID** and **Application \(Client\) ID**, respectively, in app registrations in the Microsoft Entra admin center.

```http
PATCH /applications/{id}/federatedIdentityCredentials(name='{name}')

PATCH /applications(appId='{appId}')/federatedIdentityCredentials(name='{name}')
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Prefer | `create-if-missing`. Required for upsert behavior, otherwise the request is treated as an update operation. |

## Request body

In the request body, supply a JSON representation of the [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object. The following table lists the properties that are required when you create the [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0). Note that the **name** property is required as part of the request URL.

| Property | Type | Description |
| :--- | :--- | :--- |
| audiences | String collection | The audience that can appear in the external token. This field is mandatory and should be set to `api://AzureADTokenExchange` for Microsoft Entra ID. It says what Microsoft identity platform should accept in the `aud` claim in the incoming token. This value represents Microsoft Entra ID in your external identity provider and has no fixed value across identity providers - you may need to create a new application registration in your identity provider to serve as the audience of this token. This field can only accept a single value and has a limit of 600 characters. Required. |
| issuer | String | TThe URL of the external identity provider and must match the issuer claim of the external token being exchanged. The combination of the values of **issuer** and **subject** must be unique on the app. It has a limit of 600 characters. Required. |
| subject | String | Required. The identifier of the external software workload within the external identity provider. Like the audience value, it has no fixed format, as each identity provider uses their own - sometimes a GUID, sometimes a colon delimited identifier, sometimes arbitrary strings. The value here must match the sub claim within the token presented to Microsoft Entra ID. It has a limit of 600 characters. The combination of **issuer** and **subject** must be unique on the app. |

## Response

If successful, if an application object with **name** doesn't exist, this method returns a `201 Created` response code and a new [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object in the response body.

If an application object with **name** already exists, this method updates the [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) object and returns a `204 No Content` response code.

## Examples

### Example 1: Create a new federatedIdentityCredential if it doesn't exist

The following example creates a federatedIdentityCredential because a federatedIdentityCredential with the specified **name** value doesn't exist.

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/applications(uniqueName='app-65278')/federatedIdentityCredentials(name='fic01-app-65278')
Content-Type: application/json

{
    "issuer": "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0",
    "subject": "a7d388c3-5e3f-4959-ac7d-786b3383006a",
    "audiences": [
        "api://AzureADTokenExchange"
    ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications('bcd7c908-1c4d-4d48-93ee-ff38349a75c8')/federatedIdentityCredentials/$entity",
    "id": "d9b7bf1e-429e-4678-8132-9b00c9846cc4",
    "name": "testing02fic01-app-65278",
    "issuer": "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0",
    "subject": "a7d388c3-5e3f-4959-ac7d-786b3383006a",
    "description": null,
    "audiences": [
        "api://AzureADTokenExchange"
    ]
}
```

### Example 2: Update an existing federatedIdentityCredential

The following example updates the federatedIdentityCredential because a federatedIdentityCredential with the specified **name** value exists.

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/applications(uniqueName='app-65278')/federatedIdentityCredentials(name='fic01-app-65278')
Content-Type: application/json
Prefer: create-if-missing

{
    "issuer": "https://login.microsoftonline.com/3d1e2be9-a10a-4a0c-8380-7ce190f98ed9/v2.0",
    "subject": "a7d388c3-5e3f-4959-ac7d-786b3383006a",
    "audiences": [
        "api://AzureADTokenExchange"
    ]
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
