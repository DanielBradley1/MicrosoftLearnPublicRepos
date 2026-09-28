<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationbucketlocalization?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerPlanConfigurationBucketLocalization resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the localized name of a bucket in a [plannerPlanConfigurationLocalization](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfigurationlocalization?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalBucketId | String | Application-specified identifier of the bucket. |
| name | String | Name of the bucket. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerPlanConfigurationBucketLocalization",
  "externalBucketId": "String",
  "name": "String"
}
```
