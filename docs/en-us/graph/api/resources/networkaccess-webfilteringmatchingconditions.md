<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringmatchingconditions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringMatchingConditions resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the source and destination conditions used to determine whether web traffic matches a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

This type is used by the **matchingConditions** property of [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinations | [microsoft.graph.networkaccess.webFilteringDestinationMatching](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationmatching?view=graph-rest-beta) | The destination criteria to match. |
| sources | [microsoft.graph.networkaccess.webFilteringSourceMatching](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringsourcematching?view=graph-rest-beta) | The source session criteria to match. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringMatchingConditions",
  "destinations": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringDestinationMatching"
  },
  "sources": {
    "@odata.type": "microsoft.graph.networkaccess.webFilteringSourceMatching"
  }
}
```
