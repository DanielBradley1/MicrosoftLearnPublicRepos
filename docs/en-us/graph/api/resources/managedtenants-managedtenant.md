<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managedtenant?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# managedTenant resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

As the root resource of the Microsoft 365 Lighthouse API, **managedTenant** represents the capabilities available to a Managed Service Provider \(MSP\) to scale the remote management of its customer tenants to help get them into a healthy and secure state.

The Microsoft 365 Lighthouse API is defined in the OData subnamespace, `microsoft.graph.managedTenants`.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| aggregatedPolicyCompliances | [microsoft.graph.managedTenants.aggregatedPolicyCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-aggregatedpolicycompliance?view=graph-rest-beta) collection | Aggregate view of device compliance policies across managed tenants. |
| auditEvents | [microsoft.graph.managedTenants.auditEvent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-auditevent?view=graph-rest-beta) collection | The collection of audit events across managed tenants. |
| cloudPcConnections | [microsoft.graph.managedTenants.cloudPcConnection](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcconnection?view=graph-rest-beta) collection | The collection of cloud PC connections across managed tenants. |
| cloudPcDevices | [microsoft.graph.managedTenants.cloudPcDevice](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcdevice?view=graph-rest-beta) collection | The collection of cloud PC devices across managed tenants. |
| cloudPcsOverview | [microsoft.graph.managedTenants.cloudPcOverview](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-cloudpcoverview?view=graph-rest-beta) collection | Overview of cloud PC information across managed tenants. |
| conditionalAccessPolicyCoverages | [microsoft.graph.managedTenants.conditionalAccessPolicyCoverage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-conditionalaccesspolicycoverage?view=graph-rest-beta) collection | Aggregate view of conditional access policy coverage across managed tenants. |
| credentialUserRegistrationsSummaries | [microsoft.graph.managedTenants.credentialUserRegistrationsSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-credentialuserregistrationssummary?view=graph-rest-beta) collection | Summary information for user registration for multi-factor authentication and self service password reset across managed tenants. |
| deviceCompliancePolicySettingStateSummaries | [microsoft.graph.managedTenants.deviceCompliancePolicySettingStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-devicecompliancepolicysettingstatesummary?view=graph-rest-beta) collection | Summary information for device compliance policy setting states across managed tenants. |
| managedDeviceCompliances | [microsoft.graph.managedTenants.managedDeviceCompliance](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliance?view=graph-rest-beta) collection | The collection of compliance for managed devices across managed tenants. |
| managedDeviceComplianceTrends | [microsoft.graph.managedTenants.managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) collection | Trend insights for device compliance across managed tenants. |
| managementActions | [microsoft.graph.managedTenants.managementAction](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementaction?view=graph-rest-beta) collection | The collection of baseline management actions across managed tenants. |
| managementActionTenantDeploymentStatuses | [microsoft.graph.managedTenants.managementActionTenantDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiontenantdeploymentstatus?view=graph-rest-beta) collection | The tenant level status of management actions across managed tenants. |
| managementIntents | [microsoft.graph.managedTenants.managementIntent](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintent?view=graph-rest-beta) collection | The collection of baseline management intents across managed tenants. |
| managementTemplates | [microsoft.graph.managedTenants.managementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplate?view=graph-rest-beta) collection | The collection of baseline management templates across managed tenants. |
| myRoles | [microsoft.graph.managedTenants.myRole](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-myrole?view=graph-rest-beta) collection | The collection of role assignments to a signed-in user for a managed tenant. |
| tenantGroups | [microsoft.graph.managedTenants.tenantGroup](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantgroup?view=graph-rest-beta) collection | The collection of a logical grouping of managed tenants used by the multi-tenant management platform. |
| tenants | [microsoft.graph.managedTenants.tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta) collection | The collection of tenants associated with the managing entity. |
| tenantsCustomizedInformation | [microsoft.graph.managedTenants.tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) collection | The collection of tenant level customized information across managed tenants. |
| tenantsDetailedInformation | [microsoft.graph.managedTenants.tenantDetailedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantdetailedinformation?view=graph-rest-beta) collection | The collection tenant level detailed information across managed tenants. |
| tenantTags | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) collection | The collection of tenant tags across managed tenants. |
| tenantUsage | [microsoft.graph.managedTenants.tenantUsage](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantusage?view=graph-rest-beta) collection | The collection of tenant usage across managed tenants. |
| windowsDeviceMalwareStates | [microsoft.graph.managedTenants.windowsDeviceMalwareState](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsdevicemalwarestate?view=graph-rest-beta) collection | The state of malware for Windows devices, registered with Microsoft Endpoint Manager, across managed tenants. |
| windowsProtectionStates | [microsoft.graph.managedTenants.windowsProtectionState](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-windowsprotectionstate?view=graph-rest-beta) collection | The protection state for Windows devices, registered with Microsoft Endpoint Manager, across managed tenants. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managedTenant",
  "id": "String (identifier)"
}
```
