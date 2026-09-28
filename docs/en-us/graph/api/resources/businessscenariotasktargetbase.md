<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotasktargetbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# businessScenarioTaskTargetBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a base object for all targets that can be specified for creating tasks for a scenario.

Base type of [businessScenarioGroupTarget](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariogrouptarget?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| taskTargetKind | plannerTaskTargetKind | Represents the kind of the target. The possible values are: `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenarioTaskTargetBase",
  "taskTargetKind": "String"
}
```
