<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementAlertSetting resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Notify-only alert configuration for a spending policy, addressed as the policy's `emailThresholdSettings`. Each policy has at most one, retrieved from its own URL beneath the policy. `PATCH` creates or updates the configuration; `DELETE` turns alerting off without removing separately managed recipient references. Recipients are typed `user` references managed separately with `$ref`.

Configure the alert setting after creating the policy, not inline in the policy create payload. Create a disabled configuration, add recipient references, and then enable it. At least one recipient is required while alerting is enabled. Recipients must resolve to users in the tenant; their email addresses are resolved when an alert is sent. Thresholds notify recipients but don't increase limits or authorize consumption.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-get) | [costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting) | Retrieve the properties and relationships of a costManagementAlertSetting object. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-update) | [costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting) | Create or update a costManagementAlertSetting object. |
| [Delete](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-delete) | None | Delete a costManagementAlertSetting object. |
| [List recipients](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-list-recipients) | [user](https://learn.microsoft.com/en-us/graph/api/resources/user) collection | Get the list of recipients notified by the alert setting. |
| [Add recipient](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-post-recipients) | None | Add a user reference as an alert recipient. |
| [Remove recipient](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-delete-recipients) | None | Remove an alert recipient. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Inherited entity key. Read-only. |
| `isEnabled` | Boolean | Whether alerting is enabled. On an existing configuration, omitting this property keeps its current effective value; explicit `null` isn't accepted. Enabling requires at least one linked recipient. |
| `thresholds` | [costManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertthreshold) collection | The configured thresholds, each with a concrete `@odata.type`. An explicit empty array \(`[]`\) clears the thresholds without removing the configuration or its recipients. Omitting this property on an update keeps the existing thresholds; explicit `null` for the collection or for an individual entry isn't accepted. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `recipients` | [user](https://learn.microsoft.com/en-us/graph/api/resources/user) collection | The directory users notified when a threshold is crossed. A reference navigation managed with `$ref` add and remove. The address is resolved at send time. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementAlertSetting",
  "id": "String",
  "isEnabled": "Boolean",
  "thresholds": [
    {
      "@odata.type": "microsoft.graph.costManagementAlertThreshold"
    }
  ]
}
```
