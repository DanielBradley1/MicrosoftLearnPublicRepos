<!-- Source: https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-post-profiles?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# Create verifiedIdProfile

Namespace: microsoft.graph

Create a new [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) object.

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
POST /identity/verifiedId/profiles
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) object.

You can specify the following properties when creating a **verifiedIdProfile**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Display name for the verified Id profile. Required. |
| description | String | Description for the verified Id profile. Required. |
| state | verifiedIdProfileState | Enablement state for the profile. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Required. |
| verifierDid | String | Decentralized Identifier \(DID\) string that represents the verifier in the verifiable credential exchange. Required. |
| priority | Int32 | Defines profile processing priority if multiple profiles are configured. Optional. |
| verifiedIdProfileConfiguration | [verifiedIdProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofileconfiguration?view=graph-rest-1.0) | Set of properties expressing the accepted issuer, claims binding, and credential type. Required. |
| faceCheckConfiguration | [faceCheckConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/facecheckconfiguration?view=graph-rest-1.0) | Set of properties configuring Entra Verified ID Face Check behavior. Required. |
| verifiedIdUsageConfigurations | [verifiedIdUsageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidusageconfiguration?view=graph-rest-1.0) collection | Collection defining the usage purpose for the profile. The possible values are: `recovery`, `onboarding`, `all`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/identity/verifiedId/profiles
Content-Type: application/json

