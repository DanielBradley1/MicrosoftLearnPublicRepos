<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# agentRegistration resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an agent registration containing metadata, endpoint configuration, and publishing information. This entity provides developers and administrators with all details needed to manage agent instances including their owners and agent card manifest.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-create) | `agentRegistration` | Create a new `agentRegistration` object. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-get) | `agentRegistration` | Retrieve the properties of an `agentRegistration` object. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-update) | None | Update an `agentRegistration` object. |
| [Delete](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-delete) | None | Delete an `agentRegistration` object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `agentCard` | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json) | Flexible JSON manifest containing agent card information following public manifest specifications. Can include display name, description, icon URL, version, provider, capabilities, skills, security, and other manifest-defined fields. |
| `agentIdentityBlueprintId` | String | Agent identity blueprint identifier. |
| `agentIdentityId` | String | Entra agent identity identifier. |
| `createdBy` | String | The unique identifier of the user or app who created the agent registration. |
| `description` | String | The agent description providing an overview of its purpose and capabilities. |
| `displayName` | String | Display name for the agent instance. Required. |
| `id` | String | Unique identifier for the agent registration. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity). |
| `lastPublishedBy` | String | The unique identifier of the last person to publish the agent. |
| `managedByAppId` | String | Application identifier managing this agent. |
| `originatingStore` | String | Name of the store or system where the agent originated. |
| `ownerIds` | String collection | List of owner identifiers for the agent. Either owners or `managedByAppId` is required. |
| `sourceAgentId` | String | Original agent identifier from source system. |
| `sourceCreatedDateTime` | DateTimeOffset | The date and time when the agent instance was created from source. |
| `sourceLastModifiedDateTime` | DateTimeOffset | The date and time when the agent instance was last modified from source. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentRegistration",
  "id": "String",
  "displayName": "String",
  "description": "String",
  "ownerIds": ["String"],
  "createdBy": "String",
  "sourceCreatedDateTime": "String (timestamp)",
  "sourceLastModifiedDateTime": "String (timestamp)",
  "lastPublishedBy": "String",
  "managedByAppId": "String",
  "sourceAgentId": "String",
  "originatingStore": "String",
  "agentIdentityId": "String",
  "agentIdentityBlueprintId": "String",
  "agentCard": {
    "@odata.type": "microsoft.graph.Json"
  }
}
```
