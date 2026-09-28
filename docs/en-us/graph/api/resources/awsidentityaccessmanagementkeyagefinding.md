<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsIdentityAccessManagementKeyAgeFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View the age of AWS IAM access keys.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsidentityaccessmanagementkeyagefinding-list?view=graph-rest-beta) | [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) collection | Get a list of the [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsidentityaccessmanagementkeyagefinding-get?view=graph-rest-beta) | [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) | Read the properties and relationships of an [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) object. |
| [Aggregated summary](https://learn.microsoft.com/en-us/graph/api/awsidentityaccessmanagementkeyagefinding-aggregatedsummary?view=graph-rest-beta) | [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) | Return the total number of an[awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta)and the total number in a specified authorization system. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [actionSummary](https://learn.microsoft.com/en-us/graph/api/resources/actionsummary?view=graph-rest-beta) | Contains information on authorization system actions granted to an identity and actions executed by this identity in the last 90 days. This property and its values are a snapshot as of when the finding was created and might not reflect the current values for the identity |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |
| status | iamStatus | Status of the IAM access Key. The possible values are: `active`, `inactive`, `disabled`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessKey | [awsAccessKey](https://learn.microsoft.com/en-us/graph/api/resources/awsaccesskey?view=graph-rest-beta) | Represents the AWS access key in an authorization system. **Note:** Because of a limit in the current data model, all the standard identity information for the access key's owner might not be available. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsIdentityAccessManagementKeyAgeFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "actionSummary": {
    "@odata.type": "microsoft.graph.actionSummary"
  },
  "status": "String",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  }
}
```
