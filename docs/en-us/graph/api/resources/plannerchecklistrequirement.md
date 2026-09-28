<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerChecklistRequirement resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a checklist completion requirement on a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| requiredChecklistItemIds | String collection | A collection of required [plannerChecklistItems](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitems?view=graph-rest-beta) identifiers to complete the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerChecklistRequirement",
  "requiredChecklistItemIds": ["String"]
}
```
