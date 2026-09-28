<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# tenantGovernanceSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the tenant governance settings that control related tenant discovery and invitation capabilities. This is a singleton resource.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-get?view=graph-rest-beta) | [microsoft.graph.tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-beta) | Read the properties of the [tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-beta) singleton. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-update?view=graph-rest-beta) | [microsoft.graph.tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-beta) | Update the **canReceiveInvitations** property of the tenant governance settings. |
| [Enable related tenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-beta) | None | Enable the related tenants feature for tenant discovery. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| canReceiveInvitations | Boolean | Indicates whether the tenant can receive governance invitations. When set to `false`, the tenant cannot receive new governance invitations. When set to `true`, other tenants can send your tenant invitations by providing your tenant id or domain name. Default value is `false`. |
| isRelatedTenantsEnabled | Boolean | Indicates whether the related tenants feature is enabled for tenant discovery. When set to `false`, related tenant APIs don't work. This property can be enabled by calling the [enableRelatedTenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-beta) action. Default value is `false`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantGovernanceSetting",
  "isRelatedTenantsEnabled": "Boolean",
  "canReceiveInvitations": "Boolean"
}
```
