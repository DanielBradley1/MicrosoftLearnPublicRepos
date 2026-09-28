<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentCommunicationConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the communication configuration for an agent, including the endpoint binding \(bot ID or callback URI\) and the Teams message notification settings that agents use to receive messages.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| **Agent identity blueprint** |  |  |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-get-communicationconfiguration?view=graph-rest-beta) | [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) | Read the communication configuration of an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta). |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-update-communicationconfiguration?view=graph-rest-beta) | [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) | Replace the communication configuration of an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta). |
| **Agent identity** |  |  |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentidentity-get-communicationconfiguration?view=graph-rest-beta) | [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) | Read the communication configuration of an [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-beta). |
| [Update](https://learn.microsoft.com/en-us/graph/api/agentidentity-update-communicationconfiguration?view=graph-rest-beta) | [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) | Replace the communication configuration of an [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-beta). |
| [reset](https://learn.microsoft.com/en-us/graph/api/agentcommunicationconfiguration-reset?view=graph-rest-beta) | [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) | Reset the communication configuration override for an agent identity, which restores effective configuration resolution to the agent blueprint level, and returns the blueprint's communication configuration as the new effective configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endpointConfiguration | [agentEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentendpointconfiguration?view=graph-rest-beta) | The endpoint binding \(bot ID or callback URI\) that the agent uses to receive messages. |
| isOverridableAtAgentIdLevel | Boolean | Indicates whether individual agent instances created from this blueprint can override the `endpointConfiguration`. When `true`, each instance can override it; when `false`, every instance inherits it. Not nullable. |
| teamworkConfiguration | [agentTeamworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentteamworkconfiguration?view=graph-rest-beta) | The per-conversation-context message notification settings \(group chat, channel, one-on-one chat, and meeting chat\) that agents use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentCommunicationConfiguration",
  "isOverridableAtAgentIdLevel": "Boolean",
  "endpointConfiguration": {"@odata.type": "microsoft.graph.agentEndpointConfiguration"},
  "teamworkConfiguration": {"@odata.type": "microsoft.graph.agentTeamworkConfiguration"}
}
```
