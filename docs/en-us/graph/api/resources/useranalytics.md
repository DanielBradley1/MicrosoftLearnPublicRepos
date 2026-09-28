<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/useranalytics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userAnalytics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The user's settings and activity statistics.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get settings](https://learn.microsoft.com/en-us/graph/api/useranalytics-get-settings?view=graph-rest-beta) | [settings](https://learn.microsoft.com/en-us/graph/api/resources/settings?view=graph-rest-beta) | Get the user's settings for using the analytics API. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settings | [settings](https://learn.microsoft.com/en-us/graph/api/resources/settings?view=graph-rest-beta) | The current settings for a user to use the analytics API. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activityStatistics | [activityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/activitystatistics?view=graph-rest-beta) collection | The collection of work activities that a user spent time on during and outside of working hours. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activityStatistics": [{"@odata.type": "microsoft.graph.activityStatistics"}],
  "id": "string",
  "settings": {"@odata.type": "microsoft.graph.settings"}
}
```
