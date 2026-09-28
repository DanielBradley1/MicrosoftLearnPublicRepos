<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadmin -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# copilotAdmin resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a container for Microsoft 365 Copilot admin settings.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `settings` | [copilotAdminSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminsetting) | Represents the settings for Copilot admin. |

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `policySettings` | [copilotPolicySetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotpolicysetting) collection | Collection of Copilot settings managed through policy services. The API addresses settings individually by their identifier. |
| `settings` | [copilotAdminSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminsetting) | Represents the settings for Copilot admin. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotAdmin"
}
```
