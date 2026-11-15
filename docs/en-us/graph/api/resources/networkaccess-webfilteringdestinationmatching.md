<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationmatching?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringDestinationMatching resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the destination criteria used to match web traffic in a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

This type is used by the **destinations** property of [webFilteringMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringmatchingconditions?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| httpRequestMethod | [microsoft.graph.networkaccess.httpRequestMethod](https://learn.microsoft.com/en-us/graph/api/resources/enums-networkaccess?view=graph-rest-beta#httprequestmethod-values) | The HTTP request method to match. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `get`, `post`, `patch`, `put`, `delete`, `unknownFutureValue`. |
| targets | [microsoft.graph.networkaccess.webFilteringDestinationTarget](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringdestinationtarget?view=graph-rest-beta) collection | The URL or web category destinations to match. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringDestinationMatching",
  "targets": [
    {
      "@odata.type": "microsoft.graph.networkaccess.webFilteringWebCategoryDestination"
    }
  ],
  "httpRequestMethod": "String"
}
```
