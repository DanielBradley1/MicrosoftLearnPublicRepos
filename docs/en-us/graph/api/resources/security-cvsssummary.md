<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cvsssummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# cvssSummary resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

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
