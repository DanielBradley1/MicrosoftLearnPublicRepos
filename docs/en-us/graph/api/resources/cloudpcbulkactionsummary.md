<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkactionsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-09 -->

# cloudPcBulkActionSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a run summary of the bulk actions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedCount | Int32 | The number of Cloud PCs where the action failed. |
| inProgressCount | Int32 | The number of Cloud PCs where the action is in progress. |
| notSupportedCount | Int32 | The number of Cloud PCs where the action isn't supported. |
| pendingCount | Int32 | The number of Cloud PCs where the action is pending. |
| successfulCount | Int32 | The number of Cloud PCs where the action is successful. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkActionSummary",
  "failedCount": "Int32",
  "inProgressCount": "Int32",
  "notSupportedCount": "Int32",
  "pendingCount": "Int32",
  "successfulCount": "Int32"
}
```
