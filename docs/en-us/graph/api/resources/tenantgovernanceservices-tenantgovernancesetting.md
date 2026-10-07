<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# tenantGovernanceSetting resource type

Namespace: microsoft.graph

Represents the tenant governance settings that control related tenant discovery and invitation capabilities. This is a singleton resource.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-get?view=graph-rest-1.0) | [microsoft.graph.tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-1.0) | Read the properties of the [tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-1.0) singleton. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-update?view=graph-rest-1.0) | [microsoft.graph.tenantGovernanceSetting](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancesetting?view=graph-rest-1.0) | Update the **canReceiveInvitations** property of the tenant governance settings. |
| [Enable related tenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-1.0) | None | Enable the related tenants feature for tenant discovery. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| canReceiveInvitations | Boolean | Indicates whether the tenant can receive governance invitations. When set to `false`, the tenant cannot receive new governance invitations. When set to `true`, other tenants can send your tenant invitations by providing your tenant id or domain name. Default value is `false`. |
| isRelatedTenantsEnabled | Boolean | Indicates whether the related tenants feature is enabled for tenant discovery. When set to `false`, related tenant APIs don't work. This property can be enabled by calling the [enableRelatedTenants](https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-tenantgovernancesetting-enablerelatedtenants?view=graph-rest-1.0) action. Default value is `false`. |

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
