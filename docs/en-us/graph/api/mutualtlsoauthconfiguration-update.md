<!-- Source: https://learn.microsoft.com/en-us/graph/api/mutualtlsoauthconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-07 -->

# Update mutualTlsOauthConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the specified [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) resource.

You can only update the following two properties: **displayName**, **certificateAuthority**.

To update a subset of objects in the **certificateAuthorities** collection, first get the complete list, make your modifications, and then repost the entire contents of the **certificateAuthorities** attribute list in the request body. Excluding a subset of objects removes them from the collection.

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
PATCH /directory/certificateAuthorities/mutualTlsOauthConfigurations/{mutualTlsOauthConfigurationId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) object.

You can specify the following properties when you update a **mutualTlsOauthConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthority | [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-beta) collection | Multi-value property that represents a list of trusted certificate authorities. |
| displayName | String | Friendly name. |

## Response

If successful, this method returns a `200 OK` response code and a [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta) object in the response body. If a validation failure occurs during the certificate validation steps, the method returns a `400 Bad Request` along with the error message, `Invalid value specified for property 'certificate' of resource 'CertificateAuthorityInformation'`. For more information, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Example 1: Update the display name

The following example shows how to update the display name of a **mutualTlsOauthConfiguration** object from `DoorCamera_Model_X_TrustedCAs` to `THIS_IS_A_NEW_NAME`.

#### Request

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
PATCH https://graph.microsoft.com/beta/directory/certificateAuthorities/mutualTlsOauthConfigurations/eec5ba11-2fc0-4113-83a2-ed986ed13cdb
Content-Type: application/json

