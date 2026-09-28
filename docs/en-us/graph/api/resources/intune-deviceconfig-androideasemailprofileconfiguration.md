<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# androidEasEmailProfileConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing configurations in this profile you can instruct the native email client on KNOX devices to communicate with an Exchange server and get email, contacts, calendar, tasks, and notes. Furthermore, you can also specify how much email to sync and how often the device should sync.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidEasEmailProfileConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androideasemailprofileconfiguration-list?view=graph-rest-beta) | [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) objects. |
| [Get androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androideasemailprofileconfiguration-get?view=graph-rest-beta) | [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) | Read properties and relationships of the [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) object. |
| [Create androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androideasemailprofileconfiguration-create?view=graph-rest-beta) | [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) | Create a new [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) object. |
| [Delete androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androideasemailprofileconfiguration-delete?view=graph-rest-beta) | None | Deletes a [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta). |
| [Update androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androideasemailprofileconfiguration-update?view=graph-rest-beta) | [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) | Update the properties of a [androidEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideasemailprofileconfiguration?view=graph-rest-beta) object. |

## Properties

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
| accountName | String | Exchange ActiveSync account name, displayed to users as name of EAS \(this\) profile. |
| authenticationMethod | [easAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easauthenticationmethod?view=graph-rest-beta) | Authentication method for Exchange ActiveSync. Possible values are: `usernameAndPassword`, `certificate`, `derivedCredential`. |
| syncCalendar | Boolean | Toggles syncing the calendar. If set to false calendar is turned off on the device. |
| syncContacts | Boolean | Toggles syncing contacts. If set to false contacts are turned off on the device. |
| syncTasks | Boolean | Toggles syncing tasks. If set to false tasks are turned off on the device. |
| syncNotes | Boolean | Toggles syncing notes. If set to false notes are turned off on the device. |
| durationOfEmailToSync | [emailSyncDuration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-emailsyncduration?view=graph-rest-beta) | Duration of time email should be synced to. Possible values are: `userDefined`, `oneDay`, `threeDays`, `oneWeek`, `twoWeeks`, `oneMonth`, `unlimited`. |
| emailAddressSource | [userEmailSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-useremailsource?view=graph-rest-beta) | Email attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: `userPrincipalName`, `primarySmtpAddress`. |
| emailSyncSchedule | [emailSyncSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-emailsyncschedule?view=graph-rest-beta) | Email sync schedule. Possible values are: `userDefined`, `asMessagesArrive`, `manual`, `fifteenMinutes`, `thirtyMinutes`, `sixtyMinutes`, `basedOnMyUsage`. |
| hostName | String | Exchange location \(URL\) that the native mail app connects to. |
| requireSmime | Boolean | Indicates whether or not to use S/MIME certificate. |
| requireSsl | Boolean | Indicates whether or not to use SSL. |
| usernameSource | [androidUsernameSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidusernamesource?view=graph-rest-beta) | Username attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: `username`, `userPrincipalName`, `samAccountName`, `primarySmtpAddress`. |
| userDomainNameSource | [domainNameSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-domainnamesource?view=graph-rest-beta) | UserDomainname attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: `fullDomainName`, `netBiosDomainName`. |
| customDomainName | String | Custom domain name value used while generating an email profile before installing on the device. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groupAssignments | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-beta) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-beta) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-beta) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-beta) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-beta) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| identityCertificate | [androidCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcertificateprofilebase?view=graph-rest-beta) | Identity certificate. |
| smimeSigningCertificate | [androidCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcertificateprofilebase?view=graph-rest-beta) | S/MIME signing certificate. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidEasEmailProfileConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "String"
    ],
    "name": "String",
    "ruleType": "String"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "String",
    "maxOSVersion": "String",
    "name": "String",
    "ruleType": "String"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "String",
    "name": "String",
    "ruleType": "String"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "accountName": "String",
  "authenticationMethod": "String",
  "syncCalendar": true,
  "syncContacts": true,
  "syncTasks": true,
  "syncNotes": true,
  "durationOfEmailToSync": "String",
  "emailAddressSource": "String",
  "emailSyncSchedule": "String",
  "hostName": "String",
  "requireSmime": true,
  "requireSsl": true,
  "usernameSource": "String",
  "userDomainNameSource": "String",
  "customDomainName": "String"
}
```
