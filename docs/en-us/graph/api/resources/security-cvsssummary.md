<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cvsssummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# cvssSummary resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

Represents a common vulnerability scoring system \(CVSS\) evaluation of a vulnerability.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| score | Edm.Double | The CVSS score about this vulnerability. |
| severity | microsoft.graph.security.vulnerabilitySeverity | The CVSS severity rating for this vulnerability. The possible values are: `none`, `low`, `medium`, `high`, `critical`, `unknownFutureValue`. |
| vectorString | String | The CVSS vector string for this vulnerability. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.cvssSummary",
  "score": "Double",
  "severity": "String",
  "vectorString": "String"
}
```
