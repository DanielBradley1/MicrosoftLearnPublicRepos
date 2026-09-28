<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awssecretinformationaccessfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsSecretInformationAccessFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents findings for identities who can access secret information.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

The following resources inherit from this resource type:

- [secretInformationAccessAwsResourceFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsresourcefinding?view=graph-rest-beta)
- [secretInformationAccessAwsRoleFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsrolefinding?view=graph-rest-beta)
- [secretInformationAccessAwsServerlessFunctionFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsserverlessfunctionfinding?view=graph-rest-beta)
- [secretInformationAccessAwsUserFinding](https://learn.microsoft.com/en-us/graph/api/resources/secretinformationaccessawsuserfinding?view=graph-rest-beta)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastActiveDateTime | DateTimeOffset | A date specifiying when the last time the identity in this Finding accessed a secret store |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |
| secretInformationWebServices | awsSecretInformationWebServices | AWS secret stores which can be accessed by the user, role, resource or serverless function.The possible values are: `secretsManager`, `certificateAuthority`, `cloudHsm`, `certificateManager`, `unknownFutureValue`. Supports `$filter` \(`has`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identity | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | Represents an identity in an authorization system onboarded to Permissions Management. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). Autoexpanded by default.  <br>  <br>Supports `$filter` as follows: `$filter=identity/authorizationSystem/authorizationSystemId IN ('id1', 'id2')`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsSecretInformationAccessFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "secretInformationWebServices": "String",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  },
  "lastActiveDateTime": "String (timestamp)"
}
```
