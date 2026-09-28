<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminsetting -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# copilotAdminSetting resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents an admin setting for Microsoft 365 Copilot.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `limitedMode` | [copilotAdminLimitedMode](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminlimitedmode) | Represents a setting that controls whether users of Microsoft 365 Copilot in Teams meetings can receive responses to sentiment-related prompts. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotAdminSetting"
}
```
