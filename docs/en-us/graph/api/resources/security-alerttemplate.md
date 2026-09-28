<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# alertTemplate resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the alert that is generated in response to a detection by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta), including the alert metadata, recommended actions, custom details, MITRE tactics, and entity mappings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customDetails | [microsoft.graph.security.alertCustomDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcustomdetails?view=graph-rest-beta) | Custom key-value detail pairs to include in the alert. Each value identifies the detection query column that supplies the corresponding custom detail. |
| description | String | Description of the alert triggered by the custom detection rule. |
| entityMappings | [microsoft.graph.security.entityMappingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymappingconfiguration?view=graph-rest-beta) | Defines how detection query columns map to the entities that are attached to the resulting alert. |
| recommendedActions | String | Recommended actions to mitigate the threat related to the alert triggered by the custom detection rule. |
| severity | [microsoft.graph.security.alertSeverity](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-beta#alertseverity-values) | Severity assigned to the alert triggered by the custom detection rule. The possible values are: `informational`, `low`, `medium`, `high`. |
| tactics | [microsoft.graph.security.mitreTactic](https://learn.microsoft.com/en-us/graph/api/resources/security-mitretactic?view=graph-rest-beta) collection | The MITRE ATT&CK tactics framing for this alert. |
| title | String | Name of the alert triggered by the custom detection rule. |
| category \(deprecated\) | String | Indicates the category assigned to the alert triggered by the custom detection rule. **Deprecated.** Use **tactics** instead. This property will be removed from this resource on 2026-10-01. |
| impactedAssets \(deprecated\) | [microsoft.graph.security.impactedAsset](https://learn.microsoft.com/en-us/graph/api/resources/security-impactedasset?view=graph-rest-beta) collection | Indicates the impacted assets for the alert triggered by the custom detection rule. **Deprecated.** Use **entityMappings** instead. This property will be removed from this resource on 2026-10-01. |
| mitreTechniques \(deprecated\) | String collection | Indicates the MITRE techniques assigned to the alert triggered by the custom detection rule. **Deprecated.** Use **tactics** instead. This property will be removed from this resource on 2026-10-01. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.alertTemplate",
  "title": "String",
  "description": "String",
  "severity": "String",
  "category": "String",
  "recommendedActions": "String",
  "entityMappings":  {
    "@odata.type": "microsoft.graph.security.entityMappingConfiguration"
  },
  "mitreTechniques": [
    "String"
  ],
  "tactics": [
    {
      "@odata.type": "microsoft.graph.security.mitreTactic"
    }
  ],
  "impactedAssets": [
    {
      "@odata.type": "microsoft.graph.security.impactedUserAsset"
    }
  ],
  "customDetails": {
    "@odata.type": "microsoft.graph.security.alertCustomDetails"
  }
}
```
