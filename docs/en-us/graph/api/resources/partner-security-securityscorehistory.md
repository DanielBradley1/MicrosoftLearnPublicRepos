<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# securityScoreHistory resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single history entry for the security score where the score or the requirements changed.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/partner-security-partnersecurityscore-list-history?view=graph-rest-beta) | [microsoft.graph.partner.security.securityScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta) collection | Get a list of [securityScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/partner-security-securityscorehistory-get?view=graph-rest-beta) | [microsoft.graph.partner.security.securityScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta) | Read the properties and relationships of a [securityScoreHistory](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityscorehistory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliantRequirementsCount | Int64 | The number of compliant security requirements at the time. |
| createdDateTime | DateTimeOffset | The date the history entry was created. |
| id | String | The unique identifier for the history entry. |
| score | Double | The score recorded at the time. |
| totalRequirementsCount | Int64 | The total number of requirements at the time. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.securityScoreHistory",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "score": "Double",
  "compliantRequirementsCount": "Integer",
  "totalRequirementsCount": "Integer"
}
```
