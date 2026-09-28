<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioproperties?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# businessScenarioProperties resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents scenario metadata for a [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalBucketId | String | The identifier for the [bucketDefinition](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationbucketdefinition?view=graph-rest-beta) configured in the [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) for the scenario. The task will be placed in the corresponding [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-beta) in the target plan. Required. |
| externalContextId | String | The identifier for the context of the task. Context is an application controlled value, and tasks can be queried by their **externalContextId**. Optional. |
| externalObjectId | String | Application-specific identifier for the task. Every task for the same scenario must have a unique identifier specified for this property. Required. |
| externalObjectVersion | String | Application-specific version of the task. Optional. |
| webUrl | String | The URL to the application-specific experience for this task. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.businessScenarioProperties",
  "externalBucketId": "String",
  "externalContextId": "String",
  "externalObjectId": "String",
  "externalObjectVersion": "String",
  "webUrl": "String"
}
```
