<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalbucketsource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# plannerExternalBucketSource resource type

Namespace: microsoft.graph

Contains information about the relationship of a [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-beta) to a user experience outside of Planner. This allows surfacing or syncing buckets in Planner with other experiences to track work in the context of that experience.

You can display data in a **plannerExternalBucketSource** in a user interface to sync information for an external service, or to point to where a task was created in the external service.

The combination of the **contextScenarioId** and **externalObjectId** properties is unique within a tenant. If creation is called with existing **contextScenarioId** and **externalObjectId** values, the existing object is returned with no modifications.

This type is derived from [plannerBucketCreation](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucketcreation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| creationSourceKind | plannerCreationSourceKind | Specifies what kind of creation source the bucket is created with. The possible values are: `external`, `publication` and `unknownFutureValue`. The value of this property is `external`. Inherited from [plannerBucketCreation](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucketcreation?view=graph-rest-beta). |
| contextScenarioId | String | Nullable. An identifier for the scenario associated with this external source. This should be in reverse DNS format. For example, Contoso company owned application for customer support would have a value like "com.constoso.customerSupport". |
| externalObjectId | String | Nullable. The ID of the entity that an external service associates with a bucket. |
| externalContextId | String | Nullable. The ID of the external entity's containing entity or context. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerExternalBucketSource",
  "creationSourceKind": "String-value",
  "externalObjectId": "String-value",
  "externalContextId": "String-value",
  "contextScenarioId": "String-value",
}
```
