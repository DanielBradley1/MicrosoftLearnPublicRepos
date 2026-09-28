<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# cloudFirewallRule resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a firewall rule that defines conditions and actions for network traffic filtering within a [cloud firewall policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta). Each rule specifies matching conditions for source and destination addresses, ports, and protocols, along with an action to take when traffic matches the conditions.

Inherits from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallpolicy-list-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) collection | Get a list of the cloudFirewallRule objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallpolicy-post-policyrules?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) | Create a new cloudFirewallRule object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallrule-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.cloudFirewallRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrule?view=graph-rest-beta) | Read the properties and relationships of a cloudFirewallRule object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallrule-update?view=graph-rest-beta) | None | Update the properties of a cloudFirewallRule object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-cloudfirewallrule-delete?view=graph-rest-beta) | None | Delete a cloudFirewallRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.cloudFirewallAction | The action to take when traffic matches the rule conditions. The possible values are: `allow`, `block`, `unknownFutureValue`. Required. |
| description | String | A human-readable description of the rule's purpose. Optional. |
| id | String | A unique identifier for the rule. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Key. Not nullable. Read-only. |
| matchingConditions | [microsoft.graph.networkaccess.cloudFirewallMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallmatchingconditions?view=graph-rest-beta) | The conditions that network traffic must match for the rule to apply. Required. |
| name | String | A unique display name for the rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). Required. |
| priority | Int64 | A unique priority value that determines the rule evaluation order; lower values are evaluated first. Required. |
| settings | [microsoft.graph.networkaccess.cloudFirewallRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallrulesettings?view=graph-rest-beta) | Configuration settings for the rule, including the enabled or disabled status. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallRule",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "priority": "Integer",
  "action": "String",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.cloudFirewallRuleSettings"
  },
  "matchingConditions": {
    "@odata.type": "microsoft.graph.networkaccess.cloudFirewallMatchingConditions"
  }
}
```
