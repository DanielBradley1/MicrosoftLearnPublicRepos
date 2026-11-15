<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/allresourcesexclusions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# allResourcesExclusions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains exclusions for Conditional Access policies that target all resources. Used by the **allResourcesExclusions** property of [conditionalAccessExclusions](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexclusions?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userActionExclusions | [userActionExclusion](https://learn.microsoft.com/en-us/graph/api/resources/useractionexclusion?view=graph-rest-beta) collection | The user-action exclusions and their states. Supply the complete desired collection when updating it. Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allResourcesExclusions",
  "userActionExclusions": [
    {
      "@odata.type": "microsoft.graph.userActionExclusion"
    }
  ]
}
```
