<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the deployment state of a WindowsDefenderApplicationControl supplemental policy for a device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDefenderApplicationControlSupplementalPolicyDeploymentStatuses](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus-list?view=graph-rest-beta) | [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) collection | List properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) objects. |
| [Get windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus-get?view=graph-rest-beta) | [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) | Read properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) object. |
| [Create windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus-create?view=graph-rest-beta) | [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) | Create a new [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) object. |
| [Delete windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus-delete?view=graph-rest-beta) | None | Deletes a [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta). |
| [Update windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus-update?view=graph-rest-beta) | [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) | Update the properties of a [windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentstatus?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| deviceName | String | Device name. |
| deviceId | String | Device ID. |
| lastSyncDateTime | DateTimeOffset | Last sync date time. |
| osVersion | String | Windows OS Version. |
| osDescription | String | Windows OS Version Description. |
| deploymentStatus | [windowsDefenderApplicationControlSupplementalPolicyStatuses](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicystatuses?view=graph-rest-beta) | The deployment state of the policy. Possible values are: `unknown`, `success`, `tokenError`, `notAuthorizedByToken`, `policyNotFound`. |
| userName | String | The name of the user of this device. |
| userPrincipalName | String | User Principal Name. |
| policyVersion | String | Human readable version of the WindowsDefenderApplicationControl supplemental policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-beta) | The navigation link to the WindowsDefenderApplicationControl supplemental policy. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDefenderApplicationControlSupplementalPolicyDeploymentStatus",
  "id": "String (identifier)",
  "deviceName": "String",
  "deviceId": "String",
  "lastSyncDateTime": "String (timestamp)",
  "osVersion": "String",
  "osDescription": "String",
  "deploymentStatus": "String",
  "userName": "String",
  "userPrincipalName": "String",
  "policyVersion": "String"
}
```
