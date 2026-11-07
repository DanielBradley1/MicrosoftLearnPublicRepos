<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# detectionAction resource type

Namespace: microsoft.graph.security

Describes the actions that are taken after a detection is made by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0), including the alert that is created and any automated actions that run against impacted entities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertTemplate | [microsoft.graph.security.alertTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-1.0) | The template that defines the alert that is generated when this rule detects a match, including alert metadata \(severity, title, description\), entity mappings, custom details, and MITRE tactics. |
| automatedActions | [microsoft.graph.security.automatedActionSet](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedactionset?view=graph-rest-1.0) | The set of automated actions to run against entities that match the detection. |
| organizationalScope | [microsoft.graph.security.organizationalScope](https://learn.microsoft.com/en-us/graph/api/resources/security-organizationalscope?view=graph-rest-1.0) | The set of groups \(for example, device groups\) to which the parent custom detection rule applies. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.detectionAction",
  "alertTemplate": {
    "@odata.type": "microsoft.graph.security.alertTemplate"
  },
  "automatedActions": {
    "@odata.type": "microsoft.graph.security.automatedActionSet"
  },
  "organizationalScope": {
    "@odata.type": "microsoft.graph.security.organizationalScope"
  }
}
```
