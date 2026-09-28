<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerbucketcreation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerBucketCreation resource type

Namespace: microsoft.graph

The resources that derive from plannerBucketCreation contain information about the origin of the [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-beta). Apps do not need to know the origin of the bucket to be able to work with it; however, some apps can use the additional information to provide specific experiences around these buckets. This is the abstract base type of [plannerExternalBucketSource](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalbucketsource?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| creationSourceKind | plannerCreationSourceKind | Specifies what kind of creation source the bucket is created with. The possible values are: `external`, `publication` and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerBucketCreation",
  "creationSourceKind": "String-value"
}
```
