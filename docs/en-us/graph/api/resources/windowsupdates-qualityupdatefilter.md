<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatefilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# qualityUpdateFilter resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a filter to determine which quality update content matches the rule on an ongoing basis.

Inherits from [windowsUpdateFilter](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-windowsupdatefilter?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cadence | microsoft.graph.windowsUpdates.qualityUpdateCadence | Specifies the cadence for publishing quality updates of the filter. The possible values are: `monthly`, `outOfBand`, `unknownFutureValue`. |
| classification | microsoft.graph.windowsUpdates.qualityUpdateClassification | Specifies the quality update classification of the filter. The possible values are: `all`, `security`, `nonSecurity`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateFilter", 
  "cadence": "String",
  "classification": "String"
}
```
