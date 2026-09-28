<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentCollection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Represents a collection of [agent instances](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) in the [agentRegistry](https://learn.microsoft.com/en-us/graph/api/resources/agentregistry?view=graph-rest-beta). Agent collections provide a way to organize and group related agent instances for management and organizational purposes.

Agent collections allow grouping of agent instances for organizational and access control purposes. Special collections are `Global` and `Quarantined`.

### Reserved Collections

Two system-reserved collections are always available per tenant:

| Collection | ID | Purpose |
| --- | --- | --- |
| Global | `00000000-0000-0000-0000-000000000001` | Tenant-wide pool of generally available agents |
| Quarantined | `00000000-0000-0000-0000-000000000002` | Holding area for blocked / review-pending agents |

#### Key behaviors:

1. Always-present: A GET by reserved ID never returns 404 \(synthetic returned if not persisted\).
2. Immutability: You can't UPDATE or DELETE a reserved collection, otherwise, a `403 Forbidden` error code with the message "collectionImmutable" is returned.
3. Creation protections: Attempting to create a new collection whose **displayName** matches a reserved one returns `409 Conflict` error code.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/agentinstance-list-collections?view=graph-rest-beta) | [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta) collection | Get a list of the agentCollection objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/agentregistry-post-agentcollections?view=graph-rest-beta) | [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta) | Create a new agentCollection object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentcollection-get?view=graph-rest-beta) | [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta) | Read the properties and relationships of [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentcollection-update?view=graph-rest-beta) | None | Update the properties of an agentCollection object. |
| [List members of agentCollection](https://learn.microsoft.com/en-us/graph/api/agentcollection-list-members?view=graph-rest-beta) | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) collection | List of [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) objects in the collection. |
| [Add to collection](https://learn.microsoft.com/en-us/graph/api/agentcollection-post-members?view=graph-rest-beta) | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) | Add an [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) to the agentCollection. |
| [Remove from collection](https://learn.microsoft.com/en-us/graph/api/agentcollection-delete-members?view=graph-rest-beta) | None | Remove an [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object from the agentCollection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | Object ID of the user or app that created the agent instance. |
| createdDateTime | DateTimeOffset | Timestamp when agent collection was created. |
| description | String | Description / purpose of the collection. |
| displayName | String | Friendly name of the collection. |
| id | String | Unique identifier for the collection. Key. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Timestamp of last update. |
| managedBy | String | **appId** \(referred to as **Application \(client\) ID** on the Microsoft Entra admin center\) of the service principal managing this agent. |
| originatingStore | String | Source system/store where the collection originated. For example `Copilot Studio`. |
| ownerIds | String collection | List of object IDs for the owners of the agent instance. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) collection | List of agent instances that are members of this collection. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentCollection",
  "id": "String (identifier)",
  "ownerIds": [
    "String"
  ],
  "managedBy": "String",
  "originatingStore": "String",
  "createdBy": "String",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
