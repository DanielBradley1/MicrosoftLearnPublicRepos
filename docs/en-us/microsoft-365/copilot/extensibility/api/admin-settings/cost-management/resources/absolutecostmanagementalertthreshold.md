<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/absolutecostmanagementalertthreshold -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# absoluteCostManagementAlertThreshold resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A threshold expressed as an absolute quantity. The `value` is positive and is stated in the accompanying unit, which matches the policy's limit unit. Derived from [costManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertthreshold).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | The unit the threshold value is expressed in. |
| `value` | Double | Inherited from [costManagementAlertThreshold](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertthreshold). A positive absolute threshold value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.absoluteCostManagementAlertThreshold",
  "unit": "String",
  "value": "Double"
}
```
