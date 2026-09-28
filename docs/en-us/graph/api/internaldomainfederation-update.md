<!-- Source: https://learn.microsoft.com/en-us/graph/api/internaldomainfederation-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-30 -->

# Update internalDomainFederation

Namespace: microsoft.graph

Update the properties of an [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Domain-InternalFederation.ReadWrite.All | Domain.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Domain-InternalFederation.ReadWrite.All | Domain.ReadWrite.All |

Important

To update the **authenticationType** property, the calling app must be assigned the *Domain-InternalFederation.ReadWrite.All* permission.

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Domain Name Administrator
- External Identity Provider Administrator
- Hybrid Identity Administrator
- Security Administrator

## HTTP request

```http
PATCH /domains/{domainsId}/federationConfiguration/{internalDomainFederationId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| activeSignInUri | String | URL of the endpoint used by active clients when authenticating with federated domains set up for single sign-on in Microsoft Entra ID. |
| displayName | String | The display name of the federated identity Provider \(IdP\). |
| federatedIdpMfaBehavior | federatedIdpMfaBehavior | Determines whether Microsoft Entra ID accepts the MFA performed by the federated IdP when a federated user accesses an application that is governed by a conditional access policy that requires MFA. The possible values are: `acceptIfMfaDoneByFederatedIdp`, `enforceMfaByFederatedIdp`, `rejectMfaByFederatedIdp`, `unknownFutureValue`. For more information, see [federatedIdpMfaBehavior values](#federatedidpmfabehavior-values). |
| isSignedAuthenticationRequestRequired | Boolean | If `true`, when SAML authentication requests are sent to the federated SAML IdP, Microsoft Entra ID signs those requests using the OrgID signing key. If `false` \(default\), the SAML authentication requests sent to the federated IdP aren't signed. |
| issuerUri | String | Issuer URI of the federation server. |
| metadataExchangeUri | String | URI of the metadata exchange endpoint used for authentication from rich client applications. |
| nextSigningCertificate | String | Fallback token signing certificate that is used to sign tokens when the primary signing certificate expires. Formatted as Base 64 encoded strings of the public portion of the federated IdP's token signing certificate. Needs to be compatible with the X509Certificate2 class. Much like the **signingCertificate**, the **nextSigningCertificate** property is used if a rollover is required outside of the autorollover update, a new federation service is being set up, or if the new token signing certificate isn't present in the federation properties after the federation service certificate has been updated. |
| passiveSignInUri | String | URI that web-based clients are directed to when signing into Microsoft Entra services. |
| preferredAuthenticationProtocol | authenticationProtocol | Preferred authentication protocol. This parameter must be configured explicitly for the federation passive authentication flow to work. The possible values are: `wsFed`, `saml`, `unknownFutureValue`. |
| promptLoginBehavior | promptLoginBehavior | Sets the preferred behavior for the sign-in prompt. The possible values are: `translateToFreshPasswordAuthentication`, `nativeSupport`, `disabled`, `unknownFutureValue`. |
| signingCertificate | String | Current certificate used to sign tokens passed to the Microsoft identity platform. The certificate is formatted as a Base 64 encoded string of the public portion of the federated IdP's token signing certificate and must be compatible with the X509Certificate2 class.  <br>This property is used in the following scenarios:<br><br><li> If a rollover is required outside of the autorollover update </li><br><br><li> A new federation service is being set up </li><br><br><li> If the new token signing certificate isn&#39;t present in the federation properties after the federation service certificate has been updated.<br>Microsoft Entra ID updates certificates via an autorollover process in which it attempts to retrieve a new certificate from the federation service metadata, 30 days before expiry of the current certificate. If a new certificate isn&#39;t available, Microsoft Entra ID monitors the metadata daily and updates the federation settings for the domain when a new certificate is available. Inherited from <a href="https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0" data-linktype="relative-path">samlOrWsFedProvider</a>.</li> |
| signingCertificateUpdateStatus | [signingCertificateUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/signingcertificateupdatestatus?view=graph-rest-1.0) | Provides status and timestamp of the last update of the signing certificate. |
| signOutUri | String | URI that clients are redirected to when they sign out of Microsoft Entra services. |

### federatedIdpMfaBehavior values

| Member | Description |
| :--- | :--- |
| acceptIfMfaDoneByFederatedIdp | Microsoft Entra ID accepts MFA that's performed by the federated identity provider. If the federated identity provider didn't perform MFA, Microsoft Entra ID performs the MFA. |
| enforceMfaByFederatedIdp | Microsoft Entra ID accepts MFA that's performed by federated identity provider. If the federated identity provider didn't perform MFA, it redirects the request to federated identity provider to perform MFA. |
| rejectMfaByFederatedIdp | Microsoft Entra ID always performs MFA and rejects MFA that's performed by the federated identity provider. |

Note

**federatedIdpMfaBehavior** is an evolved version of the **SupportsMfa** property of the `Set-MsolDomainFederationSettings` cmdlet of the retired MSOnline PowerShell module.

- Switching between **federatedIdpMfaBehavior** and **SupportsMfa** is not supported.
- When **federatedIdpMfaBehavior** property is set, Microsoft Entra ID ignores the **SupportsMfa** setting.
- If the **federatedIdpMfaBehavior** property is never set, Microsoft Entra ID will continue to honor the **SupportsMfa** setting.
- If neither **federatedIdpMfaBehavior** nor **SupportsMfa** is set, Microsoft Entra ID will default to `acceptIfMfaDoneByFederatedIdp` behavior.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/domains/contoso.com/federationConfiguration/6601d14b-d113-8f64-fda2-9b5ddda18ecc
Content-Type: application/json

{
  "displayName": "Contoso name change",  
  "federatedIdpMfaBehavior": "acceptIfMfaDoneByFederatedIdp"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new InternalDomainFederation
{
	DisplayName = "Contoso name change",
	FederatedIdpMfaBehavior = FederatedIdpMfaBehavior.AcceptIfMfaDoneByFederatedIdp,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Domains["{domain-id}"].FederationConfiguration["{internalDomainFederation-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewInternalDomainFederation()
displayName := "Contoso name change"
requestBody.SetDisplayName(&displayName) 
federatedIdpMfaBehavior := graphmodels.ACCEPTIFMFADONEBYFEDERATEDIDP_FEDERATEDIDPMFABEHAVIOR 
requestBody.SetFederatedIdpMfaBehavior(&federatedIdpMfaBehavior) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
federationConfiguration, err := graphClient.Domains().ByDomainId("domain-id").FederationConfiguration().ByInternalDomainFederationId("internalDomainFederation-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

InternalDomainFederation internalDomainFederation = new InternalDomainFederation();
internalDomainFederation.setDisplayName("Contoso name change");
internalDomainFederation.setFederatedIdpMfaBehavior(FederatedIdpMfaBehavior.AcceptIfMfaDoneByFederatedIdp);
InternalDomainFederation result = graphClient.domains().byDomainId("{domain-id}").federationConfiguration().byInternalDomainFederationId("{internalDomainFederation-id}").patch(internalDomainFederation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const internalDomainFederation = {
  displayName: 'Contoso name change',  
  federatedIdpMfaBehavior: 'acceptIfMfaDoneByFederatedIdp'
};

await client.api('/domains/contoso.com/federationConfiguration/6601d14b-d113-8f64-fda2-9b5ddda18ecc')
	.update(internalDomainFederation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\InternalDomainFederation;
use Microsoft\Graph\Generated\Models\FederatedIdpMfaBehavior;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InternalDomainFederation();
$requestBody->setDisplayName('Contoso name change');
$requestBody->setFederatedIdpMfaBehavior(new FederatedIdpMfaBehavior('acceptIfMfaDoneByFederatedIdp'));

$result = $graphServiceClient->domains()->byDomainId('domain-id')->federationConfiguration()->byInternalDomainFederationId('internalDomainFederation-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	displayName = "Contoso name change"
	federatedIdpMfaBehavior = "acceptIfMfaDoneByFederatedIdp"
}

Update-MgDomainFederationConfiguration -DomainId $domainId -InternalDomainFederationId $internalDomainFederationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.internal_domain_federation import InternalDomainFederation
from msgraph.generated.models.federated_idp_mfa_behavior import FederatedIdpMfaBehavior
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InternalDomainFederation(
	display_name = "Contoso name change",
	federated_idp_mfa_behavior = FederatedIdpMfaBehavior.AcceptIfMfaDoneByFederatedIdp,
)

result = await graph_client.domains.by_domain_id('domain-id').federation_configuration.by_internal_domain_federation_id('internalDomainFederation-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
