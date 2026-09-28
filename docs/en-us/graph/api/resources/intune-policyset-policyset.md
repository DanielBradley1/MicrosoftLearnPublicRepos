<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# policySet resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for PolicySet.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List policySets](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-list?view=graph-rest-beta) | [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) collection | List properties and relationships of the [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) objects. |
| [Get policySet](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-get?view=graph-rest-beta) | [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) | Read properties and relationships of the [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) object. |
| [Create policySet](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-create?view=graph-rest-beta) | [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) | Create a new [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) object. |
| [Delete policySet](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-delete?view=graph-rest-beta) | None | Deletes a [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta). |
| [Update policySet](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-update?view=graph-rest-beta) | [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) | Update the properties of a [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) object. |
| [update action](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-update?view=graph-rest-beta) | None |  |
| [getPolicySets action](https://learn.microsoft.com/en-us/graph/api/intune-policyset-policyset-getpolicysets?view=graph-rest-beta) | [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the PolicySet. |
| createdDateTime | DateTimeOffset | Creation time of the PolicySet. |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the PolicySet. |
| displayName | String | DisplayName of the PolicySet. |
| description | String | Description of the PolicySet. |
| status | [policySetStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetstatus?view=graph-rest-beta) | Validation/assignment status of the PolicySet. Possible values are: `unknown`, `validating`, `partialSuccess`, `success`, `error`, `notAssigned`. |
| errorCode | [errorCode](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-errorcode?view=graph-rest-beta) | Error code if any occured. Possible values are: `noError`, `unauthorized`, `notFound`, `deleted`. |
| guidedDeploymentTags | String collection | Tags of the guided deployment |
| roleScopeTags | String collection | RoleScopeTags of the PolicySet |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [policySetAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetassignment?view=graph-rest-beta) collection | Assignments of the PolicySet. |
| items | [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) collection | Items of the PolicySet with maximum count 100. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.policySet",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "status": "String",
  "errorCode": "String",
  "guidedDeploymentTags": [
    "String"
  ],
  "roleScopeTags": [
    "String"
  ]
}
```
