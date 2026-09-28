<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-networkaccessroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# networkAccessRoot resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the top-level namespace for network access-related resources and functionalities within the network infrastructure. It serves as the entry point for accessing various network access-related APIs and operations.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| cloudFirewallPolicies | [microsoft.graph.networkaccess.cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) collection | A collection of cloud firewall policies that define rules for managing network traffic through the Global Secure Access services. |
| connectivity | [microsoft.graph.networkaccess.connectivity](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectivity?view=graph-rest-beta) | Connectivity represents all the connectivity components in Global Secure Access. |
| filteringPolicies | [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta) collection | A filtering policy defines the specific traffic that is allowed or blocked through the Global Secure Access services for a filtering profile. |
| filteringProfiles | [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) collection | A filtering profile associates network access policies with Microsoft Entra ID Conditional Access policies, so that access policies can be applied to users and groups. |
| threatIntelligencePolicy | [microsoft.graph.networkaccess.threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) | A threat intelligence policy allows you to apply security controls blocking known threats and malicious destinations based on Microsoft's threat indicator feeds. |
| logs | [microsoft.graph.networkaccess.logs](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-logs?view=graph-rest-beta) | Represents network connections that are routed through Global Secure Access. |
| reports | [microsoft.graph.networkaccess.reports](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-reports?view=graph-rest-beta) | Represents the status of the Global Secure Access services for the tenant. |
| settings | [microsoft.graph.networkaccess.settings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-settings?view=graph-rest-beta) | Global Secure Access settings. |
| tenantStatus | [microsoft.graph.networkaccess.tenantStatus](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tenantstatus?view=graph-rest-beta) | Represents the status of the Global Secure Access services for the tenant. |
| tls | [microsoft.graph.networkaccess.tlsTermination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlstermination?view=graph-rest-beta) | A container for tenant-level TLS inspection settings for Global Secure Access. |
| tlsInspectionPolicies | [microsoft.graph.networkaccess.tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) collection | Allows you to configure TLS termination for your organization's network traffic through Global Secure Access. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.networkAccessRoot",
  "id": "String (identifier)"
}
```
