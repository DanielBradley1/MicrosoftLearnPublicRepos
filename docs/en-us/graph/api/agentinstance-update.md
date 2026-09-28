<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentinstance-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Update agentInstance

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Update the properties of an [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object. You can also update the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) associated with the agent instance by including the manifest in the request body.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentInstance.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentInstance.ReadWrite.All | AgentInstance.ReadWrite.ManagedBy |

Important

When using delegated permissions, the authenticated user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

*Agent Registry Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /agentRegistry/agentInstances/{agentInstanceId}
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
| ownerIds | String collection | List of owner identifiers for the agent instance, can be users or service principals. Required. |
| managedBy | String | Application identifier managing this agent. Optional. |
| originatingStore | String | Name of the store/system where agent originated. Optional. |
| createdBy | String | User who created the agent instance \(read-only\). Optional. |
| displayName | String | Display name for the agent instance. Required. |
| sourceAgentId | String | Original agent identifier from source system. Optional. |
| agentIdentityBlueprintId | String | Agent identity blueprint identifier. Optional. |
| agentIdentityId | String | Entra agent identity identifier. Optional. |
| agentUserId | String | User identifier associated with the agent. Optional. |
| createdDateTime | DateTimeOffset | Timestamp when agent instance was created \(read-only\). Optional. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of last modification \(read-only\). Optional. |
| url | String | Endpoint URL for the agent instance. Optional. |
| preferredTransport | String | Preferred transport protocol \(JSONRPC, GRPC, HTTP+JSON\). Optional. |
| additionalInterfaces | [agentInterface](https://learn.microsoft.com/en-us/graph/api/resources/agentinterface?view=graph-rest-beta) collection | Additional interfaces/transports supported by the agent \(url, transport\). Optional. |
| signatures | [agentCardSignature](https://learn.microsoft.com/en-us/graph/api/resources/agentcardsignature?view=graph-rest-beta) collection | Digital signatures for the agent instance \(protected, signature, header\). Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Update the agentCardManifest in an agentInstance

#### Request

The following example shows a request. The request also creates the agentCardManifest if it doesn't already exist.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/agentRegistry/agentInstances/{agentInstanceId}
Content-Type: application/json

{
  "agentCardManifest": {
    "ownerIds": [
      "0ef68a76-e247-41dd-947b-41282760a2ac"
    ],
    "originatingStore": "Copilot Studio",
    "displayName": "Conditional Access Agent Card",
    "description": "Manages organizational conditional access policies",
    "iconUrl": "https://example.com/icon.png",
    "provider": {
      "organization": "Test Organization",
      "url": "https://contoso.com"
    },
    "protocolVersion": "1.0",
    "version": "1.0.0",
    "documentationUrl": "https://example.com/docs",
    "capabilities": {
      "streaming": false,
      "pushNotifications": false,
      "stateTransitionHistory": true,
      "extensions": [
        {
          "uri": "https://contoso.example.com/a2a/capabilities/secureMessaging",
          "description": null,
          "required": false,
          "params": {
            "useHttps": true
          }
        }
      ]
    },
    "defaultInputModes": [
      "application/json"
    ],
    "defaultOutputModes": [
      "application/json",
      "text/html"
    ],
    "supportsAuthenticatedExtendedCard": true,
    "skills": [
      {
        "id": "threat-detection",
        "displayName": "Threat Detection",
        "description": "Detect security threats in real-time",
        "tags": [
          "security",
          "threat",
          "detection"
        ],
        "examples": [
          "Analyze this log for threats",
          "Check for malware"
        ],
        "inputModes": [
          "application/json",
          "text/plain"
        ],
        "outputModes": [
          "application/json",
          "text/html"
        ]
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AgentInstance
{
	AgentCardManifest = new AgentCardManifest
	{
		OwnerIds = new List<string>
		{
			"0ef68a76-e247-41dd-947b-41282760a2ac",
		},
		OriginatingStore = "Copilot Studio",
		DisplayName = "Conditional Access Agent Card",
		Description = "Manages organizational conditional access policies",
		IconUrl = "https://example.com/icon.png",
		Provider = new AgentProvider
		{
			Organization = "Test Organization",
			Url = "https://contoso.com",
		},
		ProtocolVersion = "1.0",
		Version = "1.0.0",
		DocumentationUrl = "https://example.com/docs",
		Capabilities = new AgentCapabilities
		{
			Streaming = false,
			PushNotifications = false,
			StateTransitionHistory = true,
			Extensions = new List<AgentExtension>
			{
				new AgentExtension
				{
					Uri = "https://contoso.example.com/a2a/capabilities/secureMessaging",
					Description = null,
					Required = false,
					Params = new AgentExtensionParams
					{
						AdditionalData = new Dictionary<string, object>
						{
							{
								"useHttps" , true
							},
						},
					},
				},
			},
		},
		DefaultInputModes = new List<string>
		{
			"application/json",
		},
		DefaultOutputModes = new List<string>
		{
			"application/json",
			"text/html",
		},
		SupportsAuthenticatedExtendedCard = true,
		Skills = new List<AgentSkill>
		{
			new AgentSkill
			{
				Id = "threat-detection",
				DisplayName = "Threat Detection",
				Description = "Detect security threats in real-time",
				Tags = new List<string>
				{
					"security",
					"threat",
					"detection",
				},
				Examples = new List<string>
				{
					"Analyze this log for threats",
					"Check for malware",
				},
				InputModes = new List<string>
				{
					"application/json",
					"text/plain",
				},
				OutputModes = new List<string>
				{
					"application/json",
					"text/html",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentInstances["{agentInstance-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewAgentInstance()
agentCardManifest := graphmodels.NewAgentCardManifest()
ownerIds := []string {
	"0ef68a76-e247-41dd-947b-41282760a2ac",
}
agentCardManifest.SetOwnerIds(ownerIds)
originatingStore := "Copilot Studio"
agentCardManifest.SetOriginatingStore(&originatingStore) 
displayName := "Conditional Access Agent Card"
agentCardManifest.SetDisplayName(&displayName) 
description := "Manages organizational conditional access policies"
agentCardManifest.SetDescription(&description) 
iconUrl := "https://example.com/icon.png"
agentCardManifest.SetIconUrl(&iconUrl) 
provider := graphmodels.NewAgentProvider()
organization := "Test Organization"
provider.SetOrganization(&organization) 
url := "https://contoso.com"
provider.SetUrl(&url) 
agentCardManifest.SetProvider(provider)
protocolVersion := "1.0"
agentCardManifest.SetProtocolVersion(&protocolVersion) 
version := "1.0.0"
agentCardManifest.SetVersion(&version) 
documentationUrl := "https://example.com/docs"
agentCardManifest.SetDocumentationUrl(&documentationUrl) 
capabilities := graphmodels.NewAgentCapabilities()
streaming := false
capabilities.SetStreaming(&streaming) 
pushNotifications := false
capabilities.SetPushNotifications(&pushNotifications) 
stateTransitionHistory := true
capabilities.SetStateTransitionHistory(&stateTransitionHistory) 


agentExtension := graphmodels.NewAgentExtension()
uri := "https://contoso.example.com/a2a/capabilities/secureMessaging"
agentExtension.SetUri(&uri) 
description := null
agentExtension.SetDescription(&description) 
required := false
agentExtension.SetRequired(&required) 
params := graphmodels.NewAgentExtensionParams()
additionalData := map[string]interface{}{
	useHttps := true
params.SetUseHttps(&useHttps) 
}
params.SetAdditionalData(additionalData)
agentExtension.SetParams(params)

extensions := []graphmodels.AgentExtensionable {
	agentExtension,
}
capabilities.SetExtensions(extensions)
agentCardManifest.SetCapabilities(capabilities)
defaultInputModes := []string {
	"application/json",
}
agentCardManifest.SetDefaultInputModes(defaultInputModes)
defaultOutputModes := []string {
	"application/json",
	"text/html",
}
agentCardManifest.SetDefaultOutputModes(defaultOutputModes)
supportsAuthenticatedExtendedCard := true
agentCardManifest.SetSupportsAuthenticatedExtendedCard(&supportsAuthenticatedExtendedCard) 


agentSkill := graphmodels.NewAgentSkill()
id := "threat-detection"
agentSkill.SetId(&id) 
displayName := "Threat Detection"
agentSkill.SetDisplayName(&displayName) 
description := "Detect security threats in real-time"
agentSkill.SetDescription(&description) 
tags := []string {
	"security",
	"threat",
	"detection",
}
agentSkill.SetTags(tags)
examples := []string {
	"Analyze this log for threats",
	"Check for malware",
}
agentSkill.SetExamples(examples)
inputModes := []string {
	"application/json",
	"text/plain",
}
agentSkill.SetInputModes(inputModes)
outputModes := []string {
	"application/json",
	"text/html",
}
agentSkill.SetOutputModes(outputModes)

skills := []graphmodels.AgentSkillable {
	agentSkill,
}
agentCardManifest.SetSkills(skills)
requestBody.SetAgentCardManifest(agentCardManifest)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentInstances, err := graphClient.AgentRegistry().AgentInstances().ByAgentInstanceId("agentInstance-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentInstance agentInstance = new AgentInstance();
AgentCardManifest agentCardManifest = new AgentCardManifest();
LinkedList<String> ownerIds = new LinkedList<String>();
ownerIds.add("0ef68a76-e247-41dd-947b-41282760a2ac");
agentCardManifest.setOwnerIds(ownerIds);
agentCardManifest.setOriginatingStore("Copilot Studio");
agentCardManifest.setDisplayName("Conditional Access Agent Card");
agentCardManifest.setDescription("Manages organizational conditional access policies");
agentCardManifest.setIconUrl("https://example.com/icon.png");
AgentProvider provider = new AgentProvider();
provider.setOrganization("Test Organization");
provider.setUrl("https://contoso.com");
agentCardManifest.setProvider(provider);
agentCardManifest.setProtocolVersion("1.0");
agentCardManifest.setVersion("1.0.0");
agentCardManifest.setDocumentationUrl("https://example.com/docs");
AgentCapabilities capabilities = new AgentCapabilities();
capabilities.setStreaming(false);
capabilities.setPushNotifications(false);
capabilities.setStateTransitionHistory(true);
LinkedList<AgentExtension> extensions = new LinkedList<AgentExtension>();
AgentExtension agentExtension = new AgentExtension();
agentExtension.setUri("https://contoso.example.com/a2a/capabilities/secureMessaging");
agentExtension.setDescription(null);
agentExtension.setRequired(false);
AgentExtensionParams params = new AgentExtensionParams();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("useHttps", true);
params.setAdditionalData(additionalData);
agentExtension.setParams(params);
extensions.add(agentExtension);
capabilities.setExtensions(extensions);
agentCardManifest.setCapabilities(capabilities);
LinkedList<String> defaultInputModes = new LinkedList<String>();
defaultInputModes.add("application/json");
agentCardManifest.setDefaultInputModes(defaultInputModes);
LinkedList<String> defaultOutputModes = new LinkedList<String>();
defaultOutputModes.add("application/json");
defaultOutputModes.add("text/html");
agentCardManifest.setDefaultOutputModes(defaultOutputModes);
agentCardManifest.setSupportsAuthenticatedExtendedCard(true);
LinkedList<AgentSkill> skills = new LinkedList<AgentSkill>();
AgentSkill agentSkill = new AgentSkill();
agentSkill.setId("threat-detection");
agentSkill.setDisplayName("Threat Detection");
agentSkill.setDescription("Detect security threats in real-time");
LinkedList<String> tags = new LinkedList<String>();
tags.add("security");
tags.add("threat");
tags.add("detection");
agentSkill.setTags(tags);
LinkedList<String> examples = new LinkedList<String>();
examples.add("Analyze this log for threats");
examples.add("Check for malware");
agentSkill.setExamples(examples);
LinkedList<String> inputModes = new LinkedList<String>();
inputModes.add("application/json");
inputModes.add("text/plain");
agentSkill.setInputModes(inputModes);
LinkedList<String> outputModes = new LinkedList<String>();
outputModes.add("application/json");
outputModes.add("text/html");
agentSkill.setOutputModes(outputModes);
skills.add(agentSkill);
agentCardManifest.setSkills(skills);
agentInstance.setAgentCardManifest(agentCardManifest);
AgentInstance result = graphClient.agentRegistry().agentInstances().byAgentInstanceId("{agentInstance-id}").patch(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentInstance = {
  agentCardManifest: {
    ownerIds: [
      '0ef68a76-e247-41dd-947b-41282760a2ac'
    ],
    originatingStore: 'Copilot Studio',
    displayName: 'Conditional Access Agent Card',
    description: 'Manages organizational conditional access policies',
    iconUrl: 'https://example.com/icon.png',
    provider: {
      organization: 'Test Organization',
      url: 'https://contoso.com'
    },
    protocolVersion: '1.0',
    version: '1.0.0',
    documentationUrl: 'https://example.com/docs',
    capabilities: {
      streaming: false,
      pushNotifications: false,
      stateTransitionHistory: true,
      extensions: [
        {
          uri: 'https://contoso.example.com/a2a/capabilities/secureMessaging',
          description: null,
          required: false,
          params: {
            useHttps: true
          }
        }
      ]
    },
    defaultInputModes: [
      'application/json'
    ],
    defaultOutputModes: [
      'application/json',
      'text/html'
    ],
    supportsAuthenticatedExtendedCard: true,
    skills: [
      {
        id: 'threat-detection',
        displayName: 'Threat Detection',
        description: 'Detect security threats in real-time',
        tags: [
          'security',
          'threat',
          'detection'
        ],
        examples: [
          'Analyze this log for threats',
          'Check for malware'
        ],
        inputModes: [
          'application/json',
          'text/plain'
        ],
        outputModes: [
          'application/json',
          'text/html'
        ]
      }
    ]
  }
};

await client.api('/agentRegistry/agentInstances/{agentInstanceId}')
	.version('beta')
	.update(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentInstance;
use Microsoft\Graph\Beta\Generated\Models\AgentCardManifest;
use Microsoft\Graph\Beta\Generated\Models\AgentProvider;
use Microsoft\Graph\Beta\Generated\Models\AgentCapabilities;
use Microsoft\Graph\Beta\Generated\Models\AgentExtension;
use Microsoft\Graph\Beta\Generated\Models\AgentExtensionParams;
use Microsoft\Graph\Beta\Generated\Models\AgentSkill;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentInstance();
$agentCardManifest = new AgentCardManifest();
$agentCardManifest->setOwnerIds(['0ef68a76-e247-41dd-947b-41282760a2ac', 	]);
$agentCardManifest->setOriginatingStore('Copilot Studio');
$agentCardManifest->setDisplayName('Conditional Access Agent Card');
$agentCardManifest->setDescription('Manages organizational conditional access policies');
$agentCardManifest->setIconUrl('https://example.com/icon.png');
$agentCardManifestProvider = new AgentProvider();
$agentCardManifestProvider->setOrganization('Test Organization');
$agentCardManifestProvider->setUrl('https://contoso.com');
$agentCardManifest->setProvider($agentCardManifestProvider);
$agentCardManifest->setProtocolVersion('1.0');
$agentCardManifest->setVersion('1.0.0');
$agentCardManifest->setDocumentationUrl('https://example.com/docs');
$agentCardManifestCapabilities = new AgentCapabilities();
$agentCardManifestCapabilities->setStreaming(false);
$agentCardManifestCapabilities->setPushNotifications(false);
$agentCardManifestCapabilities->setStateTransitionHistory(true);
$extensionsAgentExtension1 = new AgentExtension();
$extensionsAgentExtension1->setUri('https://contoso.example.com/a2a/capabilities/secureMessaging');
$extensionsAgentExtension1->setDescription(null);
$extensionsAgentExtension1->setRequired(false);
$extensionsAgentExtension1Params = new AgentExtensionParams();
$additionalData = [
	'useHttps' => true,
];
$extensionsAgentExtension1Params->setAdditionalData($additionalData);
$extensionsAgentExtension1->setParams($extensionsAgentExtension1Params);
$extensionsArray []= $extensionsAgentExtension1;
$agentCardManifestCapabilities->setExtensions($extensionsArray);

$agentCardManifest->setCapabilities($agentCardManifestCapabilities);
$agentCardManifest->setDefaultInputModes(['application/json', ]);
$agentCardManifest->setDefaultOutputModes(['application/json', 'text/html', ]);
$agentCardManifest->setSupportsAuthenticatedExtendedCard(true);
$skillsAgentSkill1 = new AgentSkill();
$skillsAgentSkill1->setId('threat-detection');
$skillsAgentSkill1->setDisplayName('Threat Detection');
$skillsAgentSkill1->setDescription('Detect security threats in real-time');
$skillsAgentSkill1->setTags(['security', 'threat', 'detection', ]);
$skillsAgentSkill1->setExamples(['Analyze this log for threats', 'Check for malware', ]);
$skillsAgentSkill1->setInputModes(['application/json', 'text/plain', ]);
$skillsAgentSkill1->setOutputModes(['application/json', 'text/html', ]);
$skillsArray []= $skillsAgentSkill1;
$agentCardManifest->setSkills($skillsArray);

$requestBody->setAgentCardManifest($agentCardManifest);

$result = $graphServiceClient->agentRegistry()->agentInstances()->byAgentInstanceId('agentInstance-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_instance import AgentInstance
from msgraph_beta.generated.models.agent_card_manifest import AgentCardManifest
from msgraph_beta.generated.models.agent_provider import AgentProvider
from msgraph_beta.generated.models.agent_capabilities import AgentCapabilities
from msgraph_beta.generated.models.agent_extension import AgentExtension
from msgraph_beta.generated.models.agent_extension_params import AgentExtensionParams
from msgraph_beta.generated.models.agent_skill import AgentSkill
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentInstance(
	agent_card_manifest = AgentCardManifest(
		owner_ids = [
			"0ef68a76-e247-41dd-947b-41282760a2ac",
		],
		originating_store = "Copilot Studio",
		display_name = "Conditional Access Agent Card",
		description = "Manages organizational conditional access policies",
		icon_url = "https://example.com/icon.png",
		provider = AgentProvider(
			organization = "Test Organization",
			url = "https://contoso.com",
		),
		protocol_version = "1.0",
		version = "1.0.0",
		documentation_url = "https://example.com/docs",
		capabilities = AgentCapabilities(
			streaming = False,
			push_notifications = False,
			state_transition_history = True,
			extensions = [
				AgentExtension(
					uri = "https://contoso.example.com/a2a/capabilities/secureMessaging",
					description = None,
					required = False,
					params = AgentExtensionParams(
						additional_data = {
								"use_https" : True,
						}
					),
				),
			],
		),
		default_input_modes = [
			"application/json",
		],
		default_output_modes = [
			"application/json",
			"text/html",
		],
		supports_authenticated_extended_card = True,
		skills = [
			AgentSkill(
				id = "threat-detection",
				display_name = "Threat Detection",
				description = "Detect security threats in real-time",
				tags = [
					"security",
					"threat",
					"detection",
				],
				examples = [
					"Analyze this log for threats",
					"Check for malware",
				],
				input_modes = [
					"application/json",
					"text/plain",
				],
				output_modes = [
					"application/json",
					"text/html",
				],
			),
		],
	),
)

result = await graph_client.agent_registry.agent_instances.by_agent_instance_id('agentInstance-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update an agentInstance to reference an existing agentCardManifest

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/beta/agentRegistry/agentInstances/{agentInstanceId}
Content-Type: application/json

{
  "agentCardManifest@odata.bind": "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AgentInstance
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"agentCardManifest@odata.bind" , "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentInstances["{agentInstance-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewAgentInstance()
additionalData := map[string]interface{}{
	"agentCardManifest@odata.bind" : "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentInstances, err := graphClient.AgentRegistry().AgentInstances().ByAgentInstanceId("agentInstance-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentInstance agentInstance = new AgentInstance();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("agentCardManifest@odata.bind", "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')");
agentInstance.setAdditionalData(additionalData);
AgentInstance result = graphClient.agentRegistry().agentInstances().byAgentInstanceId("{agentInstance-id}").patch(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentInstance = {
  'agentCardManifest@odata.bind': 'https://graph.microsoft.com/beta/agentRegistry/agentCardManifests(\'employee-assistant\')'
};

await client.api('/agentRegistry/agentInstances/{agentInstanceId}')
	.version('beta')
	.update(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentInstance;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentInstance();
$additionalData = [
	'agentCardManifest@odata.bind' => 'https://graph.microsoft.com/beta/agentRegistry/agentCardManifests(\'employee-assistant\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->agentRegistry()->agentInstances()->byAgentInstanceId('agentInstance-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_instance import AgentInstance
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentInstance(
	additional_data = {
			"agent_card_manifest@odata_bind" : "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')",
	}
)

result = await graph_client.agent_registry.agent_instances.by_agent_instance_id('agentInstance-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Update displayName

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/beta/agentRegistry/agentInstances/{agentInstanceId}
Content-Type: application/json

{
  "displayName": "Teams Meeting Scheduler Agent"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AgentInstance
{
	DisplayName = "Teams Meeting Scheduler Agent",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentInstances["{agentInstance-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewAgentInstance()
displayName := "Teams Meeting Scheduler Agent"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentInstances, err := graphClient.AgentRegistry().AgentInstances().ByAgentInstanceId("agentInstance-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentInstance agentInstance = new AgentInstance();
agentInstance.setDisplayName("Teams Meeting Scheduler Agent");
AgentInstance result = graphClient.agentRegistry().agentInstances().byAgentInstanceId("{agentInstance-id}").patch(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentInstance = {
  displayName: 'Teams Meeting Scheduler Agent'
};

await client.api('/agentRegistry/agentInstances/{agentInstanceId}')
	.version('beta')
	.update(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentInstance;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentInstance();
$requestBody->setDisplayName('Teams Meeting Scheduler Agent');

$result = $graphServiceClient->agentRegistry()->agentInstances()->byAgentInstanceId('agentInstance-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_instance import AgentInstance
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentInstance(
	display_name = "Teams Meeting Scheduler Agent",
)

result = await graph_client.agent_registry.agent_instances.by_agent_instance_id('agentInstance-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
