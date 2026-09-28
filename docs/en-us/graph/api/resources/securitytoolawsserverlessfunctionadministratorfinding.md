<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securitytoolawsserverlessfunctionadministratorfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# securityToolAwsServerlessFunctionAdministratorFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View AWS serverless functions that can administer security tools.

Inherits from [awsSecurityToolAdministrationFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecuritytooladministrationfinding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/securitytoolawsserverlessfunctionadministratorfinding-list?view=graph-rest-beta) | [securityToolAwsServerlessFunctionAdministratorFinding](https://learn.microsoft.com/en-us/graph/api/resources/securitytoolawsserverlessfunctionadministratorfinding?view=graph-rest-beta) collection | Get a list of the [securityToolAwsServerlessFunctionAdministratorFinding](https://learn.microsoft.com/en-us/graph/api/resources/securitytoolawsserverlessfunctionadministratorfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/securitytoolawsserverlessfunctionadministratorfinding-get?view=graph-rest-beta) | [securityToolAwsServerlessFunctionAdministratorFinding](https://learn.microsoft.com/en-us/graph/api/resources/securitytoolawsserverlessfunctionadministratorfinding?view=graph-rest-beta) | Read the properties and relationships of a [securityToolAwsServerlessFunctionAdministratorFinding](https://learn.microsoft.com/en-us/graph/api/resources/securitytoolawsserverlessfunctionadministratorfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| securityTools | awsSecurityToolWebServices | AWS security tools which can be administered by the user, role, resource or serverless function. Inherited from [awsSecurityToolAdministrationFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecuritytooladministrationfinding?view=graph-rest-beta).The possible values are: `macie`, `wafShield`, `cloudTrail`, `inspector`, `securityHub`, `detective`, `guardDuty`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identity | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | Represents an identity in an authorization system. Inherited from [microsoft.graph.awsSecurityToolAdministrationFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecuritytooladministrationfinding?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.securityToolAwsServerlessFunctionAdministratorFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "securityTools": "String",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  },
  "lastActiveDateTime": "String (timestamp)"
}
```
