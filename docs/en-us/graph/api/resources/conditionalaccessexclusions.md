<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexclusions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# conditionalAccessExclusions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the exclusions configuration in the **exclusions** property of [conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allResourcesExclusions | [allResourcesExclusions](https://learn.microsoft.com/en-us/graph/api/resources/allresourcesexclusions?view=graph-rest-beta) | The exclusions for Conditional Access policies that target all resources. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessExclusions",
  "allResourcesExclusions": {
    "@odata.type": "microsoft.graph.allResourcesExclusions"
  }
}
```
