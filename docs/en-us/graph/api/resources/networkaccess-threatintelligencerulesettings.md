<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerulesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# threatIntelligenceRuleSettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configurable settings that define how a [threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) operates. These settings control the operational status of the rule and how the rule is enforced.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | microsoft.graph.networkaccess.securityRuleStatus | The operational status of the threat intelligence rule that determines whether it is enforced. The possible values are: `enabled` \(rule is active and enforced\), `disabled` \(rule is inactive\), `reportOnly` \(rule evaluates traffic but only logs without enforcing actions\), `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceRuleSettings",
  "status": "String"
}
```
