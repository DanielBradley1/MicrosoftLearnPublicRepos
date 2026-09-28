<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppProtectionPolicySetItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for managed app protection PolicySetItem.

Inherits from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppProtectionPolicySetItems](https://learn.microsoft.com/en-us/graph/api/intune-policyset-managedappprotectionpolicysetitem-list?view=graph-rest-beta) | [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) collection | List properties and relationships of the [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) objects. |
| [Get managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-managedappprotectionpolicysetitem-get?view=graph-rest-beta) | [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) | Read properties and relationships of the [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) object. |
| [Create managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-managedappprotectionpolicysetitem-create?view=graph-rest-beta) | [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) | Create a new [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) object. |
| [Delete managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-managedappprotectionpolicysetitem-delete?view=graph-rest-beta) | None | Deletes a [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta). |
| [Update managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-managedappprotectionpolicysetitem-update?view=graph-rest-beta) | [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) | Update the properties of a [managedAppProtectionPolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-managedappprotectionpolicysetitem?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | Creation time of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| payloadId | String | PayloadId of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| itemType | String | policySetType of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| displayName | String | DisplayName of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| status | [policySetStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetstatus?view=graph-rest-beta) | Status of the PolicySetItem. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta). Possible values are: `unknown`, `validating`, `partialSuccess`, `success`, `error`, `notAssigned`. |
| errorCode | [errorCode](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-errorcode?view=graph-rest-beta) | Error code if any occured. Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta). Possible values are: `noError`, `unauthorized`, `notFound`, `deleted`. |
| guidedDeploymentTags | String collection | Tags of the guided deployment Inherited from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta) |
| targetedAppManagementLevels | String | TargetedAppManagementLevels of the ManagedAppPolicySetItem. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppProtectionPolicySetItem",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "payloadId": "String",
  "itemType": "String",
  "displayName": "String",
  "status": "String",
  "errorCode": "String",
  "guidedDeploymentTags": [
    "String"
  ],
  "targetedAppManagementLevels": "String"
}
```
