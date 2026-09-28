<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-settings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-22 -->

# settings resource type for Global Secure Access

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The tenant configuration settings associated with Microsoft Entra Internet Access and Microsoft Entra Private Access. These capabilities are under the umbrella of Global Secure Access.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| conditionalAccess | [microsoft.graph.networkaccess.conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta) | Defines whether conditional access settings are enabled for traffic profiles in Global Secure Access. Each tenant has only one conditional access settings object. |
| crossTenantAccess | [microsoft.graph.networkaccess.crossTenantAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccesssettings?view=graph-rest-beta) | Defines whether the tenant restrictions cross-tenant access settings are enabled for traffic profiles in Global Secure Access. Each tenant has only one cross-tenant access settings object. |
| forwardingOptions | [microsoft.graph.networkaccess.forwardingOptions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingoptions?view=graph-rest-beta) | Determines how Microsoft 365 traffic through Global Secure Access is forwarded to Azure Front Door. |
| customBlockPage | [microsoft.graph.networkaccess.customBlockPage](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-customblockpage?view=graph-rest-beta) | Custom block page settings define the end user experience when Global Secure Access blocks them from accessing a resource on the web. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.settings",
  "id": "String (identifier)"
}
```
