<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-remediationupdatefilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# remediationUpdateFilter resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a filter to determine which remediation update content matches the rule continuously.

Inherits from [windowsUpdateFilter](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-windowsupdatefilter?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| remediationType | microsoft.graph.windowsUpdates.remediationType | The type of remediation content that is offered to the device. The possible values are: `inPlaceUpgrade`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.remediationUpdateFilter",
  "remediationType": "String"
}
```
