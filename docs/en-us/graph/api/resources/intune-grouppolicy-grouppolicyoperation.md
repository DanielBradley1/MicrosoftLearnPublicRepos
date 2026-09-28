<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# groupPolicyOperation resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The entity represents an group policy operation.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyOperations](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyoperation-list?view=graph-rest-beta) | [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) objects. |
| [Get groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyoperation-get?view=graph-rest-beta) | [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) object. |
| [Create groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyoperation-create?view=graph-rest-beta) | [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) | Create a new [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) object. |
| [Delete groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyoperation-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta). |
| [Update groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyoperation-update?view=graph-rest-beta) | [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) | Update the properties of a [groupPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operationType | [groupPolicyOperationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperationtype?view=graph-rest-beta) | The type of group policy operation. Possible values are: `none`, `upload`, `uploadNewVersion`, `addLanguageFiles`, `removeLanguageFiles`, `updateLanguageFiles`, `remove`. |
| operationStatus | [groupPolicyOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyoperationstatus?view=graph-rest-beta) | The group policy operation status. Possible values are: `unknown`, `inProgress`, `success`, `failed`. |
| statusDetails | String | The group policy operation status detail. |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyOperation",
  "operationType": "String",
  "operationStatus": "String",
  "statusDetails": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
