<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entraaccessdriftdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# entraAccessDriftDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an access drift detail specific to Microsoft Entra reconciliation. Extends [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta) with role and access package information.

Inherits from [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [driftAccessPackageInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftaccesspackageinfo?view=graph-rest-beta) | The access package associated with this drift record. |
| assignedRole | String | The role currently assigned to the identity on the resource. |
| createdDateTime | DateTimeOffset | The date and time when the drift record was created. Inherited from [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta). |
| driftSource | [accessDriftSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftsource-values) | The comparison system that detected the drift. Inherited from [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta). The possible values are: `entra`, `externalApplication`, `unknownFutureValue`. |
| driftType | [accessDriftType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdrifttype-values) | The classification of the drift. Inherited from [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta). The possible values are: `unauthorized`, `missing`, `inSync`, `unknownFutureValue`. |
| expectedRole | String | The role expected based on the access package assignment. |
| id | String | The unique identifier for the drift detail. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resource | [driftResourceInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftresourceinfo?view=graph-rest-beta) | The governed resource associated with this drift record. Inherited from [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identities | [driftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta) collection | The identities affected by this drift record. Inherited from [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraAccessDriftDetail",
  "id": "String (identifier)",
  "resource": {"@odata.type": "microsoft.graph.driftResourceInfo"},
  "driftSource": "String",
  "driftType": "String",
  "createdDateTime": "String (timestamp)",
  "assignedRole": "String",
  "expectedRole": "String",
  "accessPackage": {"@odata.type": "microsoft.graph.driftAccessPackageInfo"}
}
```
