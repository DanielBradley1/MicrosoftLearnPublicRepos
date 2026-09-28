<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# inferenceData resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The [inferenceData](https://learn.microsoft.com/en-us/graph/api/resources/inferencedata?view=graph-rest-beta) resource type provides additional detail about an entity which has been created through inferring information about the user. This information will be present whenever the data within a particular entity was derived from a machine learning or other system process iterating over data.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| confidenceScore | Double | Confidence score reflecting the accuracy of the data inferred about the user. |
| userHasVerifiedAccuracy | Boolean | Records if the user has confirmed this inference as being True or False. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "confidenceScore": 1024,
  "userHasVerifiedAccuracy": true
}
```
