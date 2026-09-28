<!-- Source: https://learn.microsoft.com/en-us/graph/api/authentication-post-fido2methods?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Create fido2AuthenticationMethod

Namespace: microsoft.graph

Create a new [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethod?view=graph-rest-1.0) object for a user. This API completes the registration of a FIDO2 security key \(passkey\) as part of the WebAuthn registration ceremony.

**Passkey registration flow:**

1. Call the [creationOptions](https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethod-creationoptions?view=graph-rest-1.0) function to retrieve WebAuthn credential creation options from Microsoft Entra ID.
2. Use the returned options to create a new credential in the browser or authenticator using the WebAuthn API.
3. POST the resulting public key credential to this API to complete registration.

Note

This API has the following known issues:

- It doesn't support provisioning of pre-registered passkeys. For more information, see [Known issue: Provisioning of pre-registred passkeys not supported](https://learn.microsoft.com/en-us/graph/known-issues#provisioning-of-pre-registred-passkeys-not-supported)
- Admins must enable **Allow self-service setup** in the FIDO2 authentication method policy to use the FIDO2 provisioning API. For more information, see [Known issue: FIDO2 provisioning API requires self-service setup to be enabled](https://learn.microsoft.com/en-us/graph/known-issues#fido2-provisioning-api-requires-self-service-setup-to-be-enabled).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-Passkey.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-Passkey.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Administrator
- Privileged Authentication Administrator

When users manage their own authentication methods, the system prompts them to complete multi-factor authentication \(MFA\) if they last authenticated more than 10 minutes ago in the current session.

## HTTP request

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
POST /users/{id}/authentication/fido2Methods
POST /me/authentication/fido2Methods
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethod?view=graph-rest-1.0) object.

You can specify the following properties when creating a **fido2AuthenticationMethod**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the FIDO2 security key. Optional. |
| publicKeyCredential | [webauthnPublicKeyCredential](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredential?view=graph-rest-1.0) | The WebAuthn public key credential that the authenticator created. Base64URL-encode all binary data without padding, as defined in [RFC 4648 Section 5](https://www.rfc-editor.org/rfc/rfc4648#section-5). This encoding applies to the credential **id**, **clientDataJSON**, and **attestationObject** properties. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [fido2AuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethod?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/users/99a1915f-70a7-4b67-9dca-64095b41be73/authentication/fido2Methods
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fido2AuthenticationMethod",
  "displayName": "My security key",
  "publicKeyCredential": {
    "@odata.type": "#microsoft.graph.webauthnPublicKeyCredential",
    "id": "OEVEMkQzNTctNzNEMi00RjEzLTk5MjYtODdGNjFCMjRBMzQy",
    "response": {
      "@odata.type": "#microsoft.graph.webauthnAuthenticatorAttestationResponse",
      "clientDataJSON": "eyJ0eXBlIjoid2ViYXV0aG4uY3JlYXRlIiwiY2hhbGxlbmdlIjoiUVRVMU16TkROekF0TmtNM05pMDBOVFJETFVKRFEwWXRSVFJFTURaQ05UQkZSVFJFIiwib3JpZ2luIjoiaHR0cHM6Ly9sb2dpbi5taWNyb3NvZnRvbmxpbmUuY29tIiwiY3Jvc3NPcmlnaW4iOmZhbHNlfQ",
      "attestationObject": "o2NmbXRkbm9uZWdhdHRTdG10oGhhdXRoRGF0YVikSZYN5YgOjGh0NBcPZHZgW4/krrmihjLHmVzzuoMdl2NdAAAAALraVWanqkAfvZZFYZpVEg0AIDhFRDJEMzU3LTczRDItNEYxMy05OTI2LTg3RjYxQjI0QTM0MqUBAgMmIAEhWCAMKJ7T4r8w5F6JGxJLJXNR0hV1MZF1aZ1F0pZXq5p5"
    },
    "clientExtensionResults": {
      "@odata.type": "#microsoft.graph.webauthnAuthenticationExtensionsClientOutputs"
    }
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fido2AuthenticationMethod = {
  '@odata.type': '#microsoft.graph.fido2AuthenticationMethod',
  displayName: 'My security key',
  publicKeyCredential: {
    '@odata.type': '#microsoft.graph.webauthnPublicKeyCredential',
    id: 'OEVEMkQzNTctNzNEMi00RjEzLTk5MjYtODdGNjFCMjRBMzQy',
    response: {
      '@odata.type': '#microsoft.graph.webauthnAuthenticatorAttestationResponse',
      clientDataJSON: 'eyJ0eXBlIjoid2ViYXV0aG4uY3JlYXRlIiwiY2hhbGxlbmdlIjoiUVRVMU16TkROekF0TmtNM05pMDBOVFJETFVKRFEwWXRSVFJFTURaQ05UQkZSVFJFIiwib3JpZ2luIjoiaHR0cHM6Ly9sb2dpbi5taWNyb3NvZnRvbmxpbmUuY29tIiwiY3Jvc3NPcmlnaW4iOmZhbHNlfQ',
      attestationObject: 'o2NmbXRkbm9uZWdhdHRTdG10oGhhdXRoRGF0YVikSZYN5YgOjGh0NBcPZHZgW4/krrmihjLHmVzzuoMdl2NdAAAAALraVWanqkAfvZZFYZpVEg0AIDhFRDJEMzU3LTczRDItNEYxMy05OTI2LTg3RjYxQjI0QTM0MqUBAgMmIAEhWCAMKJ7T4r8w5F6JGxJLJXNR0hV1MZF1aZ1F0pZXq5p5'
    },
    clientExtensionResults: {
      '@odata.type': '#microsoft.graph.webauthnAuthenticationExtensionsClientOutputs'
    }
  }
};

await client.api('/users/99a1915f-70a7-4b67-9dca-64095b41be73/authentication/fido2Methods')
	.post(fido2AuthenticationMethod);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fido2AuthenticationMethod",
  "id": "73e4b2c6-8a2f-4d3e-9b1a-5c7d8e9f0a1b",
  "displayName": "My security key",
  "createdDateTime": "2026-04-20T10:15:30Z",
  "aaGuid": "de1e552d-db1d-4423-a619-566b625cdc84",
  "model": "Security Key NFC by Yubico",
  "attestationCertificates": [],
  "attestationLevel": "attested",
  "passkeyType": "deviceBound"
}
```
