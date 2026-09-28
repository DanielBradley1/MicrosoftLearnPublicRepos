<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-alertstatuscounts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# alertStatusCounts resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains counts of alerts grouped by status for [alertCounts](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-alertcounts?view=graph-rest-beta). Returned in the **byStatus** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inProgress | Int32 | The number of alerts that are in progress. |
| new | Int32 | The number of new alerts. |
| resolved | Int32 | The number of resolved alerts. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.alertStatusCounts",
  "new": "Integer",
  "inProgress": "Integer",
  "resolved": "Integer"
}
```
