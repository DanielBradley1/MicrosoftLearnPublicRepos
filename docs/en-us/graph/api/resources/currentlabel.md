<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/currentlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# currentLabel resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents caller-supplied sensitivity label metadata in the **sensitivityLabels** collection of [processContentMetadataBase](https://learn.microsoft.com/en-us/graph/api/resources/processcontentmetadatabase?view=graph-rest-beta) and its derived types.

This type describes label metadata. It doesn't provide operations to apply, remove, or manage sensitivity labels.

When you supply more than one label, include a separate object for each label in the **sensitivityLabels** collection. The collection isn't a single object or a string of comma-separated label identifiers.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationMode | [applicationMode](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#applicationmode-values) | The application mode associated with the sensitivity label. The possible values are: `manual`, `automatic`, `recommended`, `unknownFutureValue`. |
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
