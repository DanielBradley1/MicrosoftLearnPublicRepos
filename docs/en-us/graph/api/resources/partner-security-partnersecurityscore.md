<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# partnerSecurityScore resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the security score for the partner which helps Cloud Solution Provider \(CSP\) partners understand their security posture and their customer's security posture. The score includes an aggregate score along with history of score changes, detailed customer insights, and requirement score information.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-get?view=graph-rest-beta) | [microsoft.graph.partner.security.partnerSecurityScore](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta) | Read the properties and relationships of a [partnerSecurityScore](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityscore?view=graph-rest-beta) object. |
| [List customer insights](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-customerinsights?view=graph-rest-beta) | [microsoft.graph.partner.security.customerInsight](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customerinsight?view=graph-rest-beta) collection | Get a list of the **customerInsight** data to learn more about the partner's customer security posture. |
| [List history](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-history?view=graph-rest-beta) | [microsoft.graph.partner.security.securityScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta) collection | Lists the history of security score changes for the partner.. |
| [List requirements](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-requirements?view=graph-rest-beta) | [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta) collection | Get the security requirement resources from the **requirements** navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentScore | Single | The current security score for the partner. |
| lastRefreshDateTime | DateTimeOffset | The last time the data was checked. |
| maxScore | Single | The maximum score possible. |
| updatedDateTime | DateTimeOffset | The last time the security score or related properties changed. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customerInsights | [microsoft.graph.partner.security.customerInsight](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customerinsight?view=graph-rest-beta) collection | Contains customer-specific information for certain requirements. |
| history | [microsoft.graph.partner.security.securityScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta) collection | Contains a list of recent score changes. |
| requirements | [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta) collection | Contains the list of security requirements that make up the score. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.partnerSecurityScore",
  "updatedDateTime": "String (timestamp)",
  "lastRefreshDateTime": "String (timestamp)",
  "currentScore": "Single",
  "maxScore": "Single"
}
```
