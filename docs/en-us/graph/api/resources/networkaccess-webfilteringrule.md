<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a rule that evaluates web traffic against source and destination matching conditions and applies an allow or block action.

Inherits from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicy-list-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) collection | Get a list of the webFilteringRule objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringpolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) | Create a new webFilteringRule object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringrule-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringrule-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) | Update the properties of a webFilteringRule object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringrule-delete?view=graph-rest-beta) | None | Delete a webFilteringRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.networkaccess.webFilteringAction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringaction?view=graph-rest-beta) | The action to apply when the rule matches web traffic. |
| description | String | The description of the web filtering rule. |
| id | String | The unique identifier for the web filtering rule. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| matchingConditions | [microsoft.graph.networkaccess.webFilteringMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringmatchingconditions?view=graph-rest-beta) | The source and destination conditions that determine whether traffic matches the rule. |
| name | String | The display name of the web filtering rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| priority | Int64 | The processing order of the rule within its policy. Rules with lower values are evaluated first. |
| settings | [microsoft.graph.networkaccess.webFilteringRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrulesettings?view=graph-rest-beta) | The enforcement settings for the web filtering rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringRule",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "action": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringAction"
  },
  "priority": "Integer",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringRuleSettings"
  },
  "matchingConditions": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringMatchingConditions"
  }
}
```
