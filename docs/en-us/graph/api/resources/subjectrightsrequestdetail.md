<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# subjectRightsRequestDetail resource type

Namespace: microsoft.graph

Represents the details of a subject rights request, including number of items found, number of items reviewed, and so on.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludedItemCount | Int64 | Count of items that are excluded from the request. |
| insightCounts | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) collection | Count of items per insight. |
| itemCount | Int64 | Count of items found. |
| itemNeedReview | Int64 | Count of item that need review. |
| productItemCounts | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) collection | Count of items per product, such as Exchange, SharePoint, OneDrive, and Teams. |
| signedOffItemCount | Int64 | Count of items signed off by the administrator. |
| totalItemSize | Int64 | Total item size in bytes. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectRightsRequestDetail",
      "itemCount": "Int64",
      "totalItemSize": "Int64",
      "itemNeedReview": "Int64",
      "signedOffItemCount": "Int64",
      "excludedItemCount": "Int64",
      "productItemCounts": [],
      "insightCounts": []
}
```
