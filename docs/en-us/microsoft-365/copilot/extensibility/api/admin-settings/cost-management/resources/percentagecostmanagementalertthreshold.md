<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/percentagecostmanagementalertthreshold -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# percentageCostManagementAlertThreshold resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A threshold expressed as a percentage of the policy's period limit. The `value` is an integer from 1 to 100 and carries no unit. Derived from [costManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertthreshold).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `value` | Double | Inherited from [costManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertthreshold). An integer from 1 to 100, a share of the policy's period limit. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.percentageCostManagementAlertThreshold",
  "value": "Double"
}
```
