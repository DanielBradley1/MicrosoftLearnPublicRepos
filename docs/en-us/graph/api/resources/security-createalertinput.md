<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-createalertinput?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# createAlertInput resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Input parameters for the [createAlert](https://learn.microsoft.com/en-us/graph/api/security-alert-createalert?view=graph-rest-beta) action, including alert metadata and inline entity definitions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | String | MITRE ATT&CK category for the alert. |
| description | String | Free-text explanation of the suspicious activity or policy violation. |
| entityDefinitions | [microsoft.graph.security.entityDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-entitydefinition?view=graph-rest-beta) collection | Inline entity definitions that associate entities with the alert. |
| isExcludedFromCorrelation | Boolean | Whether the alert is excluded from automatic correlation. Defaults to `false`. |
| linkToIncident | Int64 | Incident ID to link the alert to. Use `0` or omit the value to create a new incident. |
| mitreTechniques | String collection | MITRE ATT&CK technique identifiers associated with the alert. |
| recommendedActions | String | Recommended remediation actions for the alert. |
| sentinelWorkspace | String | Microsoft Sentinel workspace identifier used for workspace routing. |
| severity | [microsoft.graph.security.alertSeverity](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#alertseverity-values) | Severity level of the alert. The possible values are: `unknown`, `informational`, `low`, `medium`, `high`, `unknownFutureValue`. |
| title | String | Short display name shown for the alert in the Defender portal. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.createAlertInput",
  "category": "String",
  "description": "String",
  "entityDefinitions": [
    {
      "@odata.type": "microsoft.graph.security.entityDefinition"
    }
  ],
  "isExcludedFromCorrelation": "Boolean",
  "linkToIncident": "Int64",
  "mitreTechniques": ["String"],
  "recommendedActions": "String",
  "sentinelWorkspace": "String",
  "severity": "String",
  "title": "String"
}
```
