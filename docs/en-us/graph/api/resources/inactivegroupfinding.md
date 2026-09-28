<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# inactiveGroupFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Contains analytic information for an inactive group in an authorization system, including actions granted to the group and its members in the last 90 days.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/inactivegroupfinding-list?view=graph-rest-beta) | [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) collection | Get a list of the [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/inactivegroupfinding-get?view=graph-rest-beta) | [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) | Read the properties and relationships of an [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [actionSummary](https://learn.microsoft.com/en-us/graph/api/resources/actionsummary?view=graph-rest-beta) | Contains information on authorization system actions granted to this group identity and actions executed by this group identity in the last 90 days. This property and its values are a snapshot as of when the finding was created and may not reflect the current values for the group identity. |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| group | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | Represents an identity in an authorization system that you've onboarded to Permissions Management. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.inactiveGroupFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "actionSummary": {
    "@odata.type": "microsoft.graph.actionSummary"
  },
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  }
}
```
