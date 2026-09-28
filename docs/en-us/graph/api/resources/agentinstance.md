<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentInstance resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Represents a specific deployed instance of an AI agent in the Microsoft Entra Agent Registry. An agent instance is associated with an [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) that defines its capabilities, skills, and metadata. Agent instances can be organized into collections and are managed through the [agentRegistry](https://learn.microsoft.com/en-us/graph/api/resources/agentregistry?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentregistry-list-agentinstances?view=graph-rest-beta) | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) collection | Get a list of the agentInstance objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentregistry-post-agentinstances?view=graph-rest-beta) | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) | Create a new agentInstance object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentinstance-get?view=graph-rest-beta) | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) | Read the properties and relationships of [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentinstance-update?view=graph-rest-beta) | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) | Update the properties of an agentInstance object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/agentregistry-delete-agentinstances?view=graph-rest-beta) | None | Delete an agentInstance object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalInterfaces | [agentInterface](https://learn.microsoft.com/en-us/graph/api/resources/agentinterface?view=graph-rest-beta) collection | Additional interfaces/transports supported by the agent. |
| agentIdentityBlueprintId | String | Object ID of the [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta) object. |
| agentIdentityId | String | Object ID of the [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-beta) object. |
| agentUserId | String | Object ID of the [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-beta) associated with the agent. Read-only. |
| createdBy | String | Object ID of the user or application that created the agent instance. Read-only. |
| createdDateTime | DateTimeOffset | Timestamp when agent instance was created. Read-only. |
| displayName | String | Display name for the agent instance. |
| id | String | Unique identifier for the agent instance. Key. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Timestamp of last modification. |
| managedBy | String | **appId** \(referred to as **Application \(client\) ID** on the Microsoft Entra admin center\) of the application managing this agent. |
| originatingStore | String | Name of the store/system where agent originated. For example `Copilot Studio`. |
| ownerIds | String collection | List of object IDs for the owners of the agent instance. |
| preferredTransport | String | Preferred transport protocol. The possible values are `JSONRPC`, `GRPC`, and `HTTP+JSON`. |
| signatures | [agentCardSignature](https://learn.microsoft.com/en-us/graph/api/resources/agentcardsignature?view=graph-rest-beta) collection | Digital signatures for the agent instance. |
| sourceAgentId | String | Identifier of the agent in the original source system. |
| url | String | Endpoint URL for the agent instance. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agentCardManifest | [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) | The agent card manifest of the agent instance. |
| collections | [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta) collection | The agent collections that the agent instance is a member of. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentInstance",
  "id": "String (identifier)",
  "ownerIds": [
    "String"
  ],
  "managedBy": "String",
  "originatingStore": "String",
  "createdBy": "String",
  "displayName": "String",
  "sourceAgentId": "String",
  "agentIdentityBlueprintId": "String",
  "agentIdentityId": "String",
  "agentUserId": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "url": "String",
  "preferredTransport": "String",
  "additionalInterfaces": [
    {
      "@odata.type": "microsoft.graph.agentInterface"
    }
  ],
  "signatures": [
    {
      "@odata.type": "microsoft.graph.agentCardSignature"
    }
  ]
}
```
