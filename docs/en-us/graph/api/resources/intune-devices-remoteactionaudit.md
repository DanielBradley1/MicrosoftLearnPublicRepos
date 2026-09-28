<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# remoteActionAudit resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Report of remote actions initiated on the devices belonging to a certain tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List remoteActionAudits](https://learn.microsoft.com/en-us/graph/api/intune-devices-remoteactionaudit-list?view=graph-rest-beta) | [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) collection | List properties and relationships of the [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) objects. |
| [Get remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/intune-devices-remoteactionaudit-get?view=graph-rest-beta) | [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) | Read properties and relationships of the [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) object. |
| [Create remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/intune-devices-remoteactionaudit-create?view=graph-rest-beta) | [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) | Create a new [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) object. |
| [Delete remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/intune-devices-remoteactionaudit-delete?view=graph-rest-beta) | None | Deletes a [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta). |
| [Update remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/intune-devices-remoteactionaudit-update?view=graph-rest-beta) | [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) | Update the properties of a [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Report Id. |
| deviceDisplayName | String | Intune device name. |
| userName | String | \[deprecated\] Please use InitiatedByUserPrincipalName instead. |
| initiatedByUserPrincipalName | String | User who initiated the device action, format is UPN. |
| action | [remoteAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteaction?view=graph-rest-beta) | The action name. Possible values are: `unknown`, `factoryReset`, `removeCompanyData`, `resetPasscode`, `remoteLock`, `enableLostMode`, `disableLostMode`, `locateDevice`, `rebootNow`, `recoverPasscode`, `cleanWindowsDevice`, `logoutSharedAppleDeviceActiveUser`, `quickScan`, `fullScan`, `windowsDefenderUpdateSignatures`, `factoryResetKeepEnrollmentData`, `updateDeviceAccount`, `automaticRedeployment`, `shutDown`, `rotateBitLockerKeys`, `rotateFileVaultKey`, `getFileVaultKey`, `setDeviceName`, `activateDeviceEsim`, `deprovision`, `disable`, `reenable`, `moveDeviceToOrganizationalUnit`, `initiateMobileDeviceManagementKeyRecovery`, `initiateOnDemandProactiveRemediation`, `rotateLocalAdminPassword`, `unknownFutureValue`, `launchRemoteHelp`, `revokeAppleVppLicenses`, `removeDeviceFirmwareConfigurationInterfaceManagement`, `pauseConfigurationRefresh`, `initiateDeviceAttestation`, `changeAssignments`, `delete`, `suspendManagedHomeScreen`, `restoreManagedHomeScreen`. |
| requestDateTime | DateTimeOffset | Time when the action was issued, given in UTC. |
| deviceOwnerUserPrincipalName | String | Upn of the device owner. |
| deviceIMEI | String | IMEI of the device. |
| actionState | [actionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-actionstate?view=graph-rest-beta) | Action state. Possible values are: `none`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. |
| managedDeviceId | String | Action target. |
| deviceActionDetails | [keyValuePair\_2OfString\_String](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-keyvaluepair_2ofstring_string?view=graph-rest-beta) collection | DeviceAction details |
| deviceActionCategory | [deviceActionCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceactioncategory?view=graph-rest-beta) | DeviceAction category. Possible values are: `single`, `bulk`. |
| bulkDeviceActionId | String | BulkAction ID |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.remoteActionAudit",
  "id": "String (identifier)",
  "deviceDisplayName": "String",
  "userName": "String",
  "initiatedByUserPrincipalName": "String",
  "action": "String",
  "requestDateTime": "String (timestamp)",
  "deviceOwnerUserPrincipalName": "String",
  "deviceIMEI": "String",
  "actionState": "String",
  "managedDeviceId": "String",
  "deviceActionDetails": [
    {
      "@odata.type": "microsoft.graph.keyValuePair_2OfString_String"
    }
  ],
  "deviceActionCategory": "String",
  "bulkDeviceActionId": "String"
}
```
