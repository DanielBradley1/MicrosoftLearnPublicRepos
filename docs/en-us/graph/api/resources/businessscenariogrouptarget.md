<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenariogrouptarget?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# businessScenarioGroupTarget resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) which will be used as the target when creating tasks in a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta).

Inherits from [businessScenarioTaskTargetBase](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotasktargetbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupId | String | The unique identifier for the group. |
| taskTargetKind | plannerTaskTargetKind | Represents the kind of the target. The possible values are: `group`, `unknownFutureValue`. The value of this property will be `group`. Inherited from [businessScenarioTaskTargetBase](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotasktargetbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenarioGroupTarget",
  "groupId": "String",
  "taskTargetKind": "String"
}
```
