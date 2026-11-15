<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringwebcategorydestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringWebCategoryDestination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents web category values used as destination targets in a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.webFilteringDestinationTarget](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationtarget?view=graph-rest-beta).

Instances of this type can be included in the **targets** collection property of [webFilteringDestinationMatching](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationmatching?view=graph-rest-beta), whose element type is [webFilteringDestinationTarget](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationtarget?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| values | String collection | The web category identifiers to match. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringWebCategoryDestination",
  "values": [
    "String"
  ]
}
```
