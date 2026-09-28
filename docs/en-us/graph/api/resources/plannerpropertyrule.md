<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerpropertyrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerPropertyRule resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract base type of all entity rule definitions for Microsoft Planner.

Base type of [plannerTaskPropertyRule](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpropertyrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ruleKind | plannerRuleKind | Identifies which type of property rules is represented by this instance. The possible values are: `taskRule`, `bucketRule`, `planRule`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerPropertyRule",
  "ruleKind": "String"
}
```
