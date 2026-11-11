<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classificationgradingjobresponse?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# classificationGradingJobResponse resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents classification results for grading. Inherits from `classificationJobResponse` without adding properties.

The inherited **result** retains the existing classification response structure. Eligible matches at `result.classification[].matches[]` use [classificationGradingContentLocation](https://learn.microsoft.com/en-us/graph/api/resources/classificationgradingcontentlocation?view=graph-rest-beta) to include **contextText**.

## Methods

Retrieve the job with `GET /dataClassification/jobs/{job-id}`. For asynchronous requests, follow the returned `Location` URL and poll until the job reaches a terminal status. No separate methods or new permissions are introduced.

## Properties

All properties, including **id**, **status**, **error**, and **result**, are inherited from `classificationJobResponse`. Only the job identifier is expanded below.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The inherited job identifier. |

## Relationships

None.

## JSON representation

This abbreviated representation shows the type and job identifier. The other inherited properties, including **result**, aren't expanded.

```json
{
  "@odata.type": "#microsoft.graph.classificationGradingJobResponse",
  "id": "String (identifier)"
}
```
