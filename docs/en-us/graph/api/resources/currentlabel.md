<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/currentlabel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-14 -->

# currentLabel resource type

Namespace: microsoft.graph

Represents caller-supplied sensitivity label metadata in the **sensitivityLabels** collection of [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-1.0) and its derived types.

This type describes label metadata. It doesn't provide operations to apply, remove, or manage sensitivity labels.

When you supply more than one label, include a separate object for each label in the **sensitivityLabels** collection. The collection isn't a single object or a string of comma-separated label identifiers.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationMode | [applicationMode](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#applicationmode-values) | The application mode associated with the sensitivity label. The possible values are: `manual`, `automatic`, `recommended`, `unknownFutureValue`. |
| id | String | The GUID that identifies the sensitivity label. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.currentLabel",
  "id": "String",
  "applicationMode": "String"
}
```
