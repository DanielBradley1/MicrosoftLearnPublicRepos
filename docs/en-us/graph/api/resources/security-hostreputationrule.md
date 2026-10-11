<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputationrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-06 -->

# hostReputationRule resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

Represents a rule that is used \(in combination with other rules\) to determine the reputation of a [hostname](https://learn.microsoft.com/en-us/graph/api/resources/security-hostname?view=graph-rest-1.0) or [IP address](https://learn.microsoft.com/en-us/graph/api/resources/security-ipaddress?view=graph-rest-1.0). Each **hostReputationRule** only applies within the parent [hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the rule that gives more context. |
| relatedDetailsUrl | String | Link to a web page with details related to this rule. |
| name | String | The name of the rule. |
| severity | microsoft.graph.security.hostReputationRuleSeverity | Indicates the severity that this rule has against the reputation score. The possible values are: `unknown`, `low`, `medium`, `high`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostReputationRule",
  "description": "String",
  "name": "String",
  "relatedDetailsUrl": "String",
  "severity": "String"
}
```
