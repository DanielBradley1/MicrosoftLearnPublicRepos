<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringPolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines a set of web filtering rules and the default action that Global Secure Access applies to traffic that does not match a rule.

Inherits from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-webfilteringpolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) collection | Get a list of the webFilteringPolicy objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-post-webfilteringpolicies?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) | Create a new webFilteringPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicy-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicy-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicy?view=graph-rest-beta) | Update the properties of a webFilteringPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-delete-webfilteringpolicies?view=graph-rest-beta) | None | Delete a webFilteringPolicy object. |
| [List policyRules](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicy-list-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) collection | Get the rules associated with the web filtering policy. |
| [Create policyRule](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) | Create a new webFilteringRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the web filtering policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| id | String | The unique identifier for the web filtering policy. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the web filtering policy was last modified. Read-only. |
| name | String | The display name of the web filtering policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| settings | [microsoft.graph.networkaccess.webFilteringPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringpolicysettings?view=graph-rest-beta) | The default settings for the web filtering policy. |
| version | String | The version of the web filtering policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) collection | The rules evaluated as part of the policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringPolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringPolicySettings"
  }
}
```
