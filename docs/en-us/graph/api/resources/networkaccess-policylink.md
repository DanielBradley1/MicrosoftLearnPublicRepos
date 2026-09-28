<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# policyLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This is an abstract type from which the following resource types are derived:

- [cloudFirewallPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicylink?view=graph-rest-beta)
- [filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta)
- [forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta)
- [threatIntelligencePolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicylink?view=graph-rest-beta)
- [tlsInspectionPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicylink?view=graph-rest-beta)

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | microsoft.graph.networkaccess.status | Link status. The possible values are: `enabled`, `disabled`. |
| version | String | Version. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) | Policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.policyLink",
  "id": "String (identifier)",
  "state": "String",
  "version": "String"
}
```