{
  "name": "Contoso Verified ID",
  "description": "Contoso Verified Identity",
  "lastModifiedDateTime": null,
  "state": "enabled",
  "verifierDid": "did:web:eu.did-dev.contoso.io",
  "priority": 0,
  "verifiedIdProfileConfiguration": {
      "type": "verifiedIdentity",
      "acceptedIssuer": "did:web:eu.did-dev.contoso.io",
      "claimBindingSource": "directory",
      "claimBindings": [
          {
              "matchConfidenceLevel": "exact",
              "sourceAttribute": "First name",
              "verifiedIdClaim": "vc.credentialSubject.firstName"
          },
          {
              "matchConfidenceLevel": "exact",
              "sourceAttribute": "Last name",
              "verifiedIdClaim": "vc.credentialSubject.lastName"
          }
      ],
      "claimValidation": {
          "isEnabled": true,
          "customExtensionId": "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
      }
  },
  "faceCheckConfiguration": {
      "isEnabled": true,
      "sourcePhotoClaimName": "portrait"
  },
  "verifiedIdUsageConfigurations": [
      {
          "isEnabledForTestOnly": true,
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
	Name = "Contoso Verified ID",
	Description = "Contoso Verified Identity",
	LastModifiedDateTime = null,
	State = VerifiedIdProfileState.Enabled,
	VerifierDid = "did:web:eu.did-dev.contoso.io",
	Priority = 0,
	VerifiedIdProfileConfiguration = new VerifiedIdProfileConfiguration
	{
		Type = "verifiedIdentity",
		AcceptedIssuer = "did:web:eu.did-dev.contoso.io",
		ClaimBindingSource = ClaimBindingSource.Directory,
		ClaimBindings = new List<ClaimBinding>
		{
			new ClaimBinding
			{
				MatchConfidenceLevel = MatchConfidenceLevel.Exact,
				SourceAttribute = "First name",
				VerifiedIdClaim = "vc.credentialSubject.firstName",
			},
			new ClaimBinding
			{
				MatchConfidenceLevel = MatchConfidenceLevel.Exact,
				SourceAttribute = "Last name",
				VerifiedIdClaim = "vc.credentialSubject.lastName",
			},
		},
		ClaimValidation = new ClaimValidation
		{
			IsEnabled = true,
			CustomExtensionId = "00aa00aa-bb11-cc22-dd33-44ee44ee44ee",
		},
	},
	FaceCheckConfiguration = new FaceCheckConfiguration
	{
		IsEnabled = true,
		SourcePhotoClaimName = "portrait",
	},
	VerifiedIdUsageConfigurations = new List<VerifiedIdUsageConfiguration>
	{
		new VerifiedIdUsageConfiguration
		{
			IsEnabledForTestOnly = true,
			Purpose = VerifiedIdUsageConfigurationPurpose.Recovery,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.VerifiedId.Profiles.PostAsync(requestBody);
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
name := "Contoso Verified ID"
requestBody.SetName(&name) 
description := "Contoso Verified Identity"
requestBody.SetDescription(&description) 
lastModifiedDateTime := null
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
state := graphmodels.ENABLED_VERIFIEDIDPROFILESTATE 
requestBody.SetState(&state) 
verifierDid := "did:web:eu.did-dev.contoso.io"
requestBody.SetVerifierDid(&verifierDid) 
priority := int32(0)
requestBody.SetPriority(&priority) 
verifiedIdProfileConfiguration := graphmodels.NewVerifiedIdProfileConfiguration()
type := "verifiedIdentity"
verifiedIdProfileConfiguration.SetType(&type) 
acceptedIssuer := "did:web:eu.did-dev.contoso.io"
verifiedIdProfileConfiguration.SetAcceptedIssuer(&acceptedIssuer) 
claimBindingSource := graphmodels.DIRECTORY_CLAIMBINDINGSOURCE 
verifiedIdProfileConfiguration.SetClaimBindingSource(&claimBindingSource) 


claimBinding := graphmodels.NewClaimBinding()
matchConfidenceLevel := graphmodels.EXACT_MATCHCONFIDENCELEVEL 
claimBinding.SetMatchConfidenceLevel(&matchConfidenceLevel) 
sourceAttribute := "First name"
claimBinding.SetSourceAttribute(&sourceAttribute) 
verifiedIdClaim := "vc.credentialSubject.firstName"
claimBinding.SetVerifiedIdClaim(&verifiedIdClaim) 
claimBinding1 := graphmodels.NewClaimBinding()
matchConfidenceLevel := graphmodels.EXACT_MATCHCONFIDENCELEVEL 
claimBinding1.SetMatchConfidenceLevel(&matchConfidenceLevel) 
sourceAttribute := "Last name"
claimBinding1.SetSourceAttribute(&sourceAttribute) 
verifiedIdClaim := "vc.credentialSubject.lastName"
claimBinding1.SetVerifiedIdClaim(&verifiedIdClaim) 

claimBindings := []graphmodels.ClaimBindingable {
	claimBinding,
	claimBinding1,
}
verifiedIdProfileConfiguration.SetClaimBindings(claimBindings)
claimValidation := graphmodels.NewClaimValidation()
isEnabled := true
claimValidation.SetIsEnabled(&isEnabled) 
customExtensionId := "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
claimValidation.SetCustomExtensionId(&customExtensionId) 
verifiedIdProfileConfiguration.SetClaimValidation(claimValidation)
requestBody.SetVerifiedIdProfileConfiguration(verifiedIdProfileConfiguration)
faceCheckConfiguration := graphmodels.NewFaceCheckConfiguration()
isEnabled := true
faceCheckConfiguration.SetIsEnabled(&isEnabled) 
sourcePhotoClaimName := "portrait"
faceCheckConfiguration.SetSourcePhotoClaimName(&sourcePhotoClaimName) 
requestBody.SetFaceCheckConfiguration(faceCheckConfiguration)


verifiedIdUsageConfiguration := graphmodels.NewVerifiedIdUsageConfiguration()
isEnabledForTestOnly := true
verifiedIdUsageConfiguration.SetIsEnabledForTestOnly(&isEnabledForTestOnly) 
purpose := graphmodels.RECOVERY_VERIFIEDIDUSAGECONFIGURATIONPURPOSE 
verifiedIdUsageConfiguration.SetPurpose(&purpose) 

verifiedIdUsageConfigurations := []graphmodels.VerifiedIdUsageConfigurationable {
	verifiedIdUsageConfiguration,
}
requestBody.SetVerifiedIdUsageConfigurations(verifiedIdUsageConfigurations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
profiles, err := graphClient.Identity().VerifiedId().Profiles().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VerifiedIdProfile verifiedIdProfile = new VerifiedIdProfile();
verifiedIdProfile.setName("Contoso Verified ID");
verifiedIdProfile.setDescription("Contoso Verified Identity");
verifiedIdProfile.setLastModifiedDateTime(null);
verifiedIdProfile.setState(VerifiedIdProfileState.Enabled);
verifiedIdProfile.setVerifierDid("did:web:eu.did-dev.contoso.io");
verifiedIdProfile.setPriority(0);
VerifiedIdProfileConfiguration verifiedIdProfileConfiguration = new VerifiedIdProfileConfiguration();
verifiedIdProfileConfiguration.setType("verifiedIdentity");
verifiedIdProfileConfiguration.setAcceptedIssuer("did:web:eu.did-dev.contoso.io");
verifiedIdProfileConfiguration.setClaimBindingSource(ClaimBindingSource.Directory);
LinkedList<ClaimBinding> claimBindings = new LinkedList<ClaimBinding>();
ClaimBinding claimBinding = new ClaimBinding();
claimBinding.setMatchConfidenceLevel(MatchConfidenceLevel.Exact);
claimBinding.setSourceAttribute("First name");
claimBinding.setVerifiedIdClaim("vc.credentialSubject.firstName");
claimBindings.add(claimBinding);
ClaimBinding claimBinding1 = new ClaimBinding();
claimBinding1.setMatchConfidenceLevel(MatchConfidenceLevel.Exact);
claimBinding1.setSourceAttribute("Last name");
claimBinding1.setVerifiedIdClaim("vc.credentialSubject.lastName");
claimBindings.add(claimBinding1);
verifiedIdProfileConfiguration.setClaimBindings(claimBindings);
ClaimValidation claimValidation = new ClaimValidation();
claimValidation.setIsEnabled(true);
claimValidation.setCustomExtensionId("00aa00aa-bb11-cc22-dd33-44ee44ee44ee");
verifiedIdProfileConfiguration.setClaimValidation(claimValidation);
verifiedIdProfile.setVerifiedIdProfileConfiguration(verifiedIdProfileConfiguration);
FaceCheckConfiguration faceCheckConfiguration = new FaceCheckConfiguration();
faceCheckConfiguration.setIsEnabled(true);
faceCheckConfiguration.setSourcePhotoClaimName("portrait");
verifiedIdProfile.setFaceCheckConfiguration(faceCheckConfiguration);
LinkedList<VerifiedIdUsageConfiguration> verifiedIdUsageConfigurations = new LinkedList<VerifiedIdUsageConfiguration>();
VerifiedIdUsageConfiguration verifiedIdUsageConfiguration = new VerifiedIdUsageConfiguration();
verifiedIdUsageConfiguration.setIsEnabledForTestOnly(true);
verifiedIdUsageConfiguration.setPurpose(VerifiedIdUsageConfigurationPurpose.Recovery);
verifiedIdUsageConfigurations.add(verifiedIdUsageConfiguration);
verifiedIdProfile.setVerifiedIdUsageConfigurations(verifiedIdUsageConfigurations);
VerifiedIdProfile result = graphClient.identity().verifiedId().profiles().post(verifiedIdProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const verifiedIdProfile = {
  name: 'Contoso Verified ID',
  description: 'Contoso Verified Identity',
  lastModifiedDateTime: null,
  state: 'enabled',
  verifierDid: 'did:web:eu.did-dev.contoso.io',
  priority: 0,
  verifiedIdProfileConfiguration: {
      type: 'verifiedIdentity',
      acceptedIssuer: 'did:web:eu.did-dev.contoso.io',
      claimBindingSource: 'directory',
      claimBindings: [
          {
              matchConfidenceLevel: 'exact',
              sourceAttribute: 'First name',
              verifiedIdClaim: 'vc.credentialSubject.firstName'
          },
          {
              matchConfidenceLevel: 'exact',
              sourceAttribute: 'Last name',
              verifiedIdClaim: 'vc.credentialSubject.lastName'
          }
      ],
      claimValidation: {
          isEnabled: true,
          customExtensionId: '00aa00aa-bb11-cc22-dd33-44ee44ee44ee'
      }
  },
  faceCheckConfiguration: {
      isEnabled: true,
      sourcePhotoClaimName: 'portrait'
  },
  verifiedIdUsageConfigurations: [
      {
          isEnabledForTestOnly: true,
          purpose: 'recovery'
      }
  ]
};

await client.api('/identity/verifiedId/profiles')
	.post(verifiedIdProfile);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VerifiedIdProfile;
use Microsoft\Graph\Generated\Models\VerifiedIdProfileState;
use Microsoft\Graph\Generated\Models\VerifiedIdProfileConfiguration;
use Microsoft\Graph\Generated\Models\ClaimBindingSource;
use Microsoft\Graph\Generated\Models\ClaimBinding;
use Microsoft\Graph\Generated\Models\MatchConfidenceLevel;
use Microsoft\Graph\Generated\Models\ClaimValidation;
use Microsoft\Graph\Generated\Models\FaceCheckConfiguration;
use Microsoft\Graph\Generated\Models\VerifiedIdUsageConfiguration;
use Microsoft\Graph\Generated\Models\VerifiedIdUsageConfigurationPurpose;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VerifiedIdProfile();
$requestBody->setName('Contoso Verified ID');
$requestBody->setDescription('Contoso Verified Identity');
$requestBody->setLastModifiedDateTime(null);
$requestBody->setState(new VerifiedIdProfileState('enabled'));
$requestBody->setVerifierDid('did:web:eu.did-dev.contoso.io');
$requestBody->setPriority(0);
$verifiedIdProfileConfiguration = new VerifiedIdProfileConfiguration();
$verifiedIdProfileConfiguration->setType('verifiedIdentity');
$verifiedIdProfileConfiguration->setAcceptedIssuer('did:web:eu.did-dev.contoso.io');
$verifiedIdProfileConfiguration->setClaimBindingSource(new ClaimBindingSource('directory'));
$claimBindingsClaimBinding1 = new ClaimBinding();
$claimBindingsClaimBinding1->setMatchConfidenceLevel(new MatchConfidenceLevel('exact'));
$claimBindingsClaimBinding1->setSourceAttribute('First name');
$claimBindingsClaimBinding1->setVerifiedIdClaim('vc.credentialSubject.firstName');
$claimBindingsArray []= $claimBindingsClaimBinding1;
$claimBindingsClaimBinding2 = new ClaimBinding();
$claimBindingsClaimBinding2->setMatchConfidenceLevel(new MatchConfidenceLevel('exact'));
$claimBindingsClaimBinding2->setSourceAttribute('Last name');
$claimBindingsClaimBinding2->setVerifiedIdClaim('vc.credentialSubject.lastName');
$claimBindingsArray []= $claimBindingsClaimBinding2;
$verifiedIdProfileConfiguration->setClaimBindings($claimBindingsArray);

$verifiedIdProfileConfigurationClaimValidation = new ClaimValidation();
$verifiedIdProfileConfigurationClaimValidation->setIsEnabled(true);
$verifiedIdProfileConfigurationClaimValidation->setCustomExtensionId('00aa00aa-bb11-cc22-dd33-44ee44ee44ee');
$verifiedIdProfileConfiguration->setClaimValidation($verifiedIdProfileConfigurationClaimValidation);
$requestBody->setVerifiedIdProfileConfiguration($verifiedIdProfileConfiguration);
$faceCheckConfiguration = new FaceCheckConfiguration();
$faceCheckConfiguration->setIsEnabled(true);
$faceCheckConfiguration->setSourcePhotoClaimName('portrait');
$requestBody->setFaceCheckConfiguration($faceCheckConfiguration);
$verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1 = new VerifiedIdUsageConfiguration();
$verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1->setIsEnabledForTestOnly(true);
$verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1->setPurpose(new VerifiedIdUsageConfigurationPurpose('recovery'));
$verifiedIdUsageConfigurationsArray []= $verifiedIdUsageConfigurationsVerifiedIdUsageConfiguration1;
$requestBody->setVerifiedIdUsageConfigurations($verifiedIdUsageConfigurationsArray);


$result = $graphServiceClient->identity()->verifiedId()->profiles()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	name = "Contoso Verified ID"
	description = "Contoso Verified Identity"
	lastModifiedDateTime = $null
	state = "enabled"
	verifierDid = "did:web:eu.did-dev.contoso.io"
	priority = 0
	verifiedIdProfileConfiguration = @{
		type = "verifiedIdentity"
		acceptedIssuer = "did:web:eu.did-dev.contoso.io"
		claimBindingSource = "directory"
		claimBindings = @(
			@{
				matchConfidenceLevel = "exact"
				sourceAttribute = "First name"
				verifiedIdClaim = "vc.credentialSubject.firstName"
			}
			@{
				matchConfidenceLevel = "exact"
				sourceAttribute = "Last name"
				verifiedIdClaim = "vc.credentialSubject.lastName"
			}
		)
		claimValidation = @{
			isEnabled = $true
			customExtensionId = "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
		}
	}
	faceCheckConfiguration = @{
		isEnabled = $true
		sourcePhotoClaimName = "portrait"
	}
	verifiedIdUsageConfigurations = @(
		@{
			isEnabledForTestOnly = $true
			purpose = "recovery"
		}
	)
}

New-MgIdentityVerifiedIdProfile -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.verified_id_profile import VerifiedIdProfile
from msgraph.generated.models.verified_id_profile_state import VerifiedIdProfileState
from msgraph.generated.models.verified_id_profile_configuration import VerifiedIdProfileConfiguration
from msgraph.generated.models.claim_binding_source import ClaimBindingSource
from msgraph.generated.models.claim_binding import ClaimBinding
from msgraph.generated.models.match_confidence_level import MatchConfidenceLevel
from msgraph.generated.models.claim_validation import ClaimValidation
from msgraph.generated.models.face_check_configuration import FaceCheckConfiguration
from msgraph.generated.models.verified_id_usage_configuration import VerifiedIdUsageConfiguration
from msgraph.generated.models.verified_id_usage_configuration_purpose import VerifiedIdUsageConfigurationPurpose
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VerifiedIdProfile(
	name = "Contoso Verified ID",
	description = "Contoso Verified Identity",
	last_modified_date_time = None,
	state = VerifiedIdProfileState.Enabled,
	verifier_did = "did:web:eu.did-dev.contoso.io",
	priority = 0,
	verified_id_profile_configuration = VerifiedIdProfileConfiguration(
		type = "verifiedIdentity",
		accepted_issuer = "did:web:eu.did-dev.contoso.io",
		claim_binding_source = ClaimBindingSource.Directory,
		claim_bindings = [
			ClaimBinding(
				match_confidence_level = MatchConfidenceLevel.Exact,
				source_attribute = "First name",
				verified_id_claim = "vc.credentialSubject.firstName",
			),
			ClaimBinding(
				match_confidence_level = MatchConfidenceLevel.Exact,
				source_attribute = "Last name",
				verified_id_claim = "vc.credentialSubject.lastName",
			),
		],
		claim_validation = ClaimValidation(
			is_enabled = True,
			custom_extension_id = "00aa00aa-bb11-cc22-dd33-44ee44ee44ee",
		),
	),
	face_check_configuration = FaceCheckConfiguration(
		is_enabled = True,
		source_photo_claim_name = "portrait",
	),
	verified_id_usage_configurations = [
		VerifiedIdUsageConfiguration(
			is_enabled_for_test_only = True,
			purpose = VerifiedIdUsageConfigurationPurpose.Recovery,
		),
	],
)

result = await graph_client.identity.verified_id.profiles.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/verifiedId/profiles/$entity",
    "id": "ca15ec56-7adf-42ee-847b-00c3008264fb",
    "name": "Contoso Verified ID",
    "description": "Contoso Verified ID",
    "lastModifiedDateTime": null,
    "state": "enabled",
    "verifierDid": "did:web:eu.did-dev.contoso.io",
    "priority": 0,
    "verifiedIdProfileConfiguration": {
        "type": "verifiedIdentity",
        "acceptedIssuer": "did:web:eu.did-dev.contoso.io",
        "claimBindingSource": "directory",
        "claimBindings": [
            {
                "matchConfidenceLevel": "exact",
                "sourceAttribute": "First name",
                "verifiedIdClaim": "vc.credentialSubject.firstName"
            },
            {
                "matchConfidenceLevel": "exact",
                "sourceAttribute": "Last name",
                "verifiedIdClaim": "vc.credentialSubject.lastName"
            }
        ],
        "claimValidation": {
            "isEnabled": true,
            "customExtensionId": "00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
        }
    },
    "faceCheckConfiguration": {
        "isEnabled": true,
        "sourcePhotoClaimName": "portrait"
    },
    "verifiedIdUsageConfigurations": [
        {
            "isEnabledForTestOnly": true,
            "purpose": "onboarding"
        }
    ]
}
```
