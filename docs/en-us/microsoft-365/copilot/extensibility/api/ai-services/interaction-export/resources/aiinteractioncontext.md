<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractioncontext -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# aiInteractionContext resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents all contexts associated with an interaction.

Note

For information about the AI interactions that are included with this API and the relevant licensing requirements, see [Licensing and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#licensing-and-prerequisites) and [AI interactions returned](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory#ai-interactions-returned).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `contextReference` | String | The full file URL where the interaction happened. |
| `contextType` | String | The type of the file. |
| `displayName` | String | The name of the file. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contextReference": "String",
  "contextType": "String",
  "displayName": "String"
}
```
