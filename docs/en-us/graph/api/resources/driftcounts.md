<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driftcounts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# driftCounts resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the aggregate counts of access drift for a governed resource.

This object is configured in the **driftCounts** property of [accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| missing | Int32 | The number of assignments that are expected but not present on the resource. |
| total | Int32 | The total number of unauthorized and missing access assignments. |
| unauthorized | Int32 | The number of assignments that exist on the resource but are not expected. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driftCounts",
  "total": "Int32",
  "unauthorized": "Int32",
  "missing": "Int32"
}
```
