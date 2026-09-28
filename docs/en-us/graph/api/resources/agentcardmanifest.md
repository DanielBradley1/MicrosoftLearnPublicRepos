<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentCardManifest resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Represents the manifest definition for an AI agent, including its capabilities, skills, security requirements, and metadata. An agent card manifest defines how an agent presents itself to users and systems. This resource is associated with [agent instances](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) through the [agent registry](https://learn.microsoft.com/en-us/graph/api/resources/agentregistry?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentinstance-list-agentcardmanifest?view=graph-rest-beta) | [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) collection | Get a list of the agentCardManifest objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentcardmanifest-get?view=graph-rest-beta) | [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) | Read the properties and relationships of [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentcardmanifest-update?view=graph-rest-beta) | [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) | Update the properties of an agentCardManifest object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [agentCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/agentcapabilities?view=graph-rest-beta) | A declaration of optional capabilities supported by the agent. |
| createdBy | String | Object ID of the user or application that created the agent card manifest. Read-only. |
| createdDateTime | DateTimeOffset | When this agent card manifest was created. |
| defaultInputModes | String collection | Default set of supported input MIME types for all skills, which can be overridden on a per-skill basis. |
| defaultOutputModes | String collection | Default set of supported output MIME types for all skills, which can be overridden on a per-skill basis. |
| description | String | A human-readable description of the agent. |
| displayName | String | A human-readable display name of the agent. |
| documentationUrl | String | URL to agent's documentation. |
| iconUrl | String | URL to agent's icon image. |
| id | String | ID of the agent card manifest. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Key. |
| lastModifiedDateTime | DateTimeOffset | When this agent card manifest was last modified. |
| managedBy | String | **appId** \(referred to as **Application \(client\) ID** on the Microsoft Entra admin center\) of the application managing this agent manifest. |
| originatingStore | String | Name of the store/system where agent originated. For example `Copilot Studio`. |
| ownerIds | String collection | List of object IDs for the owners of the agent card manifest. |
| protocolVersion | String | Protocol version supported by the agent. |
| provider | [agentProvider](https://learn.microsoft.com/en-us/graph/api/resources/agentprovider?view=graph-rest-beta) | Information about the organization providing the agent. |
| security | [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/securityrequirement?view=graph-rest-beta) collection | Security requirements - array of security scheme references. |
| securitySchemes | [securitySchemes](https://learn.microsoft.com/en-us/graph/api/resources/securityschemes?view=graph-rest-beta) | Dictionary of security scheme definitions keyed by scheme name. |
| skills | [agentSkill](https://learn.microsoft.com/en-us/graph/api/resources/agentskill?view=graph-rest-beta) collection | Skills/capabilities that the agent can perform |
| supportsAuthenticatedExtendedCard | Boolean | Whether agent supports authenticated extended card retrieval |
| version | String | Version of the agent implementation |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentCardManifest",
  "id": "String (identifier)",
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
