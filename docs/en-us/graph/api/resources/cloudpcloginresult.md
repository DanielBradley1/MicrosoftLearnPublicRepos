<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcloginresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# cloudPcLoginResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of the Cloud PC sign in results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| time | DateTimeOffSet | The time of the Cloud PC sign in action. The timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 appears as '2014-01-01T00:00:00Z'. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcLoginResult",
  "time": "String (timestamp)"
}
```
