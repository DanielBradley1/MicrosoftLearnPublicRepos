<!-- Source: https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update samlOrWsFedExternalDomainFederation

Namespace: microsoft.graph

Update the properties of a [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityProvider.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityProvider.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External Identity Provider Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH directory/federationConfigurations/graph.samlOrWsFedExternalDomainFederation/{samlOrWsFedExternalDomainFederation ID}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with one or more properties that need to be updated for a [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object in Microsoft Entra tenant.

The following table shows the properties that you may update for a [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the SAML/WS-Fed based identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). |
| issuerUri | String | Issuer URI of the federation server. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| metadataExchangeUri | String | URI of the metadata exchange endpoint used for authentication from rich client applications. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| passiveSignInUri | String | URI that web-based clients are directed to when signing in to Microsoft Entra services. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| preferredAuthenticationProtocol | authenticationProtocol | Preferred authentication protocol. The possible values are: `wsFed`, `saml`. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| signingCertificate | String | Current certificate used to sign tokens passed to the Microsoft identity platform. The certificate is formatted as a Base64 encoded string of the public portion of the federated IdP's token signing certificate and must be compatible with the X509Certificate2 class.  <br>  <br>This property is used in the following scenarios:<br><br>- if a rollover is required outside of the autorollover update<br>- a new federation service is being set up<br>- if the new token signing certificate isn't present in the federation properties after the federation service certificate has been updated.<br><br>  <br>  <br>Microsoft Entra ID updates certificates via an autorollover process in which it attempts to retrieve a new certificate from the federation service metadata, 30 days before expiry of the current certificate. If a new certificate isn't available, Microsoft Entra ID monitors the metadata daily and will update the federation settings for the domain when a new certificate is available. |

## Response

If successful, this method returns a `200 OK` response code and an updated [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/v1.0/directory/federationConfigurations/graph.samlOrWsFedExternalDomainFederation/d5a56845-6845-d5a5-4568-a5d54568a5d5
Content-Type: application/json

{
  "displayName": "Contoso name change",
  "issuerUri": "http://contoso-test.com/adfs/services/trust",
  "metadataExchangeUri": null,
  "signingCertificate": "M66C6DCCAdCgAwIBAgIQQ6vYJIVKQ",
  "passiveSignInUri": "https://contoso-test.com/adfs/ls/",
  "preferredAuthenticationProtocol": "wsFed"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const samlOrWsFedExternalDomainFederation = {
  displayName: 'Contoso name change',
  issuerUri: 'http://contoso-test.com/adfs/services/trust',
  metadataExchangeUri: null,
  signingCertificate: 'M66C6DCCAdCgAwIBAgIQQ6vYJIVKQ',
  passiveSignInUri: 'https://contoso-test.com/adfs/ls/',
  preferredAuthenticationProtocol: 'wsFed'
};

await client.api('/directory/federationConfigurations/graph.samlOrWsFedExternalDomainFederation/d5a56845-6845-d5a5-4568-a5d54568a5d5')
	.update(samlOrWsFedExternalDomainFederation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
 "id": "d5a56845-6845-d5a5-4568-a5d54568a5d5",
  "displayName": "Contoso name change",
  "issuerUri": "http://contoso-test.com/adfs/services/trust",
  "metadataExchangeUri": null,
  "signingCertificate": "M66C6DCCAdCgAwIBAgIQQ6vYJIVKQ",
  "passiveSignInUri": "https://contoso-test.com/adfs/ls/",
  "preferredAuthenticationProtocol": "wsFed",
  "domains": [
      {
          "id": "contoso.com"
      }
  ]
}
```
