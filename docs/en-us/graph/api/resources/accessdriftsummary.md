<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# accessDriftSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an aggregated view of access drift for a governed resource. Each summary captures the drift state for a single resource and drift source combination, including counts of unauthorized and missing assignments.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/accessdriftsummary-list?view=graph-rest-beta) | [accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta) collection | Get a list of the accessDriftSummary objects and their properties. |
| [Get accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/accessdriftsummary-get?view=graph-rest-beta) | [accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta) | Read the properties and relationships of an accessDriftSummary object. |
| [List details](https://learn.microsoft.com/en-us/graph/api/accessdriftsummary-list-details?view=graph-rest-beta) | [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta) collection | Get the access drift details from the details navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the drift snapshot was created. |
| driftCounts | [driftCounts](https://learn.microsoft.com/en-us/graph/api/resources/driftcounts?view=graph-rest-beta) | The aggregate counts of unauthorized and missing assignments for this resource. |
| driftSource | [accessDriftSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftsource-values) | The comparison system that detected the drift. The possible values are: `entra`, `externalApplication`, `unknownFutureValue`. |
| id | String | The unique identifier for the access drift summary. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resource | [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta) | The governed resource associated with this drift summary. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| details | [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta) collection | The collection of access drift details for this summary. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessDriftSummary",
  "id": "String (identifier)",
  "resource": {"@odata.type": "microsoft.graph.driftResourceInfo"},
  "driftSource": "String",
  "driftCounts": {"@odata.type": "microsoft.graph.driftCounts"},
  "createdDateTime": "String (timestamp)"
}
```
