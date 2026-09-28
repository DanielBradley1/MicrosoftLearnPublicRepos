<!-- Source: https://learn.microsoft.com/en-us/graph/api/verifiedidprofile-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# Update verifiedIdProfile

Namespace: microsoft.graph

Update the properties of a [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VerifiedId-Profile.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Authentication Policy Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /identity/verifiedId/profiles/{verifiedIdProfileId}
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
| name | String | Display name for the verified Id profile. Required. |
| description | String | Description for the verified Id profile. Required. |
| lastModifiedDateTime | DateTimeOffset | DateTime the profile was last modified. Optional. |
| state | verifiedIdProfileState | Enablement state for the profile. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Required. |
| verifierDid | String | Decentralized Identifier \(DID\) string that represents the verifier in the verifiable credential exchange. Required. |
| priority | Int32 | Defines profile processing priority if multiple profiles are configured. Optional. |
| verifiedIdProfileConfiguration | [verifiedIdProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofileconfiguration?view=graph-rest-1.0) | Set of properties expressing the accepted issuer, claims binding, and credential type. Required. |
| faceCheckConfiguration | [faceCheckConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/facecheckconfiguration?view=graph-rest-1.0) | Set of properties configuring Entra Verified ID Face Check behavior. Required. |
| verifiedIdUsageConfigurations | [verifiedIdUsageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidusageconfiguration?view=graph-rest-1.0) collection | Collection defining the usage purpose for the profile. The possible values are: `recovery`, `onboarding`, `all`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/v1.0/identity/verifiedId/profiles/ca15ec56-7adf-42ee-847b-00c3008264fb
Content-Type: application/json

{
  "verifiedIdUsageConfigurations": [
      {
          "isEnabledForTestOnly": false,
          "purpose": "recovery"
      }
  ]
}
  
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VerifiedIdProfile
{
	VerifiedIdUsageConfigurations = new List<VerifiedIdUsageConfiguration>
	{
		new VerifiedIdUsageConfiguration
		{
			IsEnabledForTestOnly = false,
			Purpose = VerifiedIdUsageConfigurationPurpose.Recovery,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.VerifiedId.Profiles["{verifiedIdProfile-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewVerifiedIdProfile()


verifiedIdUsageConfiguration := graphmodels.NewVerifiedIdUsageConfiguration()
isEnabledForTestOnly := false
verifiedIdUsageConfiguration.SetIsEnabledForTestOnly(&isEnabledForTestOnly) 
purpose := graphmodels.RECOVERY_VERIFIEDIDUSAGECONFIGURATIONPURPOSE 
verifiedIdUsageConfiguration.SetPurpose(&purpose) 

verifiedIdUsageConfigurations := []graphmodels.VerifiedIdUsageConfigurationable {
	verifiedIdUsageConfiguration,
}
requestBody.SetVerifiedIdUsageConfigurations(verifiedIdUsageConfigurations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
profiles, err := graphClient.Identity().VerifiedId().Profiles().ByVerifiedIdProfileId("verifiedIdProfile-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VerifiedIdProfile verifiedIdProfile = new VerifiedIdProfile();
LinkedList<VerifiedIdUsageConfiguration> verifiedIdUsageConfigurations = new LinkedList<VerifiedIdUsageConfiguration>();
VerifiedIdUsageConfiguration verifiedIdUsageConfiguration = new VerifiedIdUsageConfiguration();
verifiedIdUsageConfiguration.setIsEnabledForTestOnly(false);
verifiedIdUsageConfiguration.setPurpose(VerifiedIdUsageConfigurationPurpose.Recovery);
verifiedIdUsageConfigurations.add(verifiedIdUsageConfiguration);
verifiedIdProfile.setVerifiedIdUsageConfigurations(verifiedIdUsageConfigurations);
VerifiedIdProfile result = graphClient.identity().verifiedId().profiles().byVerifiedIdProfileId("{verifiedIdProfile-id}").patch(verifiedIdProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const verifiedIdProfile = {
  verifiedIdUsageConfigurations: [
      {
          isEnabledForTestOnly: false,
          purpose: 'recovery'
      }
  ]
};

await client.api('/identity/verifiedId/profiles/ca15ec56-7adf-42ee-847b-00c3008264fb')
	.update(verifiedIdProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VerifiedIdProfile;
use Microsoft\Graph\Generated\Models\VerifiedIdUsageConfiguration;
use Microsoft\Graph\Generated\Models\VerifiedIdUsageConfigurationPurpose;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VerifiedIdProfile();
$verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1 = new VerifiedIdUsageConfiguration();
$verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1->setIsEnabledForTestOnly(false);
$verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1->setPurpose(new VerifiedIdUsageConfigurationPurpose('recovery'));
$verifiedIdUsageConfigurationsArray []= $verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1;
$requestBody->setVerifiedIdUsageConfigurations($verifiedIdUsageConfigurationsArray);


$result = $graphServiceClient->identity()->verifiedId()->profiles()->byVerifiedIdProfileId('verifiedIdProfile-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	verifiedIdUsageConfigurations = @(
		@{
			isEnabledForTestOnly = $false
			purpose = "recovery"
		}
	)
}

Update-MgIdentityVerifiedIdProfile -VerifiedIdProfileId $verifiedIdProfileId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.verified_id_profile import VerifiedIdProfile
from msgraph.generated.models.verified_id_usage_configuration import VerifiedIdUsageConfiguration
from msgraph.generated.models.verified_id_usage_configuration_purpose import VerifiedIdUsageConfigurationPurpose
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VerifiedIdProfile(
	verified_id_usage_configurations = [
		VerifiedIdUsageConfiguration(
			is_enabled_for_test_only = False,
			purpose = VerifiedIdUsageConfigurationPurpose.Recovery,
		),
	],
)

result = await graph_client.identity.verified_id.profiles.by_verified_id_profile_id('verifiedIdProfile-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
