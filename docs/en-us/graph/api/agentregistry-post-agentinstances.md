<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentregistry-post-agentinstances?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Create agentInstance

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Create a new [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object.

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
POST /agentRegistry/agentInstances
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object.

You can specify the following properties when creating an **agentInstance**.

| Property | Type | Description |
| :--- | :--- | :--- |
| ownerIds | String collection | List of owner identifiers for the agent instance. Required. |
| managedBy | String | Application identifier managing this agent. Optional. |
| originatingStore | String | Name of the store/system where agent originated. Optional. |
| displayName | String | Display name for the agent instance. Required. |
| sourceAgentId | String | Original agent identifier from source system. Optional. |
| agentIdentityBlueprintId | String | Agent identity blueprint identifier. Optional. |
| agentIdentityId | String | Entra agent identity identifier. Optional. |
| agentUserId | String | User identifier associated with the agent. Optional. |
| url | String | Endpoint URL for the agent instance. Optional. |
| preferredTransport | String | Preferred transport protocol \(JSONRPC, GRPC, HTTP+JSON\). Optional. |
| additionalInterfaces | [agentInterface](https://learn.microsoft.com/en-us/graph/api/resources/agentinterface?view=graph-rest-beta) collection | Additional interfaces/transports supported by the agent \(url, transport\). Optional. |
| signatures | [agentCardSignature](https://learn.microsoft.com/en-us/graph/api/resources/agentcardsignature?view=graph-rest-beta) collection | Digital signatures for the agent instance \(protected, signature, header\). Optional. |

## Response

If successful, this method returns a `201 Created` response code and an [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create an agentInstance with a new agentCardManifest

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/agentRegistry/agentInstances
Content-Type: application/json

{
  "id": "Security Copilot Platform Agent: 00222",
  "ownerIds": [
    "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
    "b9108c41-d2d2-4e78-b073-92f57b752bd0"
  ],
  "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
  "originatingStore": "Microsoft Security Copilot",
  "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
  "displayName": "Conditional Access Agent",
  "sourceAgentId": "00222",
  "agentIdentityBlueprintId": "d0108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentIdentityId": "dd108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentUserId": "ee108c41-d2d2-4e78-b073-92f57b752bd0",
  "createdDateTime": "2025-01-01T00:00:00.1234567Z",
  "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
  "url": "https://conditional-access-agent.example.com/a2a/v1",
  "preferredTransport": "JSONRPC",
  "additionalInterfaces": [
    {
      "url": "https://conditional-access-agent.example.com/a2a/v1",
      "transport": "JSONRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/grpc",
      "transport": "GRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/json",
      "transport": "HTTP+JSON"
    }
  ],
  "signatures": [
    {
      "protected": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
      "signature": "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
      "header": {
        "kidHint": "contoso-key-1",
        "nonce": "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
      }
    }
  ],
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
	Id = "Security Copilot Platform Agent: 00222",
	OwnerIds = new List<string>
	{
		"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
		"b9108c41-d2d2-4e78-b073-92f57b752bd0",
	},
	ManagedBy = "719cc904-9700-4e08-9941-fd826cc84c60",
	OriginatingStore = "Microsoft Security Copilot",
	CreatedBy = "d47bffae-411a-4de9-8548-05e79bc01f0d",
	DisplayName = "Conditional Access Agent",
	SourceAgentId = "00222",
	AgentIdentityBlueprintId = "d0108c41-d2d2-4e78-b073-92f57b752bd0",
	AgentIdentityId = "dd108c41-d2d2-4e78-b073-92f57b752bd0",
	AgentUserId = "ee108c41-d2d2-4e78-b073-92f57b752bd0",
	CreatedDateTime = DateTimeOffset.Parse("2025-01-01T00:00:00.1234567Z"),
	LastModifiedDateTime = DateTimeOffset.Parse("2025-01-01T00:00:00.1234567Z"),
	Url = "https://conditional-access-agent.example.com/a2a/v1",
	PreferredTransport = "JSONRPC",
	AdditionalInterfaces = new List<AgentInterface>
	{
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/v1",
			Transport = "JSONRPC",
		},
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/grpc",
			Transport = "GRPC",
		},
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/json",
			Transport = "HTTP+JSON",
		},
	},
	Signatures = new List<AgentCardSignature>
	{
		new AgentCardSignature
		{
			Protected = "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
			Signature = "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
			Header = new JwsHeader
			{
				AdditionalData = new Dictionary<string, object>
				{
					{
						"kidHint" , "contoso-key-1"
					},
					{
						"nonce" , "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
					},
				},
			},
		},
	},
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
var result = await graphClient.AgentRegistry.AgentInstances.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAgentInstance()
id := "Security Copilot Platform Agent: 00222"
requestBody.SetId(&id) 
ownerIds := []string {
	"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
	"b9108c41-d2d2-4e78-b073-92f57b752bd0",
}
requestBody.SetOwnerIds(ownerIds)
managedBy := "719cc904-9700-4e08-9941-fd826cc84c60"
requestBody.SetManagedBy(&managedBy) 
originatingStore := "Microsoft Security Copilot"
requestBody.SetOriginatingStore(&originatingStore) 
createdBy := "d47bffae-411a-4de9-8548-05e79bc01f0d"
requestBody.SetCreatedBy(&createdBy) 
displayName := "Conditional Access Agent"
requestBody.SetDisplayName(&displayName) 
sourceAgentId := "00222"
requestBody.SetSourceAgentId(&sourceAgentId) 
agentIdentityBlueprintId := "d0108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentIdentityBlueprintId(&agentIdentityBlueprintId) 
agentIdentityId := "dd108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentIdentityId(&agentIdentityId) 
agentUserId := "ee108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentUserId(&agentUserId) 
createdDateTime , err := time.Parse(time.RFC3339, "2025-01-01T00:00:00.1234567Z")
requestBody.SetCreatedDateTime(&createdDateTime) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "2025-01-01T00:00:00.1234567Z")
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
url := "https://conditional-access-agent.example.com/a2a/v1"
requestBody.SetUrl(&url) 
preferredTransport := "JSONRPC"
requestBody.SetPreferredTransport(&preferredTransport) 


agentInterface := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/v1"
agentInterface.SetUrl(&url) 
transport := "JSONRPC"
agentInterface.SetTransport(&transport) 
agentInterface1 := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/grpc"
agentInterface1.SetUrl(&url) 
transport := "GRPC"
agentInterface1.SetTransport(&transport) 
agentInterface2 := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/json"
agentInterface2.SetUrl(&url) 
transport := "HTTP+JSON"
agentInterface2.SetTransport(&transport) 

additionalInterfaces := []graphmodels.AgentInterfaceable {
	agentInterface,
	agentInterface1,
	agentInterface2,
}
requestBody.SetAdditionalInterfaces(additionalInterfaces)


agentCardSignature := graphmodels.NewAgentCardSignature()
protected := "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9"
agentCardSignature.SetProtected(&protected) 
signature := "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w"
agentCardSignature.SetSignature(&signature) 
header := graphmodels.NewJwsHeader()
additionalData := map[string]interface{}{
	"kidHint" : "contoso-key-1", 
	"nonce" : "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0", 
}
header.SetAdditionalData(additionalData)
agentCardSignature.SetHeader(header)

signatures := []graphmodels.AgentCardSignatureable {
	agentCardSignature,
}
requestBody.SetSignatures(signatures)
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
agentInstances, err := graphClient.AgentRegistry().AgentInstances().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentInstance agentInstance = new AgentInstance();
agentInstance.setId("Security Copilot Platform Agent: 00222");
LinkedList<String> ownerIds = new LinkedList<String>();
ownerIds.add("daf58b0e-44e1-433c-b6b0-ca70cae320b8");
ownerIds.add("b9108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setOwnerIds(ownerIds);
agentInstance.setManagedBy("719cc904-9700-4e08-9941-fd826cc84c60");
agentInstance.setOriginatingStore("Microsoft Security Copilot");
agentInstance.setCreatedBy("d47bffae-411a-4de9-8548-05e79bc01f0d");
agentInstance.setDisplayName("Conditional Access Agent");
agentInstance.setSourceAgentId("00222");
agentInstance.setAgentIdentityBlueprintId("d0108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setAgentIdentityId("dd108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setAgentUserId("ee108c41-d2d2-4e78-b073-92f57b752bd0");
OffsetDateTime createdDateTime = OffsetDateTime.parse("2025-01-01T00:00:00.1234567Z");
agentInstance.setCreatedDateTime(createdDateTime);
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("2025-01-01T00:00:00.1234567Z");
agentInstance.setLastModifiedDateTime(lastModifiedDateTime);
agentInstance.setUrl("https://conditional-access-agent.example.com/a2a/v1");
agentInstance.setPreferredTransport("JSONRPC");
LinkedList<AgentInterface> additionalInterfaces = new LinkedList<AgentInterface>();
AgentInterface agentInterface = new AgentInterface();
agentInterface.setUrl("https://conditional-access-agent.example.com/a2a/v1");
agentInterface.setTransport("JSONRPC");
additionalInterfaces.add(agentInterface);
AgentInterface agentInterface1 = new AgentInterface();
agentInterface1.setUrl("https://conditional-access-agent.example.com/a2a/grpc");
agentInterface1.setTransport("GRPC");
additionalInterfaces.add(agentInterface1);
AgentInterface agentInterface2 = new AgentInterface();
agentInterface2.setUrl("https://conditional-access-agent.example.com/a2a/json");
agentInterface2.setTransport("HTTP+JSON");
additionalInterfaces.add(agentInterface2);
agentInstance.setAdditionalInterfaces(additionalInterfaces);
LinkedList<AgentCardSignature> signatures = new LinkedList<AgentCardSignature>();
AgentCardSignature agentCardSignature = new AgentCardSignature();
agentCardSignature.setProtectedEscaped("eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9");
agentCardSignature.setSignature("xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w");
JwsHeader header = new JwsHeader();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("kidHint", "contoso-key-1");
additionalData.put("nonce", "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0");
header.setAdditionalData(additionalData);
agentCardSignature.setHeader(header);
signatures.add(agentCardSignature);
agentInstance.setSignatures(signatures);
AgentCardManifest agentCardManifest = new AgentCardManifest();
LinkedList<String> ownerIds1 = new LinkedList<String>();
ownerIds1.add("0ef68a76-e247-41dd-947b-41282760a2ac");
agentCardManifest.setOwnerIds(ownerIds1);
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
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("useHttps", true);
params.setAdditionalData(additionalData1);
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
AgentInstance result = graphClient.agentRegistry().agentInstances().post(agentInstance);
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
  id: 'Security Copilot Platform Agent: 00222',
  ownerIds: [
    'daf58b0e-44e1-433c-b6b0-ca70cae320b8',
    'b9108c41-d2d2-4e78-b073-92f57b752bd0'
  ],
  managedBy: '719cc904-9700-4e08-9941-fd826cc84c60',
  originatingStore: 'Microsoft Security Copilot',
  createdBy: 'd47bffae-411a-4de9-8548-05e79bc01f0d',
  displayName: 'Conditional Access Agent',
  sourceAgentId: '00222',
  agentIdentityBlueprintId: 'd0108c41-d2d2-4e78-b073-92f57b752bd0',
  agentIdentityId: 'dd108c41-d2d2-4e78-b073-92f57b752bd0',
  agentUserId: 'ee108c41-d2d2-4e78-b073-92f57b752bd0',
  createdDateTime: '2025-01-01T00:00:00.1234567Z',
  lastModifiedDateTime: '2025-01-01T00:00:00.1234567Z',
  url: 'https://conditional-access-agent.example.com/a2a/v1',
  preferredTransport: 'JSONRPC',
  additionalInterfaces: [
    {
      url: 'https://conditional-access-agent.example.com/a2a/v1',
      transport: 'JSONRPC'
    },
    {
      url: 'https://conditional-access-agent.example.com/a2a/grpc',
      transport: 'GRPC'
    },
    {
      url: 'https://conditional-access-agent.example.com/a2a/json',
      transport: 'HTTP+JSON'
    }
  ],
  signatures: [
    {
      protected: 'eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9',
      signature: 'xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w',
      header: {
        kidHint: 'contoso-key-1',
        nonce: 'f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0'
      }
    }
  ],
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

await client.api('/agentRegistry/agentInstances')
	.version('beta')
	.post(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentInstance;
use Microsoft\Graph\Beta\Generated\Models\AgentInterface;
use Microsoft\Graph\Beta\Generated\Models\AgentCardSignature;
use Microsoft\Graph\Beta\Generated\Models\JwsHeader;
use Microsoft\Graph\Beta\Generated\Models\AgentCardManifest;
use Microsoft\Graph\Beta\Generated\Models\AgentProvider;
use Microsoft\Graph\Beta\Generated\Models\AgentCapabilities;
use Microsoft\Graph\Beta\Generated\Models\AgentExtension;
use Microsoft\Graph\Beta\Generated\Models\AgentExtensionParams;
use Microsoft\Graph\Beta\Generated\Models\AgentSkill;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentInstance();
$requestBody->setId('Security Copilot Platform Agent: 00222');
$requestBody->setOwnerIds(['daf58b0e-44e1-433c-b6b0-ca70cae320b8', 'b9108c41-d2d2-4e78-b073-92f57b752bd0', 	]);
$requestBody->setManagedBy('719cc904-9700-4e08-9941-fd826cc84c60');
$requestBody->setOriginatingStore('Microsoft Security Copilot');
$requestBody->setCreatedBy('d47bffae-411a-4de9-8548-05e79bc01f0d');
$requestBody->setDisplayName('Conditional Access Agent');
$requestBody->setSourceAgentId('00222');
$requestBody->setAgentIdentityBlueprintId('d0108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setAgentIdentityId('dd108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setAgentUserId('ee108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setCreatedDateTime(new \DateTime('2025-01-01T00:00:00.1234567Z'));
$requestBody->setLastModifiedDateTime(new \DateTime('2025-01-01T00:00:00.1234567Z'));
$requestBody->setUrl('https://conditional-access-agent.example.com/a2a/v1');
$requestBody->setPreferredTransport('JSONRPC');
$additionalInterfacesAgentInterface1 = new AgentInterface();
$additionalInterfacesAgentInterface1->setUrl('https://conditional-access-agent.example.com/a2a/v1');
$additionalInterfacesAgentInterface1->setTransport('JSONRPC');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface1;
$additionalInterfacesAgentInterface2 = new AgentInterface();
$additionalInterfacesAgentInterface2->setUrl('https://conditional-access-agent.example.com/a2a/grpc');
$additionalInterfacesAgentInterface2->setTransport('GRPC');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface2;
$additionalInterfacesAgentInterface3 = new AgentInterface();
$additionalInterfacesAgentInterface3->setUrl('https://conditional-access-agent.example.com/a2a/json');
$additionalInterfacesAgentInterface3->setTransport('HTTP+JSON');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface3;
$requestBody->setAdditionalInterfaces($additionalInterfacesArray);

$signaturesAgentCardSignature1 = new AgentCardSignature();
$signaturesAgentCardSignature1->setEscapedProtected('eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9');
$signaturesAgentCardSignature1->setSignature('xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w');
$signaturesAgentCardSignature1Header = new JwsHeader();
$additionalData = [
'kidHint' => 'contoso-key-1',
'nonce' => 'f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0',
];
$signaturesAgentCardSignature1Header->setAdditionalData($additionalData);
$signaturesAgentCardSignature1->setHeader($signaturesAgentCardSignature1Header);
$signaturesArray []= $signaturesAgentCardSignature1;
$requestBody->setSignatures($signaturesArray);

$agentCardManifest = new AgentCardManifest();
$agentCardManifest->setOwnerIds(['0ef68a76-e247-41dd-947b-41282760a2ac', ]);
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

$result = $graphServiceClient->agentRegistry()->agentInstances()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_instance import AgentInstance
from msgraph_beta.generated.models.agent_interface import AgentInterface
from msgraph_beta.generated.models.agent_card_signature import AgentCardSignature
from msgraph_beta.generated.models.jws_header import JwsHeader
from msgraph_beta.generated.models.agent_card_manifest import AgentCardManifest
from msgraph_beta.generated.models.agent_provider import AgentProvider
from msgraph_beta.generated.models.agent_capabilities import AgentCapabilities
from msgraph_beta.generated.models.agent_extension import AgentExtension
from msgraph_beta.generated.models.agent_extension_params import AgentExtensionParams
from msgraph_beta.generated.models.agent_skill import AgentSkill
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentInstance(
	id = "Security Copilot Platform Agent: 00222",
	owner_ids = [
		"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
		"b9108c41-d2d2-4e78-b073-92f57b752bd0",
	],
	managed_by = "719cc904-9700-4e08-9941-fd826cc84c60",
	originating_store = "Microsoft Security Copilot",
	created_by = "d47bffae-411a-4de9-8548-05e79bc01f0d",
	display_name = "Conditional Access Agent",
	source_agent_id = "00222",
	agent_identity_blueprint_id = "d0108c41-d2d2-4e78-b073-92f57b752bd0",
	agent_identity_id = "dd108c41-d2d2-4e78-b073-92f57b752bd0",
	agent_user_id = "ee108c41-d2d2-4e78-b073-92f57b752bd0",
	created_date_time = "2025-01-01T00:00:00.1234567Z",
	last_modified_date_time = "2025-01-01T00:00:00.1234567Z",
	url = "https://conditional-access-agent.example.com/a2a/v1",
	preferred_transport = "JSONRPC",
	additional_interfaces = [
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/v1",
			transport = "JSONRPC",
		),
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/grpc",
			transport = "GRPC",
		),
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/json",
			transport = "HTTP+JSON",
		),
	],
	signatures = [
		AgentCardSignature(
			protected = "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
			signature = "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
			header = JwsHeader(
				additional_data = {
						"kid_hint" : "contoso-key-1",
						"nonce" : "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0",
				}
			),
		),
	],
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

result = await graph_client.agent_registry.agent_instances.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "Security Copilot Platform Agent: 00222",
  "ownerIds": [
    "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
    "b9108c41-d2d2-4e78-b073-92f57b752bd0"
  ],
  "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
  "originatingStore": "Microsoft Security Copilot",
  "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
  "displayName": "Conditional Access Agent",
  "sourceAgentId": "00222",
  "agentIdentityBlueprintId": "d0108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentIdentityId": "dd108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentUserId": "ee108c41-d2d2-4e78-b073-92f57b752bd0",
  "createdDateTime": "2025-01-01T00:00:00.1234567Z",
  "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
  "url": "https://conditional-access-agent.example.com/a2a/v1",
  "preferredTransport": "JSONRPC",
  "additionalInterfaces": [
    {
      "url": "https://conditional-access-agent.example.com/a2a/v1",
      "transport": "JSONRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/grpc",
      "transport": "GRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/json",
      "transport": "HTTP+JSON"
    }
  ],
  "signatures": [
    {
      "protected": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
      "signature": "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
      "header": {
        "kidHint": "contoso-key-1",
        "nonce": "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
      }
    }
  ]
}
```

### Example 2: Create an agentInstance and reference an existing agentCardManifest

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
POST https://graph.microsoft.com/beta/agentRegistry/agentInstances
Content-Type: application/json

{
  "id": "Security Copilot Platform Agent: 00222",
  "ownerIds": [
    "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
    "b9108c41-d2d2-4e78-b073-92f57b752bd0"
  ],
  "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
  "originatingStore": "Microsoft Security Copilot",
  "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
  "displayName": "Conditional Access Agent",
  "sourceAgentId": "00222",
  "agentIdentityBlueprintId": "d0108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentIdentityId": "dd108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentUserId": "ee108c41-d2d2-4e78-b073-92f57b752bd0",
  "createdDateTime": "2025-01-01T00:00:00.1234567Z",
  "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
  "url": "https://conditional-access-agent.example.com/a2a/v1",
  "preferredTransport": "JSONRPC",
  "additionalInterfaces": [
    {
      "url": "https://conditional-access-agent.example.com/a2a/v1",
      "transport": "JSONRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/grpc",
      "transport": "GRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/json",
      "transport": "HTTP+JSON"
    }
  ],
  "signatures": [
    {
      "protected": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
      "signature": "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
      "header": {
        "kidHint": "contoso-key-1",
        "nonce": "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
      }
    }
  ],
  "agentCardManifest@odata.bind": "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AgentInstance
{
	Id = "Security Copilot Platform Agent: 00222",
	OwnerIds = new List<string>
	{
		"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
		"b9108c41-d2d2-4e78-b073-92f57b752bd0",
	},
	ManagedBy = "719cc904-9700-4e08-9941-fd826cc84c60",
	OriginatingStore = "Microsoft Security Copilot",
	CreatedBy = "d47bffae-411a-4de9-8548-05e79bc01f0d",
	DisplayName = "Conditional Access Agent",
	SourceAgentId = "00222",
	AgentIdentityBlueprintId = "d0108c41-d2d2-4e78-b073-92f57b752bd0",
	AgentIdentityId = "dd108c41-d2d2-4e78-b073-92f57b752bd0",
	AgentUserId = "ee108c41-d2d2-4e78-b073-92f57b752bd0",
	CreatedDateTime = DateTimeOffset.Parse("2025-01-01T00:00:00.1234567Z"),
	LastModifiedDateTime = DateTimeOffset.Parse("2025-01-01T00:00:00.1234567Z"),
	Url = "https://conditional-access-agent.example.com/a2a/v1",
	PreferredTransport = "JSONRPC",
	AdditionalInterfaces = new List<AgentInterface>
	{
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/v1",
			Transport = "JSONRPC",
		},
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/grpc",
			Transport = "GRPC",
		},
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/json",
			Transport = "HTTP+JSON",
		},
	},
	Signatures = new List<AgentCardSignature>
	{
		new AgentCardSignature
		{
			Protected = "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
			Signature = "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
			Header = new JwsHeader
			{
				AdditionalData = new Dictionary<string, object>
				{
					{
						"kidHint" , "contoso-key-1"
					},
					{
						"nonce" , "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
					},
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"agentCardManifest@odata.bind" , "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentInstances.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAgentInstance()
id := "Security Copilot Platform Agent: 00222"
requestBody.SetId(&id) 
ownerIds := []string {
	"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
	"b9108c41-d2d2-4e78-b073-92f57b752bd0",
}
requestBody.SetOwnerIds(ownerIds)
managedBy := "719cc904-9700-4e08-9941-fd826cc84c60"
requestBody.SetManagedBy(&managedBy) 
originatingStore := "Microsoft Security Copilot"
requestBody.SetOriginatingStore(&originatingStore) 
createdBy := "d47bffae-411a-4de9-8548-05e79bc01f0d"
requestBody.SetCreatedBy(&createdBy) 
displayName := "Conditional Access Agent"
requestBody.SetDisplayName(&displayName) 
sourceAgentId := "00222"
requestBody.SetSourceAgentId(&sourceAgentId) 
agentIdentityBlueprintId := "d0108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentIdentityBlueprintId(&agentIdentityBlueprintId) 
agentIdentityId := "dd108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentIdentityId(&agentIdentityId) 
agentUserId := "ee108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentUserId(&agentUserId) 
createdDateTime , err := time.Parse(time.RFC3339, "2025-01-01T00:00:00.1234567Z")
requestBody.SetCreatedDateTime(&createdDateTime) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "2025-01-01T00:00:00.1234567Z")
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
url := "https://conditional-access-agent.example.com/a2a/v1"
requestBody.SetUrl(&url) 
preferredTransport := "JSONRPC"
requestBody.SetPreferredTransport(&preferredTransport) 


agentInterface := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/v1"
agentInterface.SetUrl(&url) 
transport := "JSONRPC"
agentInterface.SetTransport(&transport) 
agentInterface1 := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/grpc"
agentInterface1.SetUrl(&url) 
transport := "GRPC"
agentInterface1.SetTransport(&transport) 
agentInterface2 := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/json"
agentInterface2.SetUrl(&url) 
transport := "HTTP+JSON"
agentInterface2.SetTransport(&transport) 

additionalInterfaces := []graphmodels.AgentInterfaceable {
	agentInterface,
	agentInterface1,
	agentInterface2,
}
requestBody.SetAdditionalInterfaces(additionalInterfaces)


agentCardSignature := graphmodels.NewAgentCardSignature()
protected := "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9"
agentCardSignature.SetProtected(&protected) 
signature := "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w"
agentCardSignature.SetSignature(&signature) 
header := graphmodels.NewJwsHeader()
additionalData := map[string]interface{}{
	"kidHint" : "contoso-key-1", 
	"nonce" : "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0", 
}
header.SetAdditionalData(additionalData)
agentCardSignature.SetHeader(header)

signatures := []graphmodels.AgentCardSignatureable {
	agentCardSignature,
}
requestBody.SetSignatures(signatures)
additionalData := map[string]interface{}{
	"agentCardManifest@odata.bind" : "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentInstances, err := graphClient.AgentRegistry().AgentInstances().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentInstance agentInstance = new AgentInstance();
agentInstance.setId("Security Copilot Platform Agent: 00222");
LinkedList<String> ownerIds = new LinkedList<String>();
ownerIds.add("daf58b0e-44e1-433c-b6b0-ca70cae320b8");
ownerIds.add("b9108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setOwnerIds(ownerIds);
agentInstance.setManagedBy("719cc904-9700-4e08-9941-fd826cc84c60");
agentInstance.setOriginatingStore("Microsoft Security Copilot");
agentInstance.setCreatedBy("d47bffae-411a-4de9-8548-05e79bc01f0d");
agentInstance.setDisplayName("Conditional Access Agent");
agentInstance.setSourceAgentId("00222");
agentInstance.setAgentIdentityBlueprintId("d0108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setAgentIdentityId("dd108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setAgentUserId("ee108c41-d2d2-4e78-b073-92f57b752bd0");
OffsetDateTime createdDateTime = OffsetDateTime.parse("2025-01-01T00:00:00.1234567Z");
agentInstance.setCreatedDateTime(createdDateTime);
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("2025-01-01T00:00:00.1234567Z");
agentInstance.setLastModifiedDateTime(lastModifiedDateTime);
agentInstance.setUrl("https://conditional-access-agent.example.com/a2a/v1");
agentInstance.setPreferredTransport("JSONRPC");
LinkedList<AgentInterface> additionalInterfaces = new LinkedList<AgentInterface>();
AgentInterface agentInterface = new AgentInterface();
agentInterface.setUrl("https://conditional-access-agent.example.com/a2a/v1");
agentInterface.setTransport("JSONRPC");
additionalInterfaces.add(agentInterface);
AgentInterface agentInterface1 = new AgentInterface();
agentInterface1.setUrl("https://conditional-access-agent.example.com/a2a/grpc");
agentInterface1.setTransport("GRPC");
additionalInterfaces.add(agentInterface1);
AgentInterface agentInterface2 = new AgentInterface();
agentInterface2.setUrl("https://conditional-access-agent.example.com/a2a/json");
agentInterface2.setTransport("HTTP+JSON");
additionalInterfaces.add(agentInterface2);
agentInstance.setAdditionalInterfaces(additionalInterfaces);
LinkedList<AgentCardSignature> signatures = new LinkedList<AgentCardSignature>();
AgentCardSignature agentCardSignature = new AgentCardSignature();
agentCardSignature.setProtectedEscaped("eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9");
agentCardSignature.setSignature("xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w");
JwsHeader header = new JwsHeader();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("kidHint", "contoso-key-1");
additionalData.put("nonce", "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0");
header.setAdditionalData(additionalData);
agentCardSignature.setHeader(header);
signatures.add(agentCardSignature);
agentInstance.setSignatures(signatures);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("agentCardManifest@odata.bind", "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')");
agentInstance.setAdditionalData(additionalData1);
AgentInstance result = graphClient.agentRegistry().agentInstances().post(agentInstance);
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
  id: 'Security Copilot Platform Agent: 00222',
  ownerIds: [
    'daf58b0e-44e1-433c-b6b0-ca70cae320b8',
    'b9108c41-d2d2-4e78-b073-92f57b752bd0'
  ],
  managedBy: '719cc904-9700-4e08-9941-fd826cc84c60',
  originatingStore: 'Microsoft Security Copilot',
  createdBy: 'd47bffae-411a-4de9-8548-05e79bc01f0d',
  displayName: 'Conditional Access Agent',
  sourceAgentId: '00222',
  agentIdentityBlueprintId: 'd0108c41-d2d2-4e78-b073-92f57b752bd0',
  agentIdentityId: 'dd108c41-d2d2-4e78-b073-92f57b752bd0',
  agentUserId: 'ee108c41-d2d2-4e78-b073-92f57b752bd0',
  createdDateTime: '2025-01-01T00:00:00.1234567Z',
  lastModifiedDateTime: '2025-01-01T00:00:00.1234567Z',
  url: 'https://conditional-access-agent.example.com/a2a/v1',
  preferredTransport: 'JSONRPC',
  additionalInterfaces: [
    {
      url: 'https://conditional-access-agent.example.com/a2a/v1',
      transport: 'JSONRPC'
    },
    {
      url: 'https://conditional-access-agent.example.com/a2a/grpc',
      transport: 'GRPC'
    },
    {
      url: 'https://conditional-access-agent.example.com/a2a/json',
      transport: 'HTTP+JSON'
    }
  ],
  signatures: [
    {
      protected: 'eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9',
      signature: 'xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w',
      header: {
        kidHint: 'contoso-key-1',
        nonce: 'f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0'
      }
    }
  ],
  'agentCardManifest@odata.bind': 'https://graph.microsoft.com/beta/agentRegistry/agentCardManifests(\'employee-assistant\')'
};

await client.api('/agentRegistry/agentInstances')
	.version('beta')
	.post(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentInstance;
use Microsoft\Graph\Beta\Generated\Models\AgentInterface;
use Microsoft\Graph\Beta\Generated\Models\AgentCardSignature;
use Microsoft\Graph\Beta\Generated\Models\JwsHeader;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentInstance();
$requestBody->setId('Security Copilot Platform Agent: 00222');
$requestBody->setOwnerIds(['daf58b0e-44e1-433c-b6b0-ca70cae320b8', 'b9108c41-d2d2-4e78-b073-92f57b752bd0', 	]);
$requestBody->setManagedBy('719cc904-9700-4e08-9941-fd826cc84c60');
$requestBody->setOriginatingStore('Microsoft Security Copilot');
$requestBody->setCreatedBy('d47bffae-411a-4de9-8548-05e79bc01f0d');
$requestBody->setDisplayName('Conditional Access Agent');
$requestBody->setSourceAgentId('00222');
$requestBody->setAgentIdentityBlueprintId('d0108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setAgentIdentityId('dd108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setAgentUserId('ee108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setCreatedDateTime(new \DateTime('2025-01-01T00:00:00.1234567Z'));
$requestBody->setLastModifiedDateTime(new \DateTime('2025-01-01T00:00:00.1234567Z'));
$requestBody->setUrl('https://conditional-access-agent.example.com/a2a/v1');
$requestBody->setPreferredTransport('JSONRPC');
$additionalInterfacesAgentInterface1 = new AgentInterface();
$additionalInterfacesAgentInterface1->setUrl('https://conditional-access-agent.example.com/a2a/v1');
$additionalInterfacesAgentInterface1->setTransport('JSONRPC');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface1;
$additionalInterfacesAgentInterface2 = new AgentInterface();
$additionalInterfacesAgentInterface2->setUrl('https://conditional-access-agent.example.com/a2a/grpc');
$additionalInterfacesAgentInterface2->setTransport('GRPC');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface2;
$additionalInterfacesAgentInterface3 = new AgentInterface();
$additionalInterfacesAgentInterface3->setUrl('https://conditional-access-agent.example.com/a2a/json');
$additionalInterfacesAgentInterface3->setTransport('HTTP+JSON');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface3;
$requestBody->setAdditionalInterfaces($additionalInterfacesArray);

$signaturesAgentCardSignature1 = new AgentCardSignature();
$signaturesAgentCardSignature1->setEscapedProtected('eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9');
$signaturesAgentCardSignature1->setSignature('xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w');
$signaturesAgentCardSignature1Header = new JwsHeader();
$additionalData = [
'kidHint' => 'contoso-key-1',
'nonce' => 'f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0',
];
$signaturesAgentCardSignature1Header->setAdditionalData($additionalData);
$signaturesAgentCardSignature1->setHeader($signaturesAgentCardSignature1Header);
$signaturesArray []= $signaturesAgentCardSignature1;
$requestBody->setSignatures($signaturesArray);

$additionalData = [
'agentCardManifest@odata.bind' => 'https://graph.microsoft.com/beta/agentRegistry/agentCardManifests(\'employee-assistant\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->agentRegistry()->agentInstances()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_instance import AgentInstance
from msgraph_beta.generated.models.agent_interface import AgentInterface
from msgraph_beta.generated.models.agent_card_signature import AgentCardSignature
from msgraph_beta.generated.models.jws_header import JwsHeader
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentInstance(
	id = "Security Copilot Platform Agent: 00222",
	owner_ids = [
		"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
		"b9108c41-d2d2-4e78-b073-92f57b752bd0",
	],
	managed_by = "719cc904-9700-4e08-9941-fd826cc84c60",
	originating_store = "Microsoft Security Copilot",
	created_by = "d47bffae-411a-4de9-8548-05e79bc01f0d",
	display_name = "Conditional Access Agent",
	source_agent_id = "00222",
	agent_identity_blueprint_id = "d0108c41-d2d2-4e78-b073-92f57b752bd0",
	agent_identity_id = "dd108c41-d2d2-4e78-b073-92f57b752bd0",
	agent_user_id = "ee108c41-d2d2-4e78-b073-92f57b752bd0",
	created_date_time = "2025-01-01T00:00:00.1234567Z",
	last_modified_date_time = "2025-01-01T00:00:00.1234567Z",
	url = "https://conditional-access-agent.example.com/a2a/v1",
	preferred_transport = "JSONRPC",
	additional_interfaces = [
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/v1",
			transport = "JSONRPC",
		),
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/grpc",
			transport = "GRPC",
		),
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/json",
			transport = "HTTP+JSON",
		),
	],
	signatures = [
		AgentCardSignature(
			protected = "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
			signature = "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
			header = JwsHeader(
				additional_data = {
						"kid_hint" : "contoso-key-1",
						"nonce" : "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0",
				}
			),
		),
	],
	additional_data = {
			"agent_card_manifest@odata_bind" : "https://graph.microsoft.com/beta/agentRegistry/agentCardManifests('employee-assistant')",
	}
)

result = await graph_client.agent_registry.agent_instances.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "Security Copilot Platform Agent: 00222",
  "ownerIds": [
    "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
    "b9108c41-d2d2-4e78-b073-92f57b752bd0"
  ],
  "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
  "originatingStore": "Microsoft Security Copilot",
  "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
  "displayName": "Conditional Access Agent",
  "sourceAgentId": "00222",
  "agentIdentityBlueprintId": "d0108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentIdentityId": "dd108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentUserId": "ee108c41-d2d2-4e78-b073-92f57b752bd0",
  "createdDateTime": "2025-01-01T00:00:00.1234567Z",
  "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
  "url": "https://conditional-access-agent.example.com/a2a/v1",
  "preferredTransport": "JSONRPC",
  "additionalInterfaces": [
    {
      "url": "https://conditional-access-agent.example.com/a2a/v1",
      "transport": "JSONRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/grpc",
      "transport": "GRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/json",
      "transport": "HTTP+JSON"
    }
  ],
  "signatures": [
    {
      "protected": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
      "signature": "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
      "header": {
        "kidHint": "contoso-key-1",
        "nonce": "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
      }
    }
  ]
}
```

### Example 3: Create an agentInstance without the agentCardManifest

#### Request

The following example shows a request. To add an agentCardManifest later, use the [Update agentInstance API](https://learn.microsoft.com/en-us/graph/api/agentinstance-update?view=graph-rest-beta).

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/agentRegistry/agentInstances
Content-Type: application/json

{
  "id": "Security Copilot Platform Agent: 00222",
  "ownerIds": [
    "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
    "b9108c41-d2d2-4e78-b073-92f57b752bd0"
  ],
  "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
  "originatingStore": "Microsoft Security Copilot",
  "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
  "displayName": "Conditional Access Agent",
  "sourceAgentId": "00222",
  "agentIdentityBlueprintId": "d0108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentIdentityId": "dd108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentUserId": "ee108c41-d2d2-4e78-b073-92f57b752bd0",
  "createdDateTime": "2025-01-01T00:00:00.1234567Z",
  "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
  "url": "https://conditional-access-agent.example.com/a2a/v1",
  "preferredTransport": "JSONRPC",
  "additionalInterfaces": [
    {
      "url": "https://conditional-access-agent.example.com/a2a/v1",
      "transport": "JSONRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/grpc",
      "transport": "GRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/json",
      "transport": "HTTP+JSON"
    }
  ],
  "signatures": [
    {
      "protected": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
      "signature": "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
      "header": {
        "kidHint": "contoso-key-1",
        "nonce": "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AgentInstance
{
	Id = "Security Copilot Platform Agent: 00222",
	OwnerIds = new List<string>
	{
		"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
		"b9108c41-d2d2-4e78-b073-92f57b752bd0",
	},
	ManagedBy = "719cc904-9700-4e08-9941-fd826cc84c60",
	OriginatingStore = "Microsoft Security Copilot",
	CreatedBy = "d47bffae-411a-4de9-8548-05e79bc01f0d",
	DisplayName = "Conditional Access Agent",
	SourceAgentId = "00222",
	AgentIdentityBlueprintId = "d0108c41-d2d2-4e78-b073-92f57b752bd0",
	AgentIdentityId = "dd108c41-d2d2-4e78-b073-92f57b752bd0",
	AgentUserId = "ee108c41-d2d2-4e78-b073-92f57b752bd0",
	CreatedDateTime = DateTimeOffset.Parse("2025-01-01T00:00:00.1234567Z"),
	LastModifiedDateTime = DateTimeOffset.Parse("2025-01-01T00:00:00.1234567Z"),
	Url = "https://conditional-access-agent.example.com/a2a/v1",
	PreferredTransport = "JSONRPC",
	AdditionalInterfaces = new List<AgentInterface>
	{
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/v1",
			Transport = "JSONRPC",
		},
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/grpc",
			Transport = "GRPC",
		},
		new AgentInterface
		{
			Url = "https://conditional-access-agent.example.com/a2a/json",
			Transport = "HTTP+JSON",
		},
	},
	Signatures = new List<AgentCardSignature>
	{
		new AgentCardSignature
		{
			Protected = "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
			Signature = "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
			Header = new JwsHeader
			{
				AdditionalData = new Dictionary<string, object>
				{
					{
						"kidHint" , "contoso-key-1"
					},
					{
						"nonce" , "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AgentRegistry.AgentInstances.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAgentInstance()
id := "Security Copilot Platform Agent: 00222"
requestBody.SetId(&id) 
ownerIds := []string {
	"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
	"b9108c41-d2d2-4e78-b073-92f57b752bd0",
}
requestBody.SetOwnerIds(ownerIds)
managedBy := "719cc904-9700-4e08-9941-fd826cc84c60"
requestBody.SetManagedBy(&managedBy) 
originatingStore := "Microsoft Security Copilot"
requestBody.SetOriginatingStore(&originatingStore) 
createdBy := "d47bffae-411a-4de9-8548-05e79bc01f0d"
requestBody.SetCreatedBy(&createdBy) 
displayName := "Conditional Access Agent"
requestBody.SetDisplayName(&displayName) 
sourceAgentId := "00222"
requestBody.SetSourceAgentId(&sourceAgentId) 
agentIdentityBlueprintId := "d0108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentIdentityBlueprintId(&agentIdentityBlueprintId) 
agentIdentityId := "dd108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentIdentityId(&agentIdentityId) 
agentUserId := "ee108c41-d2d2-4e78-b073-92f57b752bd0"
requestBody.SetAgentUserId(&agentUserId) 
createdDateTime , err := time.Parse(time.RFC3339, "2025-01-01T00:00:00.1234567Z")
requestBody.SetCreatedDateTime(&createdDateTime) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "2025-01-01T00:00:00.1234567Z")
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
url := "https://conditional-access-agent.example.com/a2a/v1"
requestBody.SetUrl(&url) 
preferredTransport := "JSONRPC"
requestBody.SetPreferredTransport(&preferredTransport) 


agentInterface := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/v1"
agentInterface.SetUrl(&url) 
transport := "JSONRPC"
agentInterface.SetTransport(&transport) 
agentInterface1 := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/grpc"
agentInterface1.SetUrl(&url) 
transport := "GRPC"
agentInterface1.SetTransport(&transport) 
agentInterface2 := graphmodels.NewAgentInterface()
url := "https://conditional-access-agent.example.com/a2a/json"
agentInterface2.SetUrl(&url) 
transport := "HTTP+JSON"
agentInterface2.SetTransport(&transport) 

additionalInterfaces := []graphmodels.AgentInterfaceable {
	agentInterface,
	agentInterface1,
	agentInterface2,
}
requestBody.SetAdditionalInterfaces(additionalInterfaces)


agentCardSignature := graphmodels.NewAgentCardSignature()
protected := "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9"
agentCardSignature.SetProtected(&protected) 
signature := "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w"
agentCardSignature.SetSignature(&signature) 
header := graphmodels.NewJwsHeader()
additionalData := map[string]interface{}{
	"kidHint" : "contoso-key-1", 
	"nonce" : "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0", 
}
header.SetAdditionalData(additionalData)
agentCardSignature.SetHeader(header)

signatures := []graphmodels.AgentCardSignatureable {
	agentCardSignature,
}
requestBody.SetSignatures(signatures)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
agentInstances, err := graphClient.AgentRegistry().AgentInstances().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AgentInstance agentInstance = new AgentInstance();
agentInstance.setId("Security Copilot Platform Agent: 00222");
LinkedList<String> ownerIds = new LinkedList<String>();
ownerIds.add("daf58b0e-44e1-433c-b6b0-ca70cae320b8");
ownerIds.add("b9108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setOwnerIds(ownerIds);
agentInstance.setManagedBy("719cc904-9700-4e08-9941-fd826cc84c60");
agentInstance.setOriginatingStore("Microsoft Security Copilot");
agentInstance.setCreatedBy("d47bffae-411a-4de9-8548-05e79bc01f0d");
agentInstance.setDisplayName("Conditional Access Agent");
agentInstance.setSourceAgentId("00222");
agentInstance.setAgentIdentityBlueprintId("d0108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setAgentIdentityId("dd108c41-d2d2-4e78-b073-92f57b752bd0");
agentInstance.setAgentUserId("ee108c41-d2d2-4e78-b073-92f57b752bd0");
OffsetDateTime createdDateTime = OffsetDateTime.parse("2025-01-01T00:00:00.1234567Z");
agentInstance.setCreatedDateTime(createdDateTime);
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("2025-01-01T00:00:00.1234567Z");
agentInstance.setLastModifiedDateTime(lastModifiedDateTime);
agentInstance.setUrl("https://conditional-access-agent.example.com/a2a/v1");
agentInstance.setPreferredTransport("JSONRPC");
LinkedList<AgentInterface> additionalInterfaces = new LinkedList<AgentInterface>();
AgentInterface agentInterface = new AgentInterface();
agentInterface.setUrl("https://conditional-access-agent.example.com/a2a/v1");
agentInterface.setTransport("JSONRPC");
additionalInterfaces.add(agentInterface);
AgentInterface agentInterface1 = new AgentInterface();
agentInterface1.setUrl("https://conditional-access-agent.example.com/a2a/grpc");
agentInterface1.setTransport("GRPC");
additionalInterfaces.add(agentInterface1);
AgentInterface agentInterface2 = new AgentInterface();
agentInterface2.setUrl("https://conditional-access-agent.example.com/a2a/json");
agentInterface2.setTransport("HTTP+JSON");
additionalInterfaces.add(agentInterface2);
agentInstance.setAdditionalInterfaces(additionalInterfaces);
LinkedList<AgentCardSignature> signatures = new LinkedList<AgentCardSignature>();
AgentCardSignature agentCardSignature = new AgentCardSignature();
agentCardSignature.setProtectedEscaped("eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9");
agentCardSignature.setSignature("xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w");
JwsHeader header = new JwsHeader();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("kidHint", "contoso-key-1");
additionalData.put("nonce", "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0");
header.setAdditionalData(additionalData);
agentCardSignature.setHeader(header);
signatures.add(agentCardSignature);
agentInstance.setSignatures(signatures);
AgentInstance result = graphClient.agentRegistry().agentInstances().post(agentInstance);
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
  id: 'Security Copilot Platform Agent: 00222',
  ownerIds: [
    'daf58b0e-44e1-433c-b6b0-ca70cae320b8',
    'b9108c41-d2d2-4e78-b073-92f57b752bd0'
  ],
  managedBy: '719cc904-9700-4e08-9941-fd826cc84c60',
  originatingStore: 'Microsoft Security Copilot',
  createdBy: 'd47bffae-411a-4de9-8548-05e79bc01f0d',
  displayName: 'Conditional Access Agent',
  sourceAgentId: '00222',
  agentIdentityBlueprintId: 'd0108c41-d2d2-4e78-b073-92f57b752bd0',
  agentIdentityId: 'dd108c41-d2d2-4e78-b073-92f57b752bd0',
  agentUserId: 'ee108c41-d2d2-4e78-b073-92f57b752bd0',
  createdDateTime: '2025-01-01T00:00:00.1234567Z',
  lastModifiedDateTime: '2025-01-01T00:00:00.1234567Z',
  url: 'https://conditional-access-agent.example.com/a2a/v1',
  preferredTransport: 'JSONRPC',
  additionalInterfaces: [
    {
      url: 'https://conditional-access-agent.example.com/a2a/v1',
      transport: 'JSONRPC'
    },
    {
      url: 'https://conditional-access-agent.example.com/a2a/grpc',
      transport: 'GRPC'
    },
    {
      url: 'https://conditional-access-agent.example.com/a2a/json',
      transport: 'HTTP+JSON'
    }
  ],
  signatures: [
    {
      protected: 'eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9',
      signature: 'xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w',
      header: {
        kidHint: 'contoso-key-1',
        nonce: 'f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0'
      }
    }
  ]
};

await client.api('/agentRegistry/agentInstances')
	.version('beta')
	.post(agentInstance);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AgentInstance;
use Microsoft\Graph\Beta\Generated\Models\AgentInterface;
use Microsoft\Graph\Beta\Generated\Models\AgentCardSignature;
use Microsoft\Graph\Beta\Generated\Models\JwsHeader;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AgentInstance();
$requestBody->setId('Security Copilot Platform Agent: 00222');
$requestBody->setOwnerIds(['daf58b0e-44e1-433c-b6b0-ca70cae320b8', 'b9108c41-d2d2-4e78-b073-92f57b752bd0', 	]);
$requestBody->setManagedBy('719cc904-9700-4e08-9941-fd826cc84c60');
$requestBody->setOriginatingStore('Microsoft Security Copilot');
$requestBody->setCreatedBy('d47bffae-411a-4de9-8548-05e79bc01f0d');
$requestBody->setDisplayName('Conditional Access Agent');
$requestBody->setSourceAgentId('00222');
$requestBody->setAgentIdentityBlueprintId('d0108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setAgentIdentityId('dd108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setAgentUserId('ee108c41-d2d2-4e78-b073-92f57b752bd0');
$requestBody->setCreatedDateTime(new \DateTime('2025-01-01T00:00:00.1234567Z'));
$requestBody->setLastModifiedDateTime(new \DateTime('2025-01-01T00:00:00.1234567Z'));
$requestBody->setUrl('https://conditional-access-agent.example.com/a2a/v1');
$requestBody->setPreferredTransport('JSONRPC');
$additionalInterfacesAgentInterface1 = new AgentInterface();
$additionalInterfacesAgentInterface1->setUrl('https://conditional-access-agent.example.com/a2a/v1');
$additionalInterfacesAgentInterface1->setTransport('JSONRPC');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface1;
$additionalInterfacesAgentInterface2 = new AgentInterface();
$additionalInterfacesAgentInterface2->setUrl('https://conditional-access-agent.example.com/a2a/grpc');
$additionalInterfacesAgentInterface2->setTransport('GRPC');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface2;
$additionalInterfacesAgentInterface3 = new AgentInterface();
$additionalInterfacesAgentInterface3->setUrl('https://conditional-access-agent.example.com/a2a/json');
$additionalInterfacesAgentInterface3->setTransport('HTTP+JSON');
$additionalInterfacesArray []= $additionalInterfacesAgentInterface3;
$requestBody->setAdditionalInterfaces($additionalInterfacesArray);

$signaturesAgentCardSignature1 = new AgentCardSignature();
$signaturesAgentCardSignature1->setEscapedProtected('eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9');
$signaturesAgentCardSignature1->setSignature('xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w');
$signaturesAgentCardSignature1Header = new JwsHeader();
$additionalData = [
'kidHint' => 'contoso-key-1',
'nonce' => 'f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0',
];
$signaturesAgentCardSignature1Header->setAdditionalData($additionalData);
$signaturesAgentCardSignature1->setHeader($signaturesAgentCardSignature1Header);
$signaturesArray []= $signaturesAgentCardSignature1;
$requestBody->setSignatures($signaturesArray);


$result = $graphServiceClient->agentRegistry()->agentInstances()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.agent_instance import AgentInstance
from msgraph_beta.generated.models.agent_interface import AgentInterface
from msgraph_beta.generated.models.agent_card_signature import AgentCardSignature
from msgraph_beta.generated.models.jws_header import JwsHeader
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AgentInstance(
	id = "Security Copilot Platform Agent: 00222",
	owner_ids = [
		"daf58b0e-44e1-433c-b6b0-ca70cae320b8",
		"b9108c41-d2d2-4e78-b073-92f57b752bd0",
	],
	managed_by = "719cc904-9700-4e08-9941-fd826cc84c60",
	originating_store = "Microsoft Security Copilot",
	created_by = "d47bffae-411a-4de9-8548-05e79bc01f0d",
	display_name = "Conditional Access Agent",
	source_agent_id = "00222",
	agent_identity_blueprint_id = "d0108c41-d2d2-4e78-b073-92f57b752bd0",
	agent_identity_id = "dd108c41-d2d2-4e78-b073-92f57b752bd0",
	agent_user_id = "ee108c41-d2d2-4e78-b073-92f57b752bd0",
	created_date_time = "2025-01-01T00:00:00.1234567Z",
	last_modified_date_time = "2025-01-01T00:00:00.1234567Z",
	url = "https://conditional-access-agent.example.com/a2a/v1",
	preferred_transport = "JSONRPC",
	additional_interfaces = [
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/v1",
			transport = "JSONRPC",
		),
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/grpc",
			transport = "GRPC",
		),
		AgentInterface(
			url = "https://conditional-access-agent.example.com/a2a/json",
			transport = "HTTP+JSON",
		),
	],
	signatures = [
		AgentCardSignature(
			protected = "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
			signature = "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
			header = JwsHeader(
				additional_data = {
						"kid_hint" : "contoso-key-1",
						"nonce" : "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0",
				}
			),
		),
	],
)

result = await graph_client.agent_registry.agent_instances.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "Security Copilot Platform Agent: 00222",
  "ownerIds": [
    "daf58b0e-44e1-433c-b6b0-ca70cae320b8",
    "b9108c41-d2d2-4e78-b073-92f57b752bd0"
  ],
  "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
  "originatingStore": "Microsoft Security Copilot",
  "createdBy": "d47bffae-411a-4de9-8548-05e79bc01f0d",
  "displayName": "Conditional Access Agent",
  "sourceAgentId": "00222",
  "agentIdentityBlueprintId": "d0108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentIdentityId": "dd108c41-d2d2-4e78-b073-92f57b752bd0",
  "agentUserId": "ee108c41-d2d2-4e78-b073-92f57b752bd0",
  "createdDateTime": "2025-01-01T00:00:00.1234567Z",
  "lastModifiedDateTime": "2025-01-01T00:00:00.1234567Z",
  "url": "https://conditional-access-agent.example.com/a2a/v1",
  "preferredTransport": "JSONRPC",
  "additionalInterfaces": [
    {
      "url": "https://conditional-access-agent.example.com/a2a/v1",
      "transport": "JSONRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/grpc",
      "transport": "GRPC"
    },
    {
      "url": "https://conditional-access-agent.example.com/a2a/json",
      "transport": "HTTP+JSON"
    }
  ],
  "signatures": [
    {
      "protected": "eyJhbGciOiJFUzI1NiIsImtpZCI6ImRpZDp3ZWI6Y29udG9zby5leGFtcGxlI2tleS0xIiwidHlwIjoiYWdlbnRjYXJkK2p3cyJ9",
      "signature": "xOSim9oMw_CdZM-qDhmwpB5fJcBx5I30yh-FZULd1j9ruPEUBnJzmfCynNfH1KgmJ2B7ulAYc7D2iIb-4Ul-8w",
      "header": {
        "kidHint": "contoso-key-1",
        "nonce": "f1e9b6c3-2f3a-4a3a-b604-1f9af3f2a9c0"
      }
    }
  ]
}
```
