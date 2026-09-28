<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/placeoperationprogress?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# placeOperationProgress resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the progress of an operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedPlaceCount | Int32 | The count of places failed to upsert. |
| succeededPlaceCount | Int32 | The count of places succeeded to upsert. |
| totalPlaceCount | Int32 | The total count of places in the request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.placeOperationProgress",
  "failedPlaceCount": "Int32",
  "succeededPlaceCount": "Int32",
  "totalPlaceCount": "Int32"
}
```
