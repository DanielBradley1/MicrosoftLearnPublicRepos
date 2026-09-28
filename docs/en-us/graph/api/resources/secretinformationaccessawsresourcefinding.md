<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsresourcefinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# secretInformationAccessAwsResourceFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View AWS resources that have privileges to read, modify, or delete secret information.

Inherits from [awsSecretInformationAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecretinformationaccessfinding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/secretinformationaccessawsresourcefinding-list?view=graph-rest-beta) | [secretInformationAccessAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsresourcefinding?view=graph-rest-beta) collection | Get a list of the [secretInformationAccessAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsresourcefinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/secretinformationaccessawsresourcefinding-get?view=graph-rest-beta) | [secretInformationAccessAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsresourcefinding?view=graph-rest-beta) | Read the properties and relationships of a [secretInformationAccessAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsresourcefinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastActiveDateTime | DateTimeOffset | Defines the last time the identity in this finding executed an authorization system action. Inherited from [awsSecretInformationAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecretinformationaccessfinding?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. Inherited from [awsSecretInformationAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecretinformationaccessfinding?view=graph-rest-beta). |
| secretInformationWebServices | awsSecretInformationWebServices | AWS secret stores which can be accessed by the user, role, resource or serverless function Inherited from [awsSecretInformationAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecretinformationaccessfinding?view=graph-rest-beta).The possible values are: `secretsManager`, `certificateAuthority`, `cloudHsm`, `certificateManager`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identity | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | Represents an identity in an authorization system onboarded to Permissions Management. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). Autoexpanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.secretInformationAccessAwsResourceFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "secretInformationWebServices": "String",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  },
  "lastActiveDateTime": "String (timestamp)"
}
```
