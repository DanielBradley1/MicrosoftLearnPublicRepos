<!-- Source: https://learn.microsoft.com/en-us/graph/api/securescorecontrolprofile-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# Update secureScoreControlProfile

Namespace: microsoft.graph

Update an editable **secureScoreControlProfile** object within any integrated solution to change various properties, such as **tenantNote**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityEvents.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityEvents.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /security/secureScoreControlProfiles/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |
| Prefer | return=representation. |

## Request body

In the request body, supply a JSON representation of the values for relevant fields that should be updated. The body **must** contain the `vendorInformation` property with valid `provider` and `vendor` fields. The following table lists the fields that can be updated for a **secureScoreControlProfile**. The values for existing properties that are not included in the request body will not change. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| vendorInformation | [securityVendorInformation](https://learn.microsoft.com/en-us/graph/api/resources/securityvendorinformation?view=graph-rest-1.0) | Complex type containing details about the security product/service vendor, provider, and subprovider \(for example, vendor=Microsoft; provider=SecureScore;\). **Provider and vendor fields are required.** |

## Response

If successful, this method returns a `204 No Content` response code.

If the optional `Prefer: return=representation` request header is used, the method returns a `200 OK` response code and the updated [secureScoreControlProfiles](https://learn.microsoft.com/en-us/graph/api/resources/securescorecontrolprofile?view=graph-rest-1.0) object in the response body.

## Example

### Example 1: Request without Prefer header

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
PATCH https://graph.microsoft.com/v1.0/security/secureScoreControlProfiles/NonOwnerAccess
Content-type: application/json

{
  "vendorInformation": {

    "provider": "SecureScore",
    "providerVersion": null,
    "subProvider": null,
    "vendor": "Microsoft"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SecureScoreControlProfile
{
	VendorInformation = new SecurityVendorInformation
	{
		Provider = "SecureScore",
		ProviderVersion = null,
		SubProvider = null,
		Vendor = "Microsoft",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.SecureScoreControlProfiles["{secureScoreControlProfile-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewSecureScoreControlProfile()
vendorInformation := graphmodels.NewSecurityVendorInformation()
provider := "SecureScore"
vendorInformation.SetProvider(&provider) 
providerVersion := null
vendorInformation.SetProviderVersion(&providerVersion) 
subProvider := null
vendorInformation.SetSubProvider(&subProvider) 
vendor := "Microsoft"
vendorInformation.SetVendor(&vendor) 
requestBody.SetVendorInformation(vendorInformation)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
secureScoreControlProfiles, err := graphClient.Security().SecureScoreControlProfiles().BySecureScoreControlProfileId("secureScoreControlProfile-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SecureScoreControlProfile secureScoreControlProfile = new SecureScoreControlProfile();
SecurityVendorInformation vendorInformation = new SecurityVendorInformation();
vendorInformation.setProvider("SecureScore");
vendorInformation.setProviderVersion(null);
vendorInformation.setSubProvider(null);
vendorInformation.setVendor("Microsoft");
secureScoreControlProfile.setVendorInformation(vendorInformation);
SecureScoreControlProfile result = graphClient.security().secureScoreControlProfiles().bySecureScoreControlProfileId("{secureScoreControlProfile-id}").patch(secureScoreControlProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const secureScoreControlProfile = {
  vendorInformation: {

    provider: 'SecureScore',
    providerVersion: null,
    subProvider: null,
    vendor: 'Microsoft'
  }
};

await client.api('/security/secureScoreControlProfiles/NonOwnerAccess')
	.update(secureScoreControlProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SecureScoreControlProfile;
use Microsoft\Graph\Generated\Models\SecurityVendorInformation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SecureScoreControlProfile();
$vendorInformation = new SecurityVendorInformation();
$vendorInformation->setProvider('SecureScore');
$vendorInformation->setProviderVersion(null);
$vendorInformation->setSubProvider(null);
$vendorInformation->setVendor('Microsoft');
$requestBody->setVendorInformation($vendorInformation);

$result = $graphServiceClient->security()->secureScoreControlProfiles()->bySecureScoreControlProfileId('secureScoreControlProfile-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	vendorInformation = @{
		provider = "SecureScore"
		providerVersion = $null
		subProvider = $null
		vendor = "Microsoft"
	}
}

Update-MgSecuritySecureScoreControlProfile -SecureScoreControlProfileId $secureScoreControlProfileId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.secure_score_control_profile import SecureScoreControlProfile
from msgraph.generated.models.security_vendor_information import SecurityVendorInformation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SecureScoreControlProfile(
	vendor_information = SecurityVendorInformation(
		provider = "SecureScore",
		provider_version = None,
		sub_provider = None,
		vendor = "Microsoft",
	),
)

result = await graph_client.security.secure_score_control_profiles.by_secure_score_control_profile_id('secureScoreControlProfile-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following is an example of a successful response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Request with Prefer header

#### Request

The following example shows a request that includes the `Prefer` request header.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/security/secureScoreControlProfiles/NonOwnerAccess
Content-type: application/json
Prefer: return=representation

{
  "vendorInformation": {
    "provider": "SecureScore",
    "providerVersion": null,
    "subProvider": null,
    "vendor": "Microsoft"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SecureScoreControlProfile
{
	VendorInformation = new SecurityVendorInformation
	{
		Provider = "SecureScore",
		ProviderVersion = null,
		SubProvider = null,
		Vendor = "Microsoft",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.SecureScoreControlProfiles["{secureScoreControlProfile-id}"].PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "return=representation");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "return=representation")

configuration := &graphsecurity.SecureScoreControlProfilesItemRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewSecureScoreControlProfile()
vendorInformation := graphmodels.NewSecurityVendorInformation()
provider := "SecureScore"
vendorInformation.SetProvider(&provider) 
providerVersion := null
vendorInformation.SetProviderVersion(&providerVersion) 
subProvider := null
vendorInformation.SetSubProvider(&subProvider) 
vendor := "Microsoft"
vendorInformation.SetVendor(&vendor) 
requestBody.SetVendorInformation(vendorInformation)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
secureScoreControlProfiles, err := graphClient.Security().SecureScoreControlProfiles().BySecureScoreControlProfileId("secureScoreControlProfile-id").Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SecureScoreControlProfile secureScoreControlProfile = new SecureScoreControlProfile();
SecurityVendorInformation vendorInformation = new SecurityVendorInformation();
vendorInformation.setProvider("SecureScore");
vendorInformation.setProviderVersion(null);
vendorInformation.setSubProvider(null);
vendorInformation.setVendor("Microsoft");
secureScoreControlProfile.setVendorInformation(vendorInformation);
SecureScoreControlProfile result = graphClient.security().secureScoreControlProfiles().bySecureScoreControlProfileId("{secureScoreControlProfile-id}").patch(secureScoreControlProfile, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "return=representation");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const secureScoreControlProfile = {
  vendorInformation: {
    provider: 'SecureScore',
    providerVersion: null,
    subProvider: null,
    vendor: 'Microsoft'
  }
};

await client.api('/security/secureScoreControlProfiles/NonOwnerAccess')
	.update(secureScoreControlProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\SecureScoreControlProfiles\Item\SecureScoreControlProfileItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\SecureScoreControlProfile;
use Microsoft\Graph\Generated\Models\SecurityVendorInformation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SecureScoreControlProfile();
$vendorInformation = new SecurityVendorInformation();
$vendorInformation->setProvider('SecureScore');
$vendorInformation->setProviderVersion(null);
$vendorInformation->setSubProvider(null);
$vendorInformation->setVendor('Microsoft');
$requestBody->setVendorInformation($vendorInformation);
$requestConfiguration = new SecureScoreControlProfileItemRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'return=representation',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->security()->secureScoreControlProfiles()->bySecureScoreControlProfileId('secureScoreControlProfile-id')->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	vendorInformation = @{
		provider = "SecureScore"
		providerVersion = $null
		subProvider = $null
		vendor = "Microsoft"
	}
}

Update-MgSecuritySecureScoreControlProfile -SecureScoreControlProfileId $secureScoreControlProfileId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.secure_score_control_profiles.item.secure_score_control_profile_item_request_builder import SecureScoreControlProfileItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.secure_score_control_profile import SecureScoreControlProfile
from msgraph.generated.models.security_vendor_information import SecurityVendorInformation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SecureScoreControlProfile(
	vendor_information = SecurityVendorInformation(
		provider = "SecureScore",
		provider_version = None,
		sub_provider = None,
		vendor = "Microsoft",
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "return=representation")


result = await graph_client.security.secure_score_control_profiles.by_secure_score_control_profile_id('secureScoreControlProfile-id').patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following is an example of the response when the optional `Prefer: return=representation` request header is used.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "NonOwnerAccess",
  "azureTenantId": "00000001-0001-0001-0001-000000000001c",
  "actionType": "Review",
  "actionUrl": "https://outlook.office365.com/NonOwnerAccessReport.aspx",
  "controlCategory": "Data",
  "title": "Review mailbox access by non-owners bi-weekly", 
  "deprecated": false,
  "implementationCost": "Low",
  "lastModifiedDateTime": null,
  "maxScore": 5.0,
  "rank": 25,
  "remediation": "Once you have opened the search tool, specify a date range and select access by <b>All non-owners</b> or <b>External users</b>",
  "remediationImpact": "This change will have no effect on your users",
  "service": "EXO",
  "threats": [
    "Account Breach",
    "Data Exfiltration",
    "Malicious Insider"
  ],
  "tier": "Core",
  "userImpact": "Low",
  "complianceInformation": null,
  "controlStateUpdates": [
    {
      "updatedBy": "user1@contoso.com",
      "updatedDateTime": "2019-03-19T22:37:14.628799Z"
    }
  ],
  "vendorInformation": {
    "provider": "SecureScore",
    "providerVersion": null,
    "subProvider": null,
    "vendor": "Microsoft"
  }
}
```
