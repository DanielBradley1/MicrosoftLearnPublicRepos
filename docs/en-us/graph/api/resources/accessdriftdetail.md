<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# accessDriftDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an individual access drift record for one or more identities and a resource. This concrete polymorphic base type can appear alongside derived types such as [entraAccessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/entraaccessdriftdetail?view=graph-rest-beta), which provide source-specific properties. The **@odata.type** property identifies the type of each instance.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List details](https://learn.microsoft.com/en-us/graph/api/accessdriftsummary-list-details?view=graph-rest-beta) | [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta) collection | Get a list of the access drift detail objects for a summary. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the drift record was created. |
| driftSource | [accessDriftSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftsource-values) | The comparison system that detected the drift. The possible values are: `entra`, `externalApplication`, `unknownFutureValue`. |
| driftType | [accessDriftType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdrifttype-values) | The classification of the drift. The possible values are: `unauthorized`, `missing`, `inSync`, `unknownFutureValue`. |
| id | String | The unique identifier for the drift detail. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resource | [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta) | The governed resource associated with this drift record. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identities | [driftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta) collection | The identities affected by this drift record. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessDriftDetail",
  "id": "String (identifier)",
  "resource": {"@odata.type": "microsoft.graph.driftResourceInfo"},
  "driftSource": "String",
  "driftType": "String",
  "createdDateTime": "String (timestamp)"
}
```
