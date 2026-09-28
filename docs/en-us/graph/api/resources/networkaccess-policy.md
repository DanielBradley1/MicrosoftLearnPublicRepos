<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# policy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A traffic forwarding policy consists of a policy and its associated rules. It defines the guidelines and instructions for routing and handling network traffic.

It's an abstract type from which the following resources are derived:

- [microsoft.graph.networkaccess.cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta)
- [microsoft.graph.networkaccess.filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta)
- [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta)
- [microsoft.graph.networkaccess.threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta)

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description. |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| name | String | Policy name. |
| version | String | Version. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) collection | Represents the definition of the policy ruleset that makes up the core definition of a policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.policy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "version": "String"
}
```
