<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# onPremisesAgent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents on-premises agent. On-premises agents installed by a tenant administrator can be configured to access/handle requests to a particular [published resource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onpremisesagent-list?view=graph-rest-beta) | [onPremisesAgent](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) collection | Get an **onPremisesAgents** object collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/onpremisesagent-get?view=graph-rest-beta) | [onPremisesAgent](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) | Read the properties and relationships of an **onPremisesAgent** object. |
| [Assign to agent group](https://learn.microsoft.com/en-us/graph/api/onpremisesagent-post-agentgroups?view=graph-rest-beta) | None | Assign an **onPremisesAgent** to an **onPremisesAgentGroup**. |
| [Remove from agent group](https://learn.microsoft.com/en-us/graph/api/onpremisesagent-delete-agentgroups?view=graph-rest-beta) | None | Remove an **onPremisesAgent** from an **onPremisesAgentGroup**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalIp | String | The external IP address as detected by the service for the agent machine. Read-only |
| id | String | The object id of the onPremisesAgent. Read-only. |
| machineName | String | The name of the machine that the agent is running on. Read-only |
| status | agentStatus | The possible values are: `active`, `inactive`. |
| supportedPublishingTypes | onPremisesPublishingType collection | The possible values are: `applicationProxy`, `exchangeOnline`, `authentication`, `provisioning`, `intunePfx`, `oflineDomainJoin`, `unknownFutureValue`, `privateAccess`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `privateAccess`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agentGroups | [onPremisesAgentGroup](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) collection | List of **onPremisesAgentGroups** that an **onPremisesAgent** is assigned to. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "externalIp": "String",
  "id": "String (identifier)",
  "machineName": "String",
  "status": "string",
  "supportedPublishingTypes": ["string"]
}
```
