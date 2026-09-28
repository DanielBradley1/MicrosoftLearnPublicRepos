<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/resources/copilotroot -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# copilotRoot resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A container for Microsoft 365 Copilot admin controls.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `admin` | [copilotAdmin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadmin) | The Microsoft 365 Copilot admin who can add or modify Copilot settings. Read-only. Nullable. |
| `interactionHistory` | [aiInteractionHistory](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/resources/aiinteractionhistory) | The history of interactions between AI agents and users. |
| `users` | [aiUser](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/resources/aiuser) collection | The list of AI users or agents. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotRoot"
}
```
