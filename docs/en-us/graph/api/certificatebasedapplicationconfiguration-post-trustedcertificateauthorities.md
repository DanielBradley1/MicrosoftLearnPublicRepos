<!-- Source: https://learn.microsoft.com/en-us/graph/api/certificatebasedapplicationconfiguration-post-trustedcertificateauthorities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create trustedCertificateAuthority

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new trusted certificate authority in a [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AppCertTrustConfiguration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AppCertTrustConfiguration.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /directory/certificateAuthorities/certificateBasedApplicationConfigurations/{certificateBasedApplicationConfigurationId}/trustedCertificateAuthorities
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) object.

You can specify the following properties when you create a **certificateAuthorityAsEntity**.

> **Note:** A maximum of 10 trusted authorities are allowed per **trustedCertificateAuthorities** collection.

| Property | Type | Description |
| :--- | :--- | :--- |
| certificate | Binary | The trusted certificate. Required. |
| isRootAuthority | Boolean | Indicates if the certificate is a root authority. Required. Only one object in a **trustedCertificateAuthorities** collection can be the root authority. |
| issuer | String | The issuer of the trusted certificate. Required. |
| issuerSubjectKeyIdentifier | String | The subject key identifier of the trusted certificate. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/directory/certificateAuthorities/certificateBasedApplicationConfigurations/0a6a9b97-b84c-406a-a703-14d699d1fbb1/trustedCertificateAuthorities
Content-Type: application/json

{
  "isRootAuthority": true,
  "certificate": "MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB....",
  "issuer": "ExampleIssuer",
  "issuerSubjectKeyIdentifier": " BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CertificateAuthorityAsEntity
{
	IsRootAuthority = true,
	Certificate = Convert.FromBase64String("MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB...."),
	Issuer = "ExampleIssuer",
	IssuerSubjectKeyIdentifier = " BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CertificateAuthorities.CertificateBasedApplicationConfigurations["{certificateBasedApplicationConfiguration-id}"].TrustedCertificateAuthorities.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCertificateAuthorityAsEntity()
isRootAuthority := true
requestBody.SetIsRootAuthority(&isRootAuthority) 
certificate := []byte("mIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB....")
requestBody.SetCertificate(&certificate) 
issuer := "ExampleIssuer"
requestBody.SetIssuer(&issuer) 
issuerSubjectKeyIdentifier := " BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9"
requestBody.SetIssuerSubjectKeyIdentifier(&issuerSubjectKeyIdentifier) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
trustedCertificateAuthorities, err := graphClient.Directory().CertificateAuthorities().CertificateBasedApplicationConfigurations().ByCertificateBasedApplicationConfigurationId("certificateBasedApplicationConfiguration-id").TrustedCertificateAuthorities().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CertificateAuthorityAsEntity certificateAuthorityAsEntity = new CertificateAuthorityAsEntity();
certificateAuthorityAsEntity.setIsRootAuthority(true);
byte[] certificate = Base64.getDecoder().decode("MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB....");
certificateAuthorityAsEntity.setCertificate(certificate);
certificateAuthorityAsEntity.setIssuer("ExampleIssuer");
certificateAuthorityAsEntity.setIssuerSubjectKeyIdentifier(" BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9");
CertificateAuthorityAsEntity result = graphClient.directory().certificateAuthorities().certificateBasedApplicationConfigurations().byCertificateBasedApplicationConfigurationId("{certificateBasedApplicationConfiguration-id}").trustedCertificateAuthorities().post(certificateAuthorityAsEntity);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const certificateAuthorityAsEntity = {
  isRootAuthority: true,
  certificate: 'MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB....',
  issuer: 'ExampleIssuer',
  issuerSubjectKeyIdentifier: ' BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9'
};

await client.api('/directory/certificateAuthorities/certificateBasedApplicationConfigurations/0a6a9b97-b84c-406a-a703-14d699d1fbb1/trustedCertificateAuthorities')
	.version('beta')
	.post(certificateAuthorityAsEntity);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CertificateAuthorityAsEntity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CertificateAuthorityAsEntity();
$requestBody->setIsRootAuthority(true);
$requestBody->setCertificate(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB....')));
$requestBody->setIssuer('ExampleIssuer');
$requestBody->setIssuerSubjectKeyIdentifier(' BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9');

$result = $graphServiceClient->directory()->certificateAuthorities()->certificateBasedApplicationConfigurations()->byCertificateBasedApplicationConfigurationId('certificateBasedApplicationConfiguration-id')->trustedCertificateAuthorities()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	isRootAuthority = $true
	certificate = [System.Text.Encoding]::ASCII.GetBytes("MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB....")
	issuer = "ExampleIssuer"
	issuerSubjectKeyIdentifier = " BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9"
}

New-MgBetaDirectoryCertificateAuthorityCertificateBasedApplicationConfigurationTrustedCertificateAuthority -CertificateBasedApplicationConfigurationId $certificateBasedApplicationConfigurationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.certificate_authority_as_entity import CertificateAuthorityAsEntity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CertificateAuthorityAsEntity(
	is_root_authority = True,
	certificate = base64.urlsafe_b64decode("MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB...."),
	issuer = "ExampleIssuer",
	issuer_subject_key_identifier = " BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9",
)

result = await graph_client.directory.certificate_authorities.certificate_based_application_configurations.by_certificate_based_application_configuration_id('certificateBasedApplicationConfiguration-id').trusted_certificate_authorities.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.certificateAuthorityAsEntity",
  "certificate": "MIIGrDCCBJSgAwIBAgITWgACAdWQXvWynRA6/AABAAIB",
  "id": "b505a013-aebd-2dea-e9ec-a506fbde61d3",
  "issuer": "ExampleIssuer",
  "issuerSubjectKeyIdentifier": "BA:AF:4A:02:4D:AA:A6:F1:3C:25:8E:AD:FA:38:98:CE:D9:23:32:D9",
  "isRootAuthority": true
}
```
