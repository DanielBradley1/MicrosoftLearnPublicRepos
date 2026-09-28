<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydatarunrolecountmetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# industryDataRunRoleCountMetric resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a count of people in a given role.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| count | Int32 | The number of people in this role. |
| role | String | The role that is being measured. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataRunRoleCountMetric",
  "count": "Int32",
  "role": "String"
}
```
