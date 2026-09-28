<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsCreepIndexDistribution resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the Permissions Creep Index Distribution for the authorization system. PCI distribution chart shows the classification of human and non-human identities based on the PCI score in three buckets: low, medium, high.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/permissionsanalytics-list-permissionscreepindexdistributions?view=graph-rest-beta) | [permissionsCreepIndexDistribution](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta) collection | Get the permissionsCreepIndexDistribution resources from the permissionsCreepIndexDistributions navigation property. |
| [Get](https://learn.microsoft.com/en-us/graph/api/permissionscreepindexdistribution-get?view=graph-rest-beta) | [permissionsCreepIndexDistribution](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta) | Read the properties and relationships of a [permissionsCreepIndexDistribution](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the PCI distribution was created. |
| highRiskProfile | [riskProfile](https://learn.microsoft.com/en-us/graph/api/resources/riskprofile?view=graph-rest-beta) | Defines the human and non-human identities in a high-risk bucket. |
| id | String | Unique identifier for the PCI distribution. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lowRiskProfile | [riskProfile](https://learn.microsoft.com/en-us/graph/api/resources/riskprofile?view=graph-rest-beta) | Defines the human and nonhuman identities in the low-risk bucket. |
| mediumRiskProfile | [riskProfile](https://learn.microsoft.com/en-us/graph/api/resources/riskprofile?view=graph-rest-beta) | Defines human and nonhuman identities in the medium-risk bucket. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Represents an authorization system onboarded to Permissions Management. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsCreepIndexDistribution",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lowRiskProfile": {
    "@odata.type": "microsoft.graph.riskProfile"
  },
  "mediumRiskProfile": {
    "@odata.type": "microsoft.graph.riskProfile"
  },
  "highRiskProfile": {
    "@odata.type": "microsoft.graph.riskProfile"
  }
}
```
