<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertthreshold -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementAlertThreshold resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A single notify-only alert threshold. This is an abstract type. Every threshold is one of its derived types, identified by the `@odata.type` property on create:

- [percentageCostManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/percentagecostmanagementalertthreshold)
- [absoluteCostManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/absolutecostmanagementalertthreshold)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `value` | Double | The threshold value. The permitted range is set by the derived type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementAlertThreshold",
  "value": "Double"
}
```
