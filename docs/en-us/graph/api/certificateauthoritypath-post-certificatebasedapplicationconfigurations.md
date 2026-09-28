<!-- Source: https://learn.microsoft.com/en-us/graph/api/certificateauthoritypath-post-certificatebasedapplicationconfigurations?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create certificateBasedApplicationConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object.

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
POST /directory/certificateAuthorities/certificateBasedApplicationConfigurations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object.

> **Note:** A maximum of 100 certificate-based application configuration objects are allowed per tenant. This includes any deleted or active objects.

You can specify the following properties when you create a **certificateBasedApplicationConfiguration**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description for the configuration. Optional. |
| displayName | String | The friendly name for the configuration. Optional. |
| trustedCertificateAuthorities | [certificateAuthorityAsEntity](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthorityasentity?view=graph-rest-beta) | Multi-value property that represents a list of trusted certificate authorities. At least one trusted certificate authority must be provided when you create a certificate-based application configuration. |

## Response

If successful, this method returns a `200 OK` response code and a [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/directory/certificateAuthorities/certificateBasedApplicationConfigurations
Content-Type: application/json

{
  "displayName": "Tenant Trusted Certificate Chain of Trust for Application Configuration",
  "description": "The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.",
  "trustedCertificateAuthorities ": [
    {
      "isRootAuthority": true,
      "certificate": "MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new CertificateBasedApplicationConfiguration
{
	DisplayName = "Tenant Trusted Certificate Chain of Trust for Application Configuration",
	Description = "The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"trustedCertificateAuthorities " , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"isRootAuthority", new UntypedBoolean(true)
					},
					{
						"certificate", new UntypedString("MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.CertificateAuthorities.CertificateBasedApplicationConfigurations.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CertificateBasedApplicationConfiguration certificateBasedApplicationConfiguration = new CertificateBasedApplicationConfiguration();
certificateBasedApplicationConfiguration.setDisplayName("Tenant Trusted Certificate Chain of Trust for Application Configuration");
certificateBasedApplicationConfiguration.setDescription("The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> trustedCertificateAuthorities = new LinkedList<Object>();
 property = new ();
property.setIsRootAuthority(true);
property.setCertificate("MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ");
trustedCertificateAuthorities.add(property);
additionalData.put("trustedCertificateAuthorities ", trustedCertificateAuthorities);
certificateBasedApplicationConfiguration.setAdditionalData(additionalData);
CertificateBasedApplicationConfiguration result = graphClient.directory().certificateAuthorities().certificateBasedApplicationConfigurations().post(certificateBasedApplicationConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const certificateBasedApplicationConfiguration = {
  displayName: 'Tenant Trusted Certificate Chain of Trust for Application Configuration',
  description: 'The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.',
  'trustedCertificateAuthorities ': [
    {
      isRootAuthority: true,
      certificate: 'MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ'
    }
  ]
};

await client.api('/directory/certificateAuthorities/certificateBasedApplicationConfigurations')
	.version('beta')
	.post(certificateBasedApplicationConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CertificateBasedApplicationConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CertificateBasedApplicationConfiguration();
$requestBody->setDisplayName('Tenant Trusted Certificate Chain of Trust for Application Configuration');
$requestBody->setDescription('The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.');
$additionalData = [
	'trustedCertificateAuthorities ' => [
			[
				'isRootAuthority' => true,
				'certificate' => 'MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->directory()->certificateAuthorities()->certificateBasedApplicationConfigurations()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	displayName = "Tenant Trusted Certificate Chain of Trust for Application Configuration"
	description = "The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer."
	"trustedCertificateAuthorities " = @(
		@{
			isRootAuthority = $true
			certificate = "MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ"
		}
	)
}

New-MgBetaDirectoryCertificateAuthorityCertificateBasedApplicationConfiguration -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.certificate_based_application_configuration import CertificateBasedApplicationConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CertificateBasedApplicationConfiguration(
	display_name = "Tenant Trusted Certificate Chain of Trust for Application Configuration",
	description = "The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.",
	additional_data = {
			"trusted_certificate_authorities " : [
				{
						"is_root_authority" : True,
						"certificate" : "MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ",
				},
			],
	}
)

result = await graph_client.directory.certificate_authorities.certificate_based_application_configurations.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.certificateBasedApplicationConfiguration",
    "id": "d5b0af1c-9376-6b66-16b6-e402965862c1",
    "deletedDateTime": "String (timestamp)",
    "displayName": "Tenant Trusted Certificate Chain of Trust for Application Configuration",
    "description": "The Trusted Certificate Chain of Trust containing a certificate chain used by the Tenant app policy, to only allow application certificates from this issuer.",
    "trustedCertificateAuthorities ": [
      {
        "isRootAuthority": true,
        "certificate": "MIIHMDCCBRigAwIBAgITWgAAmdzMYKZPslw+twABAACZ"
      }
    ]
  }
}
```
