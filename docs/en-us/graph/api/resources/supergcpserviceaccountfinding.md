<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/supergcpserviceaccountfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# superGcpServiceAccountFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the super GCP service accounts.

Inherits from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/supergcpserviceaccountfinding-list?view=graph-rest-beta) | [superGcpServiceAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/supergcpserviceaccountfinding?view=graph-rest-beta) collection | Get a list of the [superGcpServiceAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/supergcpserviceaccountfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/supergcpserviceaccountfinding-get?view=graph-rest-beta) | [superGcpServiceAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/supergcpserviceaccountfinding?view=graph-rest-beta) | Read the properties and relationships of a [superGcpServiceAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/supergcpserviceaccountfinding?view=graph-rest-beta) object. |
| [Aggregated summary](https://learn.microsoft.com/en-us/graph/api/supergcpserviceaccountfinding-aggregatedsummary?view=graph-rest-beta) | [permissionsAnalyticsAggregatedIdentitySummary](https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalyticsaggregatedidentitysummary?view=graph-rest-beta) | Return the total number of an identity type and the total number of a specific finding for that identity in an authorization system. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [actionSummary](https://learn.microsoft.com/en-us/graph/api/resources/actionsummary?view=graph-rest-beta) | Contains information on authorization system actions granted to an identity and actions executed by this identity in the last 90 days. This property and its values are a snapshot as of when the finding was created and might not reflect the current values for the identity. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| identityDetails | [identityDetails](https://learn.microsoft.com/en-us/graph/api/resources/identitydetails?view=graph-rest-beta) | An identity's information details. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identity | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | Represents an identity in an authorization system onboarded to Permissions Management. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). Autoexpanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.superGcpServiceAccountFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  },
  "identityDetails": {
    "@odata.type": "#microsoft.graph.identityDetails"
  },
  "actionSummary": {
    "@odata.type": "microsoft.graph.actionSummary"
  }
}
```
