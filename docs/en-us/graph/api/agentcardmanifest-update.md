<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentcardmanifest-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Update agentCardManifest

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Update the properties of an [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentCardManifest.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentCardManifest.ReadWrite.All | AgentCardManifest.ReadWrite.ManagedBy |

Important

When using delegated permissions, the authenticated user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

*Agent Registry Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /agentRegistry/agentCardManifests/{agentCardManifestId}
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
| displayName | String | Display name of the agent. Optional. |
| description | String | Description of the agent's purpose. Optional. |
| iconUrl | String | URL to agent's icon image. Optional. |
| protocolVersion | String | Protocol version supported by the agent. Optional. |
| version | String | Version of the agent implementation. Optional. |
| documentationUrl | String | URL to agent's documentation. Optional. |
| defaultInputModes | String collection | Default input modes supported. Optional. |
| defaultOutputModes | String collection | Default output modes supported. Optional. |
| provider | [agentProvider](https://learn.microsoft.com/en-us/graph/api/resources/agentprovider?view=graph-rest-beta) | Information about the organization providing the agent. Optional. |
| securitySchemes | [securitySchemes](https://learn.microsoft.com/en-us/graph/api/resources/securityschemes?view=graph-rest-beta) | Dictionary of security scheme definitions keyed by scheme name. Optional. |
| security | [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/securityrequirement?view=graph-rest-beta) collection | Security requirements - array of security scheme references. Optional. |
| capabilities | [agentCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/agentcapabilities?view=graph-rest-beta) | Specific capabilities supported by the agent. Optional. |
| skills | [agentSkill](https://learn.microsoft.com/en-us/graph/api/resources/agentskill?view=graph-rest-beta) collection | Skills/capabilities that the agent can perform. Optional. |
| supportsAuthenticatedExtendedCard | Boolean | Whether agent supports authenticated extended card retrieval. Optional. |
| ownerIds | String collection | List of owner identifiers for the agent card manifest, can be users or service principals. Optional. |
| managedBy | String | Application identifier managing this manifest. Optional. |
| originatingStore | String | Name of the store/system where agent originated. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/agentRegistry/agentCardManifests/{agentCardManifestId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.agentCardManifest",
  "ownerIds": [
    "String"
  ],
  "managedBy": "String",
  "originatingStore": "String",
  "createdBy": "String",
  "protocolVersion": "String",
  "displayName": "String",
  "description": "String",
  "iconUrl": "String",
  "provider": {
    "@odata.type": "microsoft.graph.agentProvider"
  },
  "version": "String",
  "documentationUrl": "String",
  "capabilities": {
    "@odata.type": "microsoft.graph.agentCapabilities"
  },
  "securitySchemes": {
    "@odata.type": "microsoft.graph.securitySchemes"
  },
  "security": [
    {
      "@odata.type": "microsoft.graph.securityRequirement"
    }
  ],
  "defaultInputModes": [
    "String"
  ],
  "defaultOutputModes": [
    "String"
  ],
  "skills": [
    {
      "@odata.type": "microsoft.graph.agentSkill"
    }
  ],
  "supportsAuthenticatedExtendedCard": "Boolean"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AgentCardManifest
{
	OdataType = "#microsoft.graph.agentCardManifest",
	OwnerIds = new List<string>
	{
		"String",
	},
	ManagedBy = "String",
	OriginatingStore = "String",
	CreatedBy = "String",
	ProtocolVersion = "String",
	DisplayName = "String",
	Description = "String",
	IconUrl = "String",
	Provider = new AgentProvider
	{
		OdataType = "microsoft.graph.agentProvider",
	},
	Version = "String",
	DocumentationUrl = "String",
	Capabilities = new AgentCapabilities
	{
		OdataType = "microsoft.graph.agentCapabilities",
	},
	SecuritySchemes = new SecuritySchemes
	{
		OdataType = "microsoft.graph.securitySchemes",
	},
	Security = new List<SecurityRequirement>
	{
		new SecurityRequirement
		{
			OdataType = "microsoft.graph.securityRequirement",
		},
	},
	DefaultInputModes = new List<string>
	{
		"String",
	},
	DefaultOutputModes = new List<string>
	{
		"String",
	},
	Skills = new List<AgentSkill>
	{
		new AgentSkill
		{
			OdataType = "microsoft.graph.agentSkill",
		},
	},
	SupportsAuthenticatedExtendedCard = boolean,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentCardManifests["{agentCardManifest-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewAgentCardManifest()
ownerIds := []string {
	"String",
}
requestBody.SetOwnerIds(ownerIds)
managedBy := "String"
requestBody.SetManagedBy(&managedBy) 
originatingStore := "String"
requestBody.SetOriginatingStore(&originatingStore) 
createdBy := "String"
requestBody.SetCreatedBy(&createdBy) 
protocolVersion := "String"
requestBody.SetProtocolVersion(&protocolVersion) 
displayName := "String"
requestBody.SetDisplayName(&displayName) 
description := "String"
requestBody.SetDescription(&description) 
iconUrl := "String"
requestBody.SetIconUrl(&iconUrl) 
provider := graphmodels.NewAgentProvider()
requestBody.SetProvider(provider)
version := "String"
requestBody.SetVersion(&version) 
documentationUrl := "String"
requestBody.SetDocumentationUrl(&documentationUrl) 
capabilities := graphmodels.NewAgentCapabilities()
requestBody.SetCapabilities(capabilities)
securitySchemes := graphmodels.NewSecuritySchemes()
requestBody.SetSecuritySchemes(securitySchemes)


securityRequirement := graphmodels.NewSecurityRequirement()

security := []graphmodels.SecurityRequirementable {
	securityRequirement,
}
requestBody.SetSecurity(security)
defaultInputModes := []string {
	"String",
}
requestBody.SetDefaultInputModes(defaultInputModes)
defaultOutputModes := []string {
	"String",
}
requestBody.SetDefaultOutputModes(defaultOutputModes)


agentSkill := graphmodels.NewAgentSkill()

skills := []graphmodels.AgentSkillable {
	agentSkill,
}
requestBody.SetSkills(skills)
supportsAuthenticatedExtendedCard := boolean
requestBody.SetSupportsAuthenticatedExtendedCard(&supportsAuthenticatedExtendedCard) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentCardManifests, err := graphClient.AgentRegistry().AgentCardManifests().ByAgentCardManifestId("agentCardManifest-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentCardManifest agentCardManifest = new AgentCardManifest();
agentCardManifest.setOdataType("#microsoft.graph.agentCardManifest");
LinkedList<String> ownerIds = new LinkedList<String>();
ownerIds.add("String");
agentCardManifest.setOwnerIds(ownerIds);
agentCardManifest.setManagedBy("String");
agentCardManifest.setOriginatingStore("String");
agentCardManifest.setCreatedBy("String");
agentCardManifest.setProtocolVersion("String");
agentCardManifest.setDisplayName("String");
agentCardManifest.setDescription("String");
agentCardManifest.setIconUrl("String");
AgentProvider provider = new AgentProvider();
provider.setOdataType("microsoft.graph.agentProvider");
agentCardManifest.setProvider(provider);
agentCardManifest.setVersion("String");
agentCardManifest.setDocumentationUrl("String");
AgentCapabilities capabilities = new AgentCapabilities();
capabilities.setOdataType("microsoft.graph.agentCapabilities");
agentCardManifest.setCapabilities(capabilities);
SecuritySchemes securitySchemes = new SecuritySchemes();
securitySchemes.setOdataType("microsoft.graph.securitySchemes");
agentCardManifest.setSecuritySchemes(securitySchemes);
LinkedList<SecurityRequirement> security = new LinkedList<SecurityRequirement>();
SecurityRequirement securityRequirement = new SecurityRequirement();
securityRequirement.setOdataType("microsoft.graph.securityRequirement");
security.add(securityRequirement);
agentCardManifest.setSecurity(security);
LinkedList<String> defaultInputModes = new LinkedList<String>();
defaultInputModes.add("String");
agentCardManifest.setDefaultInputModes(defaultInputModes);
LinkedList<String> defaultOutputModes = new LinkedList<String>();
defaultOutputModes.add("String");
agentCardManifest.setDefaultOutputModes(defaultOutputModes);
LinkedList<AgentSkill> skills = new LinkedList<AgentSkill>();
AgentSkill agentSkill = new AgentSkill();
agentSkill.setOdataType("microsoft.graph.agentSkill");
skills.add(agentSkill);
agentCardManifest.setSkills(skills);
agentCardManifest.setSupportsAuthenticatedExtendedCard(boolean);
AgentCardManifest result = graphClient.agentRegistry().agentCardManifests().byAgentCardManifestId("{agentCardManifest-id}").patch(agentCardManifest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentCardManifest = {
  '@odata.type': '#microsoft.graph.agentCardManifest',
  ownerIds: [
    'String'
  ],
  managedBy: 'String',
  originatingStore: 'String',
  createdBy: 'String',
  protocolVersion: 'String',
  displayName: 'String',
  description: 'String',
  iconUrl: 'String',
  provider: {
    '@odata.type': 'microsoft.graph.agentProvider'
  },
  version: 'String',
  documentationUrl: 'String',
  capabilities: {
    '@odata.type': 'microsoft.graph.agentCapabilities'
  },
  securitySchemes: {
    '@odata.type': 'microsoft.graph.securitySchemes'
  },
  security: [
    {
      '@odata.type': 'microsoft.graph.securityRequirement'
    }
  ],
  defaultInputModes: [
    'String'
  ],
  defaultOutputModes: [
    'String'
  ],
  skills: [
    {
      '@odata.type': 'microsoft.graph.agentSkill'
    }
  ],
  supportsAuthenticatedExtendedCard: 'Boolean'
};

await client.api('/agentRegistry/agentCardManifests/{agentCardManifestId}')
	.version('beta')
	.update(agentCardManifest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentCardManifest;
use Microsoft\Graph\Beta\Generated\Models\AgentProvider;
use Microsoft\Graph\Beta\Generated\Models\AgentCapabilities;
use Microsoft\Graph\Beta\Generated\Models\SecuritySchemes;
use Microsoft\Graph\Beta\Generated\Models\SecurityRequirement;
use Microsoft\Graph\Beta\Generated\Models\AgentSkill;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentCardManifest();
$requestBody->setOdataType('#microsoft.graph.agentCardManifest');
$requestBody->setOwnerIds(['String', 	]);
$requestBody->setManagedBy('String');
$requestBody->setOriginatingStore('String');
$requestBody->setCreatedBy('String');
$requestBody->setProtocolVersion('String');
$requestBody->setDisplayName('String');
$requestBody->setDescription('String');
$requestBody->setIconUrl('String');
$provider = new AgentProvider();
$provider->setOdataType('microsoft.graph.agentProvider');
$requestBody->setProvider($provider);
$requestBody->setVersion('String');
$requestBody->setDocumentationUrl('String');
$capabilities = new AgentCapabilities();
$capabilities->setOdataType('microsoft.graph.agentCapabilities');
$requestBody->setCapabilities($capabilities);
$securitySchemes = new SecuritySchemes();
$securitySchemes->setOdataType('microsoft.graph.securitySchemes');
$requestBody->setSecuritySchemes($securitySchemes);
$securitySecurityRequirement1 = new SecurityRequirement();
$securitySecurityRequirement1->setOdataType('microsoft.graph.securityRequirement');
$securityArray []= $securitySecurityRequirement1;
$requestBody->setSecurity($securityArray);

$requestBody->setDefaultInputModes(['String', ]);
$requestBody->setDefaultOutputModes(['String', ]);
$skillsAgentSkill1 = new AgentSkill();
$skillsAgentSkill1->setOdataType('microsoft.graph.agentSkill');
$skillsArray []= $skillsAgentSkill1;
$requestBody->setSkills($skillsArray);

$requestBody->setSupportsAuthenticatedExtendedCard(boolean);

$result = $graphServiceClient->agentRegistry()->agentCardManifests()->byAgentCardManifestId('agentCardManifest-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_card_manifest import AgentCardManifest
from msgraph_beta.generated.models.agent_provider import AgentProvider
from msgraph_beta.generated.models.agent_capabilities import AgentCapabilities
from msgraph_beta.generated.models.security_schemes import SecuritySchemes
from msgraph_beta.generated.models.security_requirement import SecurityRequirement
from msgraph_beta.generated.models.agent_skill import AgentSkill
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentCardManifest(
	odata_type = "#microsoft.graph.agentCardManifest",
	owner_ids = [
		"String",
	],
	managed_by = "String",
	originating_store = "String",
	created_by = "String",
	protocol_version = "String",
	display_name = "String",
	description = "String",
	icon_url = "String",
	provider = AgentProvider(
		odata_type = "microsoft.graph.agentProvider",
	),
	version = "String",
	documentation_url = "String",
	capabilities = AgentCapabilities(
		odata_type = "microsoft.graph.agentCapabilities",
	),
	security_schemes = SecuritySchemes(
		odata_type = "microsoft.graph.securitySchemes",
	),
	security = [
		SecurityRequirement(
			odata_type = "microsoft.graph.securityRequirement",
		),
	],
	default_input_modes = [
		"String",
	],
	default_output_modes = [
		"String",
	],
	skills = [
		AgentSkill(
			odata_type = "microsoft.graph.agentSkill",
		),
	],
	supports_authenticated_extended_card = Boolean,
)

result = await graph_client.agent_registry.agent_card_manifests.by_agent_card_manifest_id('agentCardManifest-id').patch(request_body)
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
  "@odata.type": "#microsoft.graph.agentCardManifest",
  "id": "5d1d9ba4-36ed-2e0c-c182-9da69c5e398d",
  "ownerIds": [
    "String"
  ],
  "managedBy": "String",
  "originatingStore": "String",
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "protocolVersion": "String",
  "displayName": "String",
  "description": "String",
  "iconUrl": "String",
  "provider": {
    "@odata.type": "microsoft.graph.agentProvider"
  },
  "version": "String",
  "documentationUrl": "String",
  "capabilities": {
    "@odata.type": "microsoft.graph.agentCapabilities"
  },
  "securitySchemes": {
    "@odata.type": "microsoft.graph.securitySchemes"
  },
  "security": [
    {
      "@odata.type": "microsoft.graph.securityRequirement"
    }
  ],
  "defaultInputModes": [
    "String"
  ],
  "defaultOutputModes": [
    "String"
  ],
  "skills": [
    {
      "@odata.type": "microsoft.graph.agentSkill"
    }
  ],
  "supportsAuthenticatedExtendedCard": "Boolean"
}
```
