<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdateapprovalrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# qualityUpdateApprovalRule resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the quality update approval deployment rules.

Inherits from [approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cadence | microsoft.graph.windowsUpdates.qualityUpdateCadence | Indicates the frequency and rhythm at which updates are delivered and installed. The possible values are: `monthly`, `outOfBand`, `unknownFutureValue`. |
| classification | microsoft.graph.windowsUpdates.qualityUpdateClassification | The quality update classification type. The possible values are: `all`, `security`, `nonSecurity`, `unknownFutureValue`. |
| deferralInDays | Int32 | The quality update deferral period in days. The value must be between `0` and `30`. Inherited from [microsoft.graph.windowsUpdates.approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateApprovalRule",
  "cadence": "String",
  "classification": "String",
  "deferralInDays": "Int32"
}
```
