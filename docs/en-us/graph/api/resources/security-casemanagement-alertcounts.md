<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-alertcounts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# alertCounts resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains alert count summaries for an [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta). Returned in the **alertCounts** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| active | Int32 | The number of active alerts. |
| bySeverity | [microsoft.graph.security.caseManagement.incidentSeverityCounts](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentseveritycounts?view=graph-rest-beta) | The alert counts grouped by incident severity. |
| byStatus | [microsoft.graph.security.caseManagement.alertStatusCounts](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-alertstatuscounts?view=graph-rest-beta) | The alert counts grouped by alert status. |
| total | Int32 | The total number of alerts. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.alertCounts",
  "total": "Integer",
  "active": "Integer",
  "bySeverity": {
    "@odata.type": "#microsoft.graph.security.caseManagement.incidentSeverityCounts"
  },
  "byStatus": {
    "@odata.type": "#microsoft.graph.security.caseManagement.alertStatusCounts"
  }
}
```
