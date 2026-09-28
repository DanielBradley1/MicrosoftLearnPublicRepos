<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/asyncjobstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# asyncJobStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This resource provides information on the status of a asynchronous job progress.

The following API calls return **asyncJobStatus** resources:

- [Copy Item](https://learn.microsoft.com/en-us/graph/api/driveitem-copy?view=graph-rest-beta)

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| percentageComplete | Double | A value between 0 and 100 that indicates the completion percentage. |
| status | String | A string value that maps to an enumeration of possible values about the status of the job. |

## Relationships

None.

## JSON representation

```json
{
  "percentageComplete": 100.0,
  "status": "notStarted | inProgress | completed | updating | failed | deletePending | deleteFailed | waiting"
}
```
