<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# spendingPolicyServiceSetting resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Desired governance state for a single service within a spending policy. Keyed by `serviceId`. The collection has no `DELETE`; removal is expressed by setting `state` to `disabled`, which retains the entry in that state.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-list) | [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) collection | Get a list of spendingPolicyServiceSetting objects. |
| [Create](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-create) | [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) | Create a new spendingPolicyServiceSetting object. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-get) | [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) | Retrieve the properties of a spendingPolicyServiceSetting object. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-update) | [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) | Update a spendingPolicyServiceSetting object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `parentEtag` | String | The containing policy's ETag. Use this value in `If-Match` for concurrency control on service-setting changes. Read-only. |
| `parentStatus` | [spendingPolicyStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy#spendingpolicystatus-enumeration) | The containing policy's lifecycle status. A service setting has no effect while the parent policy is disabled or provisioning. Read-only. |
| `serviceId` | String | The key identifying a governed service category, such as `cowork` or `workIQ`. Multiple billable services can share a category. This isn't a directory object identifier. Required on create. |
| `state` | [serviceSettingState](#servicesettingstate-enumeration) | Whether the service is governed \(`enabled`\) or excluded \(`disabled`\). Required on create. |

### serviceSettingState enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `enabled` | The service is governed by the policy. |
| `disabled` | The service is excluded from the policy. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.spendingPolicyServiceSetting",
  "parentEtag": "String",
  "parentStatus": "String",
  "serviceId": "String",
  "state": "String"
}
```
