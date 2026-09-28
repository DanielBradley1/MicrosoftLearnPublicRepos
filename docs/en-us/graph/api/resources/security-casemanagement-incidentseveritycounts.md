<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentseveritycounts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# incidentSeverityCounts resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains counts of alerts grouped by severity for [alertCounts](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-alertcounts?view=graph-rest-beta). Returned in the **bySeverity** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| high | Int32 | The number of alerts with high severity. |
| informational | Int32 | The number of alerts with informational severity. |
| low | Int32 | The number of alerts with low severity. |
| medium | Int32 | The number of alerts with medium severity. |
| unknown | Int32 | The number of alerts with unknown severity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.incidentSeverityCounts",
  "unknown": "Integer",
  "informational": "Integer",
  "low": "Integer",
  "medium": "Integer",
  "high": "Integer"
}
```
