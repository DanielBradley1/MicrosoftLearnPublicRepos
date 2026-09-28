<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# identityFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a finding related to an identity such as a user, role, or function in the authorization system.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

The following resources inherit from this resource type:

- [inactiveawsresourcefinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveawsresourcefinding?view=graph-rest-beta)
- [inactiveawsrolefinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveawsrolefinding?view=graph-rest-beta)
- [inactiveazureserviceprincipalfinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveazureserviceprincipalfinding?view=graph-rest-beta)
- [inactivegcpserviceaccountfinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegcpserviceaccountfinding?view=graph-rest-beta)
- [inactiveserverlessfunctionfinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveserverlessfunctionfinding?view=graph-rest-beta)
- [inactiveuserfinding](https://learn.microsoft.com/en-us/graph/api/resources/inactiveuserfinding?view=graph-rest-beta)
- [overprovisionedawsresourcefinding](https://learn.microsoft.com/en-us/graph/api/resources/overprovisionedawsresourcefinding?view=graph-rest-beta)
- [overprovisionedawsrolefinding](https://learn.microsoft.com/en-us/graph/api/resources/overprovisionedawsrolefinding?view=graph-rest-beta)
- [overprovisionedazureserviceprincipalfinding](https://learn.microsoft.com/en-us/graph/api/resources/overprovisionedazureserviceprincipalfinding?view=graph-rest-beta)
- [overprovisionedgcpserviceaccountfinding](https://learn.microsoft.com/en-us/graph/api/resources/overprovisionedgcpserviceaccountfinding?view=graph-rest-beta)
- [overprovisionedserverlessfunctionfinding](https://learn.microsoft.com/en-us/graph/api/resources/overprovisionedserverlessfunctionfinding?view=graph-rest-beta)
- [overprovisioneduserfinding](https://learn.microsoft.com/en-us/graph/api/resources/overprovisioneduserfinding?view=graph-rest-beta)
- [superawsresourcefinding](https://learn.microsoft.com/en-us/graph/api/resources/superawsresourcefinding?view=graph-rest-beta)
- [superawsrolefinding](https://learn.microsoft.com/en-us/graph/api/resources/superawsrolefinding?view=graph-rest-beta)
- [superazureserviceprincipalfinding](https://learn.microsoft.com/en-us/graph/api/resources/superazureserviceprincipalfinding?view=graph-rest-beta)
- [supergcpserviceaccountfinding](https://learn.microsoft.com/en-us/graph/api/resources/supergcpserviceaccountfinding?view=graph-rest-beta)
- [superserverlessfunctionfinding](https://learn.microsoft.com/en-us/graph/api/resources/superserverlessfunctionfinding?view=graph-rest-beta)
- [superuserfinding](https://learn.microsoft.com/en-us/graph/api/resources/superuserfinding?view=graph-rest-beta)
- [unenforcedMfaAwsUserFinding](https://learn.microsoft.com/en-us/graph/api/resources/unenforcedmfaawsuserfinding?view=graph-rest-beta)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [actionSummary](https://learn.microsoft.com/en-us/graph/api/resources/actionsummary?view=graph-rest-beta) | Contains information on authorization system actions granted to an identity and actions executed by this identity in the last 90 days. This property and its values are a snapshot as of when the finding was created and might not reflect the current values for the identity. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Supports `$select`. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| identityDetails | [identityDetails](https://learn.microsoft.com/en-us/graph/api/resources/identitydetails?view=graph-rest-beta) | An identity's information details. |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identity | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | epresents an identity in an authorization system onboarded to Permissions Management. Autoexpanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityFinding",
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
