<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/selectedgroupsspendingpolicy -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# selectedGroupsSpendingPolicy resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A spending policy that governs only the users in its assigned groups. Derived from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy); it adds the `assignedGroups` relationship. Omitting `assignedGroups` or supplying an empty collection creates a disabled policy.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-list) | [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy) collection | Get a list of spendingPolicy objects. |
| [Create](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-create) | [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy) | Create a new spendingPolicy object. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-get) | [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy) | Retrieve the properties and relationships of a spendingPolicy object. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-update) | [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy) | Update a spendingPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicy-delete) | None | Delete a spendingPolicy object. |
| [List assigned groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-list-assignedgroups) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group) collection | Get the list of groups assigned to the policy. |
| [Add assigned group](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-post-assignedgroups) | None | Add a group reference to the policy. |
| [Remove assigned group](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-delete-assignedgroups) | None | Remove a group reference from the policy. |

## Properties

All properties are inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). This type adds no properties of its own.

| Property | Type | Description |
| :--- | :--- | :--- |
| `billingMethods` | [costManagementBillingMethods](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy#costmanagementbillingmethods-enumeration) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). How consumption is funded. |
| `createdBy` | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). The identity that created the policy. Read-only. |
| `createdDateTime` | DateTimeOffset | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). When the policy was created. Read-only. |
| `displayName` | String | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). The policy display name. Required on create. |
| `id` | String | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). Entity key. Read-only. |
| `lastModifiedBy` | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). The identity that last modified the policy. Read-only. |
| `lastModifiedDateTime` | DateTimeOffset | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). When the policy was last modified. Read-only. |
| `periodLimit` | [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). The consumption limit for one period. Required on create. |
| `perUserLimit` | [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). The uniform per-user consumption limit. Required on create. |
| `status` | [spendingPolicyStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy#spendingpolicystatus-enumeration) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). The policy lifecycle status. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `assignedGroups` | [group](https://learn.microsoft.com/en-us/graph/api/resources/group) collection | The groups the policy is assigned to. A reference navigation managed with `$ref` add and remove through the `microsoft.graph.selectedGroupsSpendingPolicy` cast segment. |
| `emailThresholdSettings` | [costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting) | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). Nullable. Notify-only email threshold configuration. |
| `serviceSettings` | [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) collection | Inherited from [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy). Per-service settings contained by the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.selectedGroupsSpendingPolicy",
  "billingMethods": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "DateTimeOffset",
  "displayName": "String",
  "id": "String",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "DateTimeOffset",
  "periodLimit": {
    "@odata.type": "microsoft.graph.costManagementQuantity"
  },
  "perUserLimit": {
    "@odata.type": "microsoft.graph.costManagementQuantity"
  },
  "status": "String"
}
```
