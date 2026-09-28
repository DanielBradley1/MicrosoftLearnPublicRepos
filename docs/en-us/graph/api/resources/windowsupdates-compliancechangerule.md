<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# complianceChangeRule resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a rule for governing the automatic creation of compliance changes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the rule was created. |
| lastEvaluatedDateTime | DateTimeOffset | The date and time when the rule was last evaluated. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the rule was last modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.complianceChangeRule",
  "createdDateTime": "String (timestamp)",
  "lastEvaluatedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
