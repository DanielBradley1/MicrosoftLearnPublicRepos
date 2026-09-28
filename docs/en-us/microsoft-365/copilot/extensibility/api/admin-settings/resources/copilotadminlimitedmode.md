<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminlimitedmode -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# copilotAdminLimitedMode resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a setting that controls whether users of Microsoft 365 Copilot in Teams meetings can receive responses to sentiment-related prompts. When this setting is enabled, Copilot in Teams meetings doesn't respond to sentiment-related prompts and questions from the user. When disabled, it responds to them. Copilot in Teams meetings currently honors this setting. By default, the setting is disabled.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/copilotadminlimitedmode-get) | `copilotAdminLimitedMode` | Read the properties and relationships of a `copilotAdminLimitedMode` object. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/copilotadminlimitedmode-update) | `copilotAdminLimitedMode` | Update the properties of a `copilotAdminLimitedMode`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `groupId` | String | The ID of a Microsoft Entra group, for which the value of `isEnabledForGroup` is applied. The default value is `null`. If `isEnabledForGroup` is set to `true`, the `groupId` value must be provided for the Copilot limited mode in Teams meetings to be enabled for the members of the group. Optional. |
| `isEnabledForGroup` | Boolean | Enables the user to be in limited mode for Copilot in Teams meetings. When `copilotAdminLimitedMode=true`, users in this mode can ask any questions, but Copilot doesn't respond to certain questions related to inferring emotions, behavior, or judgments. When `copilotAdminLimitedMode=false`, it responds to all types of questions grounded to the meeting conversation. The default value is `false`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotAdminLimitedMode",
  "groupId": "String",
  "isEnabledForGroup": "Boolean"
}
```
