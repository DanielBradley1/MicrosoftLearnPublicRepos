<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# alertTemplate resource type

Namespace: microsoft.graph.security

Describes the alert that is generated in response to a detection by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0), including the alert metadata, recommended actions, custom details, MITRE tactics, and entity mappings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customDetails | [microsoft.graph.security.alertCustomDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcustomdetails?view=graph-rest-1.0) | Custom key-value detail pairs to include in the alert. Each value identifies the detection query column that supplies the corresponding custom detail. |
| description | String | Description of the alert triggered by the custom detection rule. |
| entityMappings | [microsoft.graph.security.entityMappingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymappingconfiguration?view=graph-rest-1.0) | Defines how detection query columns map to the entities that are attached to the resulting alert. |
| recommendedActions | String | Recommended actions to mitigate the threat related to the alert triggered by the custom detection rule. |
| severity | [microsoft.graph.security.alertSeverity](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0#alertseverity-values) | Severity assigned to the alert triggered by the custom detection rule. The possible values are: `informational`, `low`, `medium`, `high`. |
| tactics | [microsoft.graph.security.mitreTactic](https://learn.microsoft.com/en-us/graph/api/resources/security-mitretactic?view=graph-rest-1.0) collection | The MITRE ATT&CK tactics framing for this alert. |
| title | String | Name of the alert triggered by the custom detection rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.alertTemplate",
  "customDetails": {
    "@odata.type": "microsoft.graph.security.alertCustomDetails"
  },
  "description": "String",
  "entityMappings": {
    "@odata.type": "microsoft.graph.security.entityMappingConfiguration"
  },
  "recommendedActions": "String",
  "severity": "String",
  "tactics": [
    {
      "@odata.type": "microsoft.graph.security.mitreTactic"
    }
  ],
  "title": "String"
}
```
