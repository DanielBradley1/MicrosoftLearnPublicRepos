<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolscalingpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcAgentPoolScalingPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the scaling policy for a Cloud PC agent pool.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maximumCount | Int32 | The maximum number of Cloud PCs in the pool. The valid values are `1` to `900`, and must be greater than or equal to **minimumCount**. |
| minimumCount | Int32 | The minimum number of Cloud PCs in the pool. The valid values are `0` to `900`, and must be less than or equal to **maximumCount**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolScalingPolicy",
  "maximumCount": "Int32",
  "minimumCount": "Int32"
}
```
