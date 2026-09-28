<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencematchingconditions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# threatIntelligenceMatchingConditions resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the conditions used to evaluate and match against potential threats in network traffic. These conditions define what network destinations should be considered threats and how they should be evaluated based on severity levels. Parent resource [threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) consumes this complex type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinations | [microsoft.graph.networkaccess.threatIntelligenceDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencedestination?view=graph-rest-beta) collection | A collection of destinations that are considered potential threats for network access evaluation. |
| severity | microsoft.graph.networkaccess.threatIntelligenceSeverity | The severity level of the threat associated with the destinations. Higher severity levels typically result in stricter security controls. The possible values are: `low`, `medium`, `high`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceMatchingConditions",
  "severity": "String",
  "destinations": [
    {
      "@odata.type": "microsoft.graph.networkaccess.threatIntelligenceFqdnDestination"
    }
  ]
}
```
