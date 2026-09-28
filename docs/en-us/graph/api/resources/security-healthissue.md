<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-13 -->

# healthIssue resource type

Namespace: microsoft.graph.security

Represents potential issues identified by Microsoft Defender for Identity within a customer's Microsoft Defender for Identity configuration.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-healthissues?view=graph-rest-1.0) | [microsoft.graph.security.healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) collection | Get a list of [healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-healthissue-get?view=graph-rest-1.0) | [microsoft.graph.security.healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) | Read the properties and relationships of a [healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-healthissue-update?view=graph-rest-1.0) | [microsoft.graph.security.healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) | Update the properties of a [healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalInformation | String collection | Contains additional information about the issue, such as a list of items to fix. |
| createdDateTime | DateTimeOffset | The date and time when the health issue was generated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | Contains more detailed information about the health issue. |
| displayName | String | The display name of the health issue. |
| domainNames | String collection | A list of the fully qualified domain names of the domains or the sensors the health issue is related to. |
| healthIssueType | [microsoft.graph.security.healthIssueType](#healthissuetype-values) | The type of the health issue. The possible values are: `sensor`, `global`, `unknownFutureValue`. For a list of all health issues and their identifiers, see [Microsoft Defender for Identity health issues](https://learn.microsoft.com/en-us/defender-for-identity/health-alerts). |
| id | String | A unique identifier that represents the health issue. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| issueTypeId | String | The type identifier of the health issue. For a list of all health issues and their identifiers, see [Microsoft Defender for Identity health issues](https://learn.microsoft.com/en-us/defender-for-identity/health-alerts). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the health issue was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| recommendations | String collection | A list of recommended actions that can be taken to resolve the issue effectively and efficiently. These actions might include instructions for further investigation and aren't limited to prewritten responses. |
| recommendedActionCommands | String collection | A list of commands from the PowerShell module for the product that can be used to resolve the issue, if available. If no commands can be used to solve the issue, this property is empty. The commands, if present, provide a quick and efficient way to address the issue. These commands run in sequence for the single recommended fix. |
| sensorDNSNames | String collection | A list of the DNS names of the sensors the health issue is related to. |
| severity | [microsoft.graph.security.healthIssueSeverity](#healthissueseverity-values) | The severity of the health issue. The possible values are: `low`, `medium`, `high`, `unknownFutureValue`. |
| status | [microsoft.graph.security.healthIssueStatus](#healthissuestatus-values) | The status of the health issue. The possible values are: `open`, `closed`, `suppressed`, `unknownFutureValue`. |

### healthIssueSeverity values

| Member | Description |
| :--- | :--- |
| low | Low severity health issues usually indicate minor issues that don't have a significant impact on your environment. These issues require further investigation, but they usually don't require immediate action. |
| medium | Medium severity health issues indicate more significant issues that could potentially impact your environment. These issues may require further investigation and action to prevent any potential problems. |
| high | High severity health issues indicate critical issues that could have a severe impact on your environment. These issues require immediate attention and action. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### healthIssueStatus values

| Member | Description |
| :--- | :--- |
| open | The issue is open and should be addressed. |
| closed | The issue was addressed. Either someone manually closed the issue or took an action on the affected item, or it was closed automatically by the system. |
| suppressed | The operator suppressed the issue manually. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### healthIssueType values

| Member | Description |
| :--- | :--- |
| sensor | The issue is on specific sensor. |
| global | The issue is in the Defender for Identity system configuration. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.healthIssue",
  "additionalInformation": ["String"],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "domainNames": ["String"],
  "healthIssueType": "String",
  "id": "String (identifier)",
  "issueTypeId": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "recommendations": ["String"],
  "recommendedActionCommands": ["String"],
  "sensorDNSNames": ["String"],
  "severity": "String",
  "status": "String"
}
```
