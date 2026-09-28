<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentinterface?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentInterface resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Declares a combination of a target URL and a transport protocol for interacting with the agent, as defined in the [agentInstance object](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta). This allows agents to expose the same functionality over multiple transport mechanisms.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| transport | String | The transport protocol supported at this URL. |
| url | String | The URL where this interface is available. Must be a valid absolute HTTPS URL in production. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentInterface",
  "url": "String",
  "transport": "String"
}
```
