<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentcapabilities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentCapabilities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Defines optional capabilities defined in the [agent card manifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| extensions | [agentExtension](https://learn.microsoft.com/en-us/graph/api/resources/agentextension?view=graph-rest-beta) collection | A list of protocol extensions supported by the agent. |
| pushNotifications | Boolean | Indicates if the agent supports sending push notifications for asynchronous task updates. |
| stateTransitionHistory | Boolean | Indicates if the agent provides a history of state transitions for a task. |
| streaming | Boolean | Indicates if the agent supports Server-Sent Events \(SSE\) for streaming responses. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentCapabilities",
  "streaming": "Boolean",
  "pushNotifications": "Boolean",
  "stateTransitionHistory": "Boolean",
  "extensions": [
    {
      "@odata.type": "microsoft.graph.agentExtension"
    }
  ]
}
```
