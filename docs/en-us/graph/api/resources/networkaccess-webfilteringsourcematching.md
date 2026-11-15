<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringsourcematching?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# webFilteringSourceMatching resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the source session criteria used to match web traffic in a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

This type is used by the **sources** property of [webFilteringMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringmatchingconditions?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sessionType | [microsoft.graph.networkaccess.sessionType](https://learn.microsoft.com/en-us/graph/api/resources/enums-networkaccess?view=graph-rest-beta#sessiontype-values) | The type of session to match. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `user`, `agent`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringSourceMatching",
  "sessionType": "String"
}
```
