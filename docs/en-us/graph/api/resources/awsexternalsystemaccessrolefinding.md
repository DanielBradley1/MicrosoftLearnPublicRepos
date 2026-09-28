<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessrolefinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsExternalSystemAccessRoleFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the findings for roles that allow for external system access.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsexternalsystemaccessrolefinding-list?view=graph-rest-beta) | [awsExternalSystemAccessRoleFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessrolefinding?view=graph-rest-beta) collection | Get a list of the [awsExternalSystemAccessRoleFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessrolefinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsexternalsystemaccessrolefinding-get?view=graph-rest-beta) | [awsExternalSystemAccessRoleFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessrolefinding?view=graph-rest-beta) | Read the properties and relationships of an [awsExternalSystemAccessRoleFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessrolefinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessibleSystemIds | String collection | The IDs of the accounts that this role is able to access. |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| role | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) | The role that has access to external accounts. Supports `$orderby` \(for `role/displayName`\) and `$filter` as follows: `$filter=role/authorizationSystem/authorizationSystemId IN ['authorizationSystemIds']` and `$filter=role/authorizationSystem/authorizationSystemName eq 'authsystemname'`. Autoexpanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsExternalSystemAccessRoleFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  },
  "accessibleSystemIds": [
    "String"
  ]
}
```
