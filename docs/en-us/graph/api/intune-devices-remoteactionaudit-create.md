<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-remoteactionaudit-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Create remoteActionAudit

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/remoteActionAudits
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the remoteActionAudit object.

The following table shows the properties that are required when you create the remoteActionAudit.

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

## Response

If successful, this method returns a `201 Created` response code and a [remoteActionAudit](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remoteactionaudit?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/remoteActionAudits
Content-type: application/json
Content-length: 713

{
  "@odata.type": "#microsoft.graph.remoteActionAudit",
  "deviceDisplayName": "Device Display Name value",
  "userName": "User Name value",
  "initiatedByUserPrincipalName": "Initiated By User Principal Name value",
  "action": "factoryReset",
  "requestDateTime": "2017-01-01T00:03:07.1589002-08:00",
  "deviceOwnerUserPrincipalName": "Device Owner User Principal Name value",
  "deviceIMEI": "Device IMEI value",
  "actionState": "pending",
  "managedDeviceId": "Managed Device Id value",
  "deviceActionDetails": [
    {
      "@odata.type": "microsoft.graph.keyValuePair_2OfString_String"
    }
  ],
  "deviceActionCategory": "bulk",
  "bulkDeviceActionId": "Bulk Device Action Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 762

{
  "@odata.type": "#microsoft.graph.remoteActionAudit",
  "id": "477f8d24-8d24-477f-248d-7f47248d7f47",
  "deviceDisplayName": "Device Display Name value",
  "userName": "User Name value",
  "initiatedByUserPrincipalName": "Initiated By User Principal Name value",
  "action": "factoryReset",
  "requestDateTime": "2017-01-01T00:03:07.1589002-08:00",
  "deviceOwnerUserPrincipalName": "Device Owner User Principal Name value",
  "deviceIMEI": "Device IMEI value",
  "actionState": "pending",
  "managedDeviceId": "Managed Device Id value",
  "deviceActionDetails": [
    {
      "@odata.type": "microsoft.graph.keyValuePair_2OfString_String"
    }
  ],
  "deviceActionCategory": "bulk",
  "bulkDeviceActionId": "Bulk Device Action Id value"
}
```
