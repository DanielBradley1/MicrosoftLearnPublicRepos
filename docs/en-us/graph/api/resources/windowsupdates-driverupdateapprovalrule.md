<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdateapprovalrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# driverUpdateApprovalRule resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an automatic approval rule for driver and firmware update content. The rule controls how long matching content is deferred before approval. The **approvalRules** property of a [driverUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatepolicy?view=graph-rest-beta) resource can contain this type.

Inherits from [approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deferralInDays | Int32 | The number of days to wait before matching driver and firmware update content is approved. Inherited from [approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateApprovalRule",
  "deferralInDays": "Int32"
}
```
