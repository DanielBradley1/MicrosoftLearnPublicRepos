<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-aggregatedpolicycompliance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# aggregatedPolicyCompliance resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an aggregate view of device compliance for a managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List aggregated policy compliances](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-aggregatedpolicycompliances?view=graph-rest-beta) | [microsoft.graph.managedTenants.aggregatedPolicyCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-aggregatedpolicycompliance?view=graph-rest-beta) collection | Get a list of the [aggregatedPolicyCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-aggregatedpolicycompliance?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliancePolicyId | String | Identifier for the device compliance policy. Optional. Read-only. |
| compliancePolicyName | String | Name of the device compliance policy. Optional. Read-only. |
| compliancePolicyPlatform | String | Platform for the device compliance policy. The possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `androidAOSP`, `all`. Optional. Read-only. |
| compliancePolicyType | String | The type of compliance policy. Optional. Read-only. |
| id | String | Unique identifier for the aggregate device compliance policy. Required. Read-only |
| lastRefreshedDateTime | DateTimeOffset | Date and time the entity was last updated in the multi-tenant management platform. Optional. Read-only. |
| numberOfCompliantDevices | Int64 | The number of devices that are in a compliant status. Optional. Read-only. |
| numberOfErrorDevices | Int64 | The number of devices that are in an error status. Optional. Read-only. |
| numberOfNonCompliantDevices | Int64 | The number of device that are in a non-compliant status. Optional. Read-only. |
| policyModifiedDateTime | DateTimeOffset | The date and time the device policy was last modified. Optional. Read-only. |
| tenantDisplayName | String | The display name for the managed tenant. Optional. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.aggregatedPolicyCompliance",
  "id": "String (identifier)",
  "tenantId": "String",
  "tenantDisplayName": "String",
  "compliancePolicyId": "String",
  "compliancePolicyName": "String",
  "compliancePolicyType": "String",
  "compliancePolicyPlatform": "String",
  "numberOfCompliantDevices": "Integer",
  "numberOfNonCompliantDevices": "Integer",
  "numberOfErrorDevices": "Integer",
  "policyModifiedDateTime": "String (timestamp)",
  "lastRefreshedDateTime": "String (timestamp)"
}
```
