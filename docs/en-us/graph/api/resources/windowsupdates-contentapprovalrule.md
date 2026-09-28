<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapprovalrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# contentApprovalRule resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a rule for governing the automatic creation of content approvals.

Inherits from [complianceChangeRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentFilter | [microsoft.graph.windowsUpdates.contentFilter](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentfilter?view=graph-rest-beta) | A filter to determine which content matches the rule on an ongoing basis. |
| createdDateTime | DateTimeOffset | The date and time when the rule was created. Inherited from [microsoft.graph.windowsUpdates.complianceChangeRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta). |
| durationBeforeDeploymentStart | Duration | The time before the deployment starts represented in ISO 8601 format for durations. |
| lastEvaluatedDateTime | DateTimeOffset | The date and time when the rule was last evaluated. Inherited from [microsoft.graph.windowsUpdates.complianceChangeRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the rule was last modified. Inherited from [microsoft.graph.windowsUpdates.complianceChangeRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.contentApprovalRule",
  "contentFilter": {
    "@odata.type": "microsoft.graph.windowsUpdates.contentFilter"
  },
  "createdDateTime": "String (timestamp)",
  "durationBeforeDeploymentStart": "String (duration)",
  "lastEvaluatedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
