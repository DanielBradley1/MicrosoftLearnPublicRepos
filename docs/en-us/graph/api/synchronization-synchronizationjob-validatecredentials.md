<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-validatecredentials?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationJob: validateCredentials

Namespace: microsoft.graph

Validate that the credentials are valid in the tenant for a [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Synchronization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | Synchronization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator - to configure Microsoft Entra Cloud Sync

## HTTP request

```http
POST /servicePrincipals/{id}/synchronization/jobs/{id}/validateCredentials
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| useSavedCredentials | Boolean | When `true`, the `credentials` parameter will be ignored and the previously saved credentials \(if any\) will be validated instead. |
| credentials | [synchronizationSecretKeyStringValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationsecretkeystringvaluepair?view=graph-rest-1.0) collection | Credentials to validate. Ignored when the `useSavedCredentials` parameter is `true`. |

## Response

If validation is successful, this method returns a `204, No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{id}/validateCredentials
Content-type: application/json

{ 
    credentials: [ 
        { key: "UserName", value: "user@domain.com" },
        { key: "Password", value: "password-value" }
    ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const validateCredentials = {
    credentials: [ 
        { key: 'UserName', value: 'user@domain.com' },
        { key: 'Password', value: 'password-value' }
    ]
};

await client.api('/servicePrincipals/{id}/synchronization/jobs/{id}/validateCredentials')
	.post(validateCredentials);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
