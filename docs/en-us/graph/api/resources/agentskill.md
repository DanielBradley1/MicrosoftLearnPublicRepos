<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentskill?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentSkill resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Represents a distinct capability or function that an agent can perform, as defined in the [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A detailed description of the skill, intended to help clients or users understand its purpose and functionality. |
| displayName | String | A human-readable name for the skill. |
| examples | String collection | Example prompts or scenarios that this skill can handle. Provides a hint to the client on how to use the skill. |
| id | String | A unique identifier for the agent's skill. |
| inputModes | String collection | The set of supported input MIME types for this skill, overriding the agent's defaults. |
| outputModes | String collection | The set of supported output MIME types for this skill, overriding the agent's defaults. |
| security | [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/securityrequirement?view=graph-rest-beta) collection | Security schemes necessary for the agent to leverage this skill. |
| tags | String collection | A set of keywords describing the skill's capabilities. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentSkill",
  "id": "String",
  "displayName": "String",
  "description": "String",
  "tags": [
    "String"
  ],
  "examples": [
    "String"
  ],
  "inputModes": [
    "String"
  ],
  "outputModes": [
    "String"
  ],
  "security": [
    {
      "@odata.type": "microsoft.graph.securityRequirement"
    }
  ]
}
```
