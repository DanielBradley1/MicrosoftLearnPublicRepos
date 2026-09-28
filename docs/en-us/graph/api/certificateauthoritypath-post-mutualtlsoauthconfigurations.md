<!-- Source: https://learn.microsoft.com/en-us/graph/api/certificateauthoritypath-post-mutualtlsoauthconfigurations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-07 -->

# Create mutualTlsOauthConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resource that contains a specified certificate authority object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MutualTlsOauthConfiguration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MutualTlsOauthConfiguration.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Cloud Device Administrator
- IoT Device Administrator

## HTTP request

```http
POST /directory/certificateAuthorities/mutualTlsOauthConfigurations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) object.

You can specify the following properties when you create a **mutualTlsOauthConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthority | [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-beta) collection | Multi-value property that represents a list of trusted certificate authorities. Optional. |
| displayName | String | Friendly name. Optional. |
| tlsClientAuthParameter | tlsClientRegistrationMetadata | Specifies which field in the certificate contains the subject ID. The possible values are: `tls_client_auth_subject_dn`, `tls_client_auth_san_dns`, `tls_client_auth_san_uri`, `tls_client_auth_san_ip`, `tls_client_auth_san_email`, `unknownFutureValue`. Required. Read-only. |

## Response

If successful, this method returns a `201 Created` response code and a [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) object in the response body. If a validation failure occurs during the certificate validation steps, the method returns a `400 Bad Request` along with the error message, `Invalid value specified for property 'certificate' of resource 'CertificateAuthorityInformation'.`.

For more information, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

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
POST https://graph.microsoft.com/beta/directory/certificateAuthorities/mutualTlsOauthConfigurations
Content-Type: application/json

{
  "displayName": "DoorCamera_Model_X_TrustedCAs",
  "tlsClientAuthParameter": "tls_client_auth_san_uri",
  "certificateAuthorities": [
    {
      "@odata.type": "microsoft.graph.certificateAuthority"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MutualTlsOauthConfiguration
{
	DisplayName = "DoorCamera_Model_X_TrustedCAs",
	TlsClientAuthParameter = TlsClientRegistrationMetadata.Tls_client_auth_san_uri,
	CertificateAuthorities = new List<CertificateAuthority>
	{
		new CertificateAuthority
		{
			OdataType = "microsoft.graph.certificateAuthority",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CertificateAuthorities.MutualTlsOauthConfigurations.PostAsync(requestBody);
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

requestBody := graphmodels.NewMutualTlsOauthConfiguration()
displayName := "DoorCamera_Model_X_TrustedCAs"
requestBody.SetDisplayName(&displayName) 
tlsClientAuthParameter := graphmodels.TLS_CLIENT_AUTH_SAN_URI_TLSCLIENTREGISTRATIONMETADATA 
requestBody.SetTlsClientAuthParameter(&tlsClientAuthParameter) 


certificateAuthority := graphmodels.NewCertificateAuthority()

certificateAuthorities := []graphmodels.CertificateAuthorityable {
	certificateAuthority,
}
requestBody.SetCertificateAuthorities(certificateAuthorities)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mutualTlsOauthConfigurations, err := graphClient.Directory().CertificateAuthorities().MutualTlsOauthConfigurations().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MutualTlsOauthConfiguration mutualTlsOauthConfiguration = new MutualTlsOauthConfiguration();
mutualTlsOauthConfiguration.setDisplayName("DoorCamera_Model_X_TrustedCAs");
mutualTlsOauthConfiguration.setTlsClientAuthParameter(TlsClientRegistrationMetadata.Tls_client_auth_san_uri);
LinkedList<CertificateAuthority> certificateAuthorities = new LinkedList<CertificateAuthority>();
CertificateAuthority certificateAuthority = new CertificateAuthority();
certificateAuthority.setOdataType("microsoft.graph.certificateAuthority");
certificateAuthorities.add(certificateAuthority);
mutualTlsOauthConfiguration.setCertificateAuthorities(certificateAuthorities);
MutualTlsOauthConfiguration result = graphClient.directory().certificateAuthorities().mutualTlsOauthConfigurations().post(mutualTlsOauthConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mutualTlsOauthConfiguration = {
  displayName: 'DoorCamera_Model_X_TrustedCAs',
  tlsClientAuthParameter: 'tls_client_auth_san_uri',
  certificateAuthorities: [
    {
      '@odata.type': 'microsoft.graph.certificateAuthority'
    }
  ]
};

await client.api('/directory/certificateAuthorities/mutualTlsOauthConfigurations')
	.version('beta')
	.post(mutualTlsOauthConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MutualTlsOauthConfiguration;
use Microsoft\Graph\Beta\Generated\Models\TlsClientRegistrationMetadata;
use Microsoft\Graph\Beta\Generated\Models\CertificateAuthority;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MutualTlsOauthConfiguration();
$requestBody->setDisplayName('DoorCamera_Model_X_TrustedCAs');
$requestBody->setTlsClientAuthParameter(new TlsClientRegistrationMetadata('tls_client_auth_san_uri'));
$certificateAuthoritiesCertificateAuthority1 = new CertificateAuthority();
$certificateAuthoritiesCertificateAuthority1->setOdataType('microsoft.graph.certificateAuthority');
$certificateAuthoritiesArray []= $certificateAuthoritiesCertificateAuthority1;
$requestBody->setCertificateAuthorities($certificateAuthoritiesArray);


$result = $graphServiceClient->directory()->certificateAuthorities()->mutualTlsOauthConfigurations()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	displayName = "DoorCamera_Model_X_TrustedCAs"
	tlsClientAuthParameter = "tls_client_auth_san_uri"
	certificateAuthorities = @(
		@{
			"@odata.type" = "microsoft.graph.certificateAuthority"
		}
	)
}

New-MgBetaDirectoryCertificateAuthorityMutualTlOauthConfiguration -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.mutual_tls_oauth_configuration import MutualTlsOauthConfiguration
from msgraph_beta.generated.models.tls_client_registration_metadata import TlsClientRegistrationMetadata
from msgraph_beta.generated.models.certificate_authority import CertificateAuthority
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MutualTlsOauthConfiguration(
	display_name = "DoorCamera_Model_X_TrustedCAs",
	tls_client_auth_parameter = TlsClientRegistrationMetadata.Tls_client_auth_san_uri,
	certificate_authorities = [
		CertificateAuthority(
			odata_type = "microsoft.graph.certificateAuthority",
		),
	],
)

result = await graph_client.directory.certificate_authorities.mutual_tls_oauth_configurations.post(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/certificateAuthorities/mutualTlsOauthConfigurations/$entity",
  "id":"eec5ba11-2fc0-4113-83a2-ed986ed13cdb",
  "displayName": "DoorCamera_Model_X_TrustedCAs",
  "tlsClientAuthParameter": "tls_client_auth_san_uri",
  "certificateAuthorities": [
    {
      "@odata.type": "microsoft.graph.certificateAuthority"
    }
  ]
}
```