{
  "displayName": "THIS_IS_A_NEW_NAME"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MutualTlsOauthConfiguration
{
	DisplayName = "THIS_IS_A_NEW_NAME",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CertificateAuthorities.MutualTlsOauthConfigurations["{mutualTlsOauthConfiguration-id}"].PatchAsync(requestBody);
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
displayName := "THIS_IS_A_NEW_NAME"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mutualTlsOauthConfigurations, err := graphClient.Directory().CertificateAuthorities().MutualTlsOauthConfigurations().ByMutualTlsOauthConfigurationId("mutualTlsOauthConfiguration-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MutualTlsOauthConfiguration mutualTlsOauthConfiguration = new MutualTlsOauthConfiguration();
mutualTlsOauthConfiguration.setDisplayName("THIS_IS_A_NEW_NAME");
MutualTlsOauthConfiguration result = graphClient.directory().certificateAuthorities().mutualTlsOauthConfigurations().byMutualTlsOauthConfigurationId("{mutualTlsOauthConfiguration-id}").patch(mutualTlsOauthConfiguration);
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
  displayName: 'THIS_IS_A_NEW_NAME'
};

await client.api('/directory/certificateAuthorities/mutualTlsOauthConfigurations/eec5ba11-2fc0-4113-83a2-ed986ed13cdb')
	.version('beta')
	.update(mutualTlsOauthConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MutualTlsOauthConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MutualTlsOauthConfiguration();
$requestBody->setDisplayName('THIS_IS_A_NEW_NAME');

$result = $graphServiceClient->directory()->certificateAuthorities()->mutualTlsOauthConfigurations()->byMutualTlsOauthConfigurationId('mutualTlsOauthConfiguration-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	displayName = "THIS_IS_A_NEW_NAME"
}

Update-MgBetaDirectoryCertificateAuthorityMutualTlOauthConfiguration -MutualTlsOauthConfigurationId $mutualTlsOauthConfigurationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.mutual_tls_oauth_configuration import MutualTlsOauthConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MutualTlsOauthConfiguration(
	display_name = "THIS_IS_A_NEW_NAME",
)

result = await graph_client.directory.certificate_authorities.mutual_tls_oauth_configurations.by_mutual_tls_oauth_configuration_id('mutualTlsOauthConfiguration-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/certificateAuthorities/mutualTlsOauthConfigurations/$entity",
  "id":"eec5ba11-2fc0-4113-83a2-ed986ed13cdb",
  "displayName": "THIS_IS_A_NEW_NAME",
  "tlsClientAuthParameter": "tls_client_auth_subject_dn",
  "certificateAuthorities": [
    {
      "@odata.type": "microsoft.graph.certificateAuthority"
    }
  ]
}
```

### Example 2: Remove a certificate from the list of certificateAuthorities

This example assumes that the original object stored has the following value. Note that the starting resource contains two values in the certificate authority list.

```json
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/certificateAuthorities/mutualTlsOauthConfigurations/$entity",
  "id": "eec5ba11-2fc0-4113-83a2-ed986ed13cdb",
  "displayName": "DoorCamera_Model_X_TrustedCAs",
  "tlsClientAuthParameter": "tls_client_auth_subject_dn",
  "certificateAuthorities": [
    {
      "isRootAuthority": true,
      "certificateRevocationListUrl": "http://LakeshoreRetail.com/root.crl",
      "deltaCertificateRevocationListUrl": null,
      "certificate": "joGrWL+Yqkik/CABWG0d1w....",
      "issuer": "Lakeshore Retail",
      "issuerSubjectkeyIdentifier": "SKI"
    },
    {
      "isRootAuthority": true,
      "certificateRevocationListUrl": "http://LakeshoreRetail.com/root.crl",
      "deltaCertificateRevocationListUrl": null,
      "certificate": "koGrWL+Yqkik/CABWG0d1w....",
      "issuer": "Lakeshore Retail",
      "issuerSubjectkeyIdentifier": "SKI"
    }
  ]
}
```

#### Request

The following example shows a request that updates the certificate authority list to contain only a single certificate, which removes the other.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/beta/directory/certificateAuthorities/mutualTlsOauthConfigurations/00001111-aaaa-2222-bbbb-3333cccc4444
Content-Type: application/json

{
  "certificateAuthorities": [
    {
      "isRootAuthority": true,
      "certificateRevocationListUrl": "http://LakeshoreRetail.com/root.crl",
      "deltaCertificateRevocationListUrl": null,
      "certificate": "Binary",
      "issuer": "Lakeshore Retail",
      "issuerSubjectkeyIdentifier": "SKI"
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
	CertificateAuthorities = new List<CertificateAuthority>
	{
		new CertificateAuthority
		{
			IsRootAuthority = true,
			CertificateRevocationListUrl = "http://LakeshoreRetail.com/root.crl",
			DeltaCertificateRevocationListUrl = null,
			Certificate = Convert.FromBase64String("Binary"),
			Issuer = "Lakeshore Retail",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"issuerSubjectkeyIdentifier" , "SKI"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CertificateAuthorities.MutualTlsOauthConfigurations["{mutualTlsOauthConfiguration-id}"].PatchAsync(requestBody);
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


certificateAuthority := graphmodels.NewCertificateAuthority()
isRootAuthority := true
certificateAuthority.SetIsRootAuthority(&isRootAuthority) 
certificateRevocationListUrl := "http://LakeshoreRetail.com/root.crl"
certificateAuthority.SetCertificateRevocationListUrl(&certificateRevocationListUrl) 
deltaCertificateRevocationListUrl := null
certificateAuthority.SetDeltaCertificateRevocationListUrl(&deltaCertificateRevocationListUrl) 
certificate := []byte("binary")
certificateAuthority.SetCertificate(&certificate) 
issuer := "Lakeshore Retail"
certificateAuthority.SetIssuer(&issuer) 
additionalData := map[string]interface{}{
	"issuerSubjectkeyIdentifier" : "SKI", 
}
certificateAuthority.SetAdditionalData(additionalData)

certificateAuthorities := []graphmodels.CertificateAuthorityable {
	certificateAuthority,
}
requestBody.SetCertificateAuthorities(certificateAuthorities)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mutualTlsOauthConfigurations, err := graphClient.Directory().CertificateAuthorities().MutualTlsOauthConfigurations().ByMutualTlsOauthConfigurationId("mutualTlsOauthConfiguration-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MutualTlsOauthConfiguration mutualTlsOauthConfiguration = new MutualTlsOauthConfiguration();
LinkedList<CertificateAuthority> certificateAuthorities = new LinkedList<CertificateAuthority>();
CertificateAuthority certificateAuthority = new CertificateAuthority();
certificateAuthority.setIsRootAuthority(true);
certificateAuthority.setCertificateRevocationListUrl("http://LakeshoreRetail.com/root.crl");
certificateAuthority.setDeltaCertificateRevocationListUrl(null);
byte[] certificate = Base64.getDecoder().decode("Binary");
certificateAuthority.setCertificate(certificate);
certificateAuthority.setIssuer("Lakeshore Retail");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("issuerSubjectkeyIdentifier", "SKI");
certificateAuthority.setAdditionalData(additionalData);
certificateAuthorities.add(certificateAuthority);
mutualTlsOauthConfiguration.setCertificateAuthorities(certificateAuthorities);
MutualTlsOauthConfiguration result = graphClient.directory().certificateAuthorities().mutualTlsOauthConfigurations().byMutualTlsOauthConfigurationId("{mutualTlsOauthConfiguration-id}").patch(mutualTlsOauthConfiguration);
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
  certificateAuthorities: [
    {
      isRootAuthority: true,
      certificateRevocationListUrl: 'http://LakeshoreRetail.com/root.crl',
      deltaCertificateRevocationListUrl: null,
      certificate: 'Binary',
      issuer: 'Lakeshore Retail',
      issuerSubjectkeyIdentifier: 'SKI'
    }
  ]
};

await client.api('/directory/certificateAuthorities/mutualTlsOauthConfigurations/00001111-aaaa-2222-bbbb-3333cccc4444')
	.version('beta')
	.update(mutualTlsOauthConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MutualTlsOauthConfiguration;
use Microsoft\Graph\Beta\Generated\Models\CertificateAuthority;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MutualTlsOauthConfiguration();
$certificateAuthoritiesCertificateAuthority1 = new CertificateAuthority();
$certificateAuthoritiesCertificateAuthority1->setIsRootAuthority(true);
$certificateAuthoritiesCertificateAuthority1->setCertificateRevocationListUrl('http://LakeshoreRetail.com/root.crl');
$certificateAuthoritiesCertificateAuthority1->setDeltaCertificateRevocationListUrl(null);
$certificateAuthoritiesCertificateAuthority1->setCertificate(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('Binary')));
$certificateAuthoritiesCertificateAuthority1->setIssuer('Lakeshore Retail');
$additionalData = [
	'issuerSubjectkeyIdentifier' => 'SKI',
];
$certificateAuthoritiesCertificateAuthority1->setAdditionalData($additionalData);
$certificateAuthoritiesArray []= $certificateAuthoritiesCertificateAuthority1;
$requestBody->setCertificateAuthorities($certificateAuthoritiesArray);


$result = $graphServiceClient->directory()->certificateAuthorities()->mutualTlsOauthConfigurations()->byMutualTlsOauthConfigurationId('mutualTlsOauthConfiguration-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	certificateAuthorities = @(
		@{
			isRootAuthority = $true
			certificateRevocationListUrl = "http://LakeshoreRetail.com/root.crl"
			deltaCertificateRevocationListUrl = $null
			certificate = [System.Text.Encoding]::ASCII.GetBytes("Binary")
			issuer = "Lakeshore Retail"
			issuerSubjectkeyIdentifier = "SKI"
		}
	)
}

Update-MgBetaDirectoryCertificateAuthorityMutualTlOauthConfiguration -MutualTlsOauthConfigurationId $mutualTlsOauthConfigurationId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.mutual_tls_oauth_configuration import MutualTlsOauthConfiguration
from msgraph_beta.generated.models.certificate_authority import CertificateAuthority
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MutualTlsOauthConfiguration(
	certificate_authorities = [
		CertificateAuthority(
			is_root_authority = True,
			certificate_revocation_list_url = "http://LakeshoreRetail.com/root.crl",
			delta_certificate_revocation_list_url = None,
			certificate = base64.urlsafe_b64decode("Binary"),
			issuer = "Lakeshore Retail",
			additional_data = {
					"issuer_subjectkey_identifier" : "SKI",
			}
		),
	],
)

result = await graph_client.directory.certificate_authorities.mutual_tls_oauth_configurations.by_mutual_tls_oauth_configuration_id('mutualTlsOauthConfiguration-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Location: "https://graph.microsoft.com/beta/directory/certificateAuthorities/mutualTlsOauthConfigurations/00001111-aaaa-2222-bbbb-3333cccc4444"

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/certificateAuthorities/mutualTlsOauthConfigurations/$entity",
  "id":"eec5ba11-2fc0-4113-83a2-ed986ed13cdb",
  "displayName": "DoorCamera_Model_X_TrustedCAs",
  "tlsClientAuthParameter": "tls_client_auth_subject_dn",
  "certificateAuthorities": [
    {
      "isRootAuthority": true,
      "certificateRevocationListUrl": "http://LakeshoreRetail.com/root.crl",
      "deltaCertificateRevocationListUrl": null,
      "certificate": "Binary",
      "issuer": "Lakeshore Retail",
      "issuerSubjectkeyIdentifier": "SKI"
    }
  ]
}
```
