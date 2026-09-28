<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateconfiguration-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Create macOSSoftwareUpdateConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/deviceConfigurations
POST /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsDomainJoinConfiguration/networkAccessConfigurations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the macOSSoftwareUpdateConfiguration object.

The following table shows the properties that are required when you create the macOSSoftwareUpdateConfiguration.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| supportsScopeTags | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsEdition | [deviceManagementApplicabilityRuleOsEdition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosedition?view=graph-rest-beta) | The OS edition applicability for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsVersion | [deviceManagementApplicabilityRuleOsVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosversion?view=graph-rest-beta) | The OS version applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleDeviceMode | [deviceManagementApplicabilityRuleDeviceMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruledevicemode?view=graph-rest-beta) | The device mode applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| criticalUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for critical updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| configDataUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for configuration data file updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| firmwareUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for firmware updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| allOtherUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for all other updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| updateScheduleType | [macOSSoftwareUpdateScheduleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatescheduletype?view=graph-rest-beta) | Update schedule type. Possible values are: `alwaysUpdate`, `updateDuringTimeWindows`, `updateOutsideOfTimeWindows`. |
| customUpdateTimeWindows | [customUpdateTimeWindow](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-customupdatetimewindow?view=graph-rest-beta) collection | Custom Time windows when updates will be allowed or blocked. This collection can contain a maximum of 20 elements. |
| updateTimeWindowUtcOffsetInMinutes | Int32 | Minutes indicating UTC offset for each update time window |
| maxUserDeferralsCount | Int32 | The maximum number of times the system allows the user to postpone an update before it’s installed. Supported values: 0 - 366. Valid values 0 to 365 |
| priority | [macOSPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macospriority?view=graph-rest-beta) | The scheduling priority for downloading and preparing the requested update. Default: Low. Possible values: Null, Low, High. Possible values are: `low`, `high`, `unknownFutureValue`. |

## Response

If successful, this method returns a `201 Created` response code and a [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations
Content-type: application/json
Content-length: 1596

{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateConfiguration",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "windows10EnterpriseN"
    ],
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "Min OSVersion value",
    "maxOSVersion": "Max OSVersion value",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "sModeConfiguration",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "criticalUpdateBehavior": "default",
  "configDataUpdateBehavior": "default",
  "firmwareUpdateBehavior": "default",
  "allOtherUpdateBehavior": "default",
  "updateScheduleType": "updateDuringTimeWindows",
  "customUpdateTimeWindows": [
    {
      "@odata.type": "microsoft.graph.customUpdateTimeWindow",
      "startDay": "monday",
      "endDay": "monday",
      "startTime": "12:03:30.2730000",
      "endTime": "12:03:02.3740000"
    }
  ],
  "updateTimeWindowUtcOffsetInMinutes": 2,
  "maxUserDeferralsCount": 5,
  "priority": "high"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 1768

{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateConfiguration",
  "id": "b8e467ac-67ac-b8e4-ac67-e4b8ac67e4b8",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "roleScopeTagIds": [
    "Role Scope Tag Ids value"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "windows10EnterpriseN"
    ],
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "Min OSVersion value",
    "maxOSVersion": "Max OSVersion value",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "sModeConfiguration",
    "name": "Name value",
    "ruleType": "exclude"
  },
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "criticalUpdateBehavior": "default",
  "configDataUpdateBehavior": "default",
  "firmwareUpdateBehavior": "default",
  "allOtherUpdateBehavior": "default",
  "updateScheduleType": "updateDuringTimeWindows",
  "customUpdateTimeWindows": [
    {
      "@odata.type": "microsoft.graph.customUpdateTimeWindow",
      "startDay": "monday",
      "endDay": "monday",
      "startTime": "12:03:30.2730000",
      "endTime": "12:03:02.3740000"
    }
  ],
  "updateTimeWindowUtcOffsetInMinutes": 2,
  "maxUserDeferralsCount": 5,
  "priority": "high"
}
```
