<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# forwardingPolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A forwarding policy defines the specific traffic that is routed through the Global Secure Access services. It's then added to a [forwarding profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingpolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingpolicy-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) object. |
| [Update policy rules](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingpolicy-updatepolicyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) | Update the rules within a forwarding policy. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Forwarding policy description. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| id | String | Identifier for the forwarding policy. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| name | String | Forwarding policy name. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| trafficForwardingType | microsoft.graph.networkaccess.trafficForwardingType | Traffic type for forwarding policy. The possible values are: `m365`, `internet`, `private`. |
| version | String | Forwarding policy version. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) collection | Represents the definition of the policy ruleset that makes up the core definition of a policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "version": "String",
  "trafficForwardingType": "String"
}
```
