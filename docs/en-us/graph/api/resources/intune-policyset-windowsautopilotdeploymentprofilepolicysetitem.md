<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsAutopilotDeploymentProfilePolicySetItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for windows autopilot deployment profile PolicySetItem.

Inherits from [policySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policysetitem?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsAutopilotDeploymentProfilePolicySetItems](https://learn.microsoft.com/en-us/graph/api/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem-list?view=graph-rest-beta) | [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) collection | List properties and relationships of the [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) objects. |
| [Get windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem-get?view=graph-rest-beta) | [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) | Read properties and relationships of the [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) object. |
| [Create windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem-create?view=graph-rest-beta) | [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) | Create a new [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) object. |
| [Delete windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem-delete?view=graph-rest-beta) | None | Deletes a [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta). |
| [Update windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem-update?view=graph-rest-beta) | [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) | Update the properties of a [windowsAutopilotDeploymentProfilePolicySetItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-windowsautopilotdeploymentprofilepolicysetitem?view=graph-rest-beta) object. |

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

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsAutopilotDeploymentProfilePolicySetItem",
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
  ]
}
```
