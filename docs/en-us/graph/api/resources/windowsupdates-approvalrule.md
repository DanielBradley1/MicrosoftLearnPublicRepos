<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# approvalRule resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents an entity that governs the overall Windows update approval deployment rules.

Base type of [qualityUpdateApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdateapprovalrule?view=graph-rest-beta) and [recoveryApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-recoveryapprovalrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deferralInDays | Int32 | The Windows update deferral period in days. The value must be between `0` and `30`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.approvalRule",
  "deferralInDays": "Int32"
}
```
