<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# detectionAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the actions that are taken after a detection is made by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta), including the alert that is created and any automated actions that run against impacted entities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alertTemplate | [microsoft.graph.security.alertTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-beta) | The template that defines the alert that is generated when this rule detects a match, including alert metadata \(severity, title, description\), entity mappings, custom details, and MITRE tactics. |
| automatedActions | [microsoft.graph.security.automatedActionSet](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedactionset?view=graph-rest-beta) | The set of automated actions to run against entities that match the detection. Replaces the deprecated **responseActions** property. |
| organizationalScope | [microsoft.graph.security.organizationalScope](https://learn.microsoft.com/en-us/graph/api/resources/security-organizationalscope?view=graph-rest-beta) | The set of groups \(for example, device groups\) to which the parent custom detection rule applies. |
| responseActions \(deprecated\) | [microsoft.graph.security.responseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-responseaction?view=graph-rest-beta) collection | Actions taken on impacted assets as set in the custom detection rule. **Deprecated.** Use **automatedActions** instead. This property will be removed from this resource on 2026-10-01. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.detectionAction",
  "organizationalScope": {
    "@odata.type": "microsoft.graph.security.organizationalScope"
  },
  "automatedActions": {
    "@odata.type": "microsoft.graph.security.automatedActionSet"
  },
  "alertTemplate": {
    "@odata.type": "microsoft.graph.security.alertTemplate"
  }
}
```
