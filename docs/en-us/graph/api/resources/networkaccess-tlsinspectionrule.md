<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines a specific rule within a Global Secure Access [TLS inspection policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) that determines whether certain network traffic should be inspected or bypassed based on matching conditions.

Rules are evaluated in order of priority, with the first matching rule's action being applied. If no rules match, the [policy's default action](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicysettings?view=graph-rest-beta) is used.

Inherits from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-list-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) collection | Get a list of the tlsInspectionRule objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) | Create a new tlsInspectionRule object and add it to a policy. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionrule-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) | Get a single tlsInspectionRule object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionrule-update?view=graph-rest-beta) | None | Update the properties of a tlsInspectionRule object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionrule-delete?view=graph-rest-beta) | None | Delete a tlsInspectionRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.tlsInspectionAction | The action to take when traffic matches this rule. The possible values are: `bypass`, `inspect`, `unknownFutureAction`. |
| description | String | Optional description explaining the purpose of the rule. |
| id | String | The unique identifier for the rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| matchingConditions | [microsoft.graph.networkaccess.tlsInspectionMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionmatchingconditions?view=graph-rest-beta) | The conditions that determine when this rule should be applied to traffic. |
| name | String | The display name of the rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`, `startsWith`\). |
| priority | Int64 | The priority of the rule. Rules are evaluated in ascending order of priority. Lower numbers indicate higher priority. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\) and `$orderby`. |
| settings | [microsoft.graph.networkaccess.tlsInspectionRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrulesettings?view=graph-rest-beta) | Additional settings that configure the rule's behavior. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionRule",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "action": "String",
  "priority": "Integer",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.tlsInspectionRuleSettings"
  },
  "matchingConditions": {
    "@odata.type": "microsoft.graph.networkaccess.tlsInspectionMatchingConditions"
  }
}
```
