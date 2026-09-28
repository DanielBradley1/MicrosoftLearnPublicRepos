<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# iosEasEmailProfileConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing configurations in this profile you can instruct the native email client on iOS devices to communicate with an Exchange server and get email, contacts, calendar, reminders, and notes. Furthermore, you can also specify how much email to sync and how often the device should sync.

Inherits from [easEmailProfileConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easemailprofileconfigurationbase?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosEasEmailProfileConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioseasemailprofileconfiguration-list?view=graph-rest-beta) | [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) objects. |
| [Get iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioseasemailprofileconfiguration-get?view=graph-rest-beta) | [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) | Read properties and relationships of the [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) object. |
| [Create iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioseasemailprofileconfiguration-create?view=graph-rest-beta) | [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) | Create a new [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) object. |
| [Delete iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioseasemailprofileconfiguration-delete?view=graph-rest-beta) | None | Deletes a [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta). |
| [Update iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioseasemailprofileconfiguration-update?view=graph-rest-beta) | [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) | Update the properties of a [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) object. |

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
| usernameSource | [userEmailSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-useremailsource?view=graph-rest-beta) | Username attribute that is picked from AAD and injected into this profile before installing on the device. Inherited from [easEmailProfileConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easemailprofileconfigurationbase?view=graph-rest-beta). Possible values are: `userPrincipalName`, `primarySmtpAddress`. |
| usernameAADSource | [usernameSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-usernamesource?view=graph-rest-beta) | Name of the AAD field, that will be used to retrieve UserName for email profile. Inherited from [easEmailProfileConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easemailprofileconfigurationbase?view=graph-rest-beta). Possible values are: `userPrincipalName`, `primarySmtpAddress`, `samAccountName`. |
| userDomainNameSource | [domainNameSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-domainnamesource?view=graph-rest-beta) | UserDomainname attribute that is picked from AAD and injected into this profile before installing on the device. Inherited from [easEmailProfileConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easemailprofileconfigurationbase?view=graph-rest-beta). Possible values are: `fullDomainName`, `netBiosDomainName`. |
| customDomainName | String | Custom domain name value used while generating an email profile before installing on the device. Inherited from [easEmailProfileConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easemailprofileconfigurationbase?view=graph-rest-beta) |
| accountName | String | Account name. |
| authenticationMethod | [easAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easauthenticationmethod?view=graph-rest-beta) | Authentication method for this Email profile. Possible values are: `usernameAndPassword`, `certificate`, `derivedCredential`. |
| blockMovingMessagesToOtherEmailAccounts | Boolean | Indicates whether or not to block moving messages to other email accounts. |
| blockSendingEmailFromThirdPartyApps | Boolean | Indicates whether or not to block sending email from third party apps. |
| blockSyncingRecentlyUsedEmailAddresses | Boolean | Indicates whether or not to block syncing recently used email addresses, for instance - when composing new email. |
| durationOfEmailToSync | [emailSyncDuration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-emailsyncduration?view=graph-rest-beta) | Duration of time email should be synced back to. . Possible values are: `userDefined`, `oneDay`, `threeDays`, `oneWeek`, `twoWeeks`, `oneMonth`, `unlimited`. |
| emailAddressSource | [userEmailSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-useremailsource?view=graph-rest-beta) | Email attribute that is picked from AAD and injected into this profile before installing on the device. Possible values are: `userPrincipalName`, `primarySmtpAddress`. |
| easServices | [easServices](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-easservices?view=graph-rest-beta) | Exchange data to sync. Possible values are: `none`, `calendars`, `contacts`, `email`, `notes`, `reminders`. |
| easServicesUserOverrideEnabled | Boolean | Allow users to change sync settings. |
| hostName | String | Exchange location that \(URL\) that the native mail app connects to. |
| requireSmime | Boolean | Indicates whether or not to use S/MIME certificate. |
| smimeEnablePerMessageSwitch | Boolean | Indicates whether or not to allow unencrypted emails. |
| smimeEncryptByDefaultEnabled | Boolean | If set to true S/MIME encryption is enabled by default. |
| smimeSigningEnabled | Boolean | If set to true S/MIME signing is enabled for this account |
| smimeSigningUserOverrideEnabled | Boolean | If set to true, the user can toggle S/MIME signing on or off. |
| smimeEncryptByDefaultUserOverrideEnabled | Boolean | If set to true, the user can toggle the encryption by default setting. |
| smimeSigningCertificateUserOverrideEnabled | Boolean | If set to true, the user can select the signing identity. |
| smimeEncryptionCertificateUserOverrideEnabled | Boolean | If set to true the user can select the S/MIME encryption identity. |
| requireSsl | Boolean | Indicates whether or not to use SSL. |
| useOAuth | Boolean | Specifies whether the connection should use OAuth for authentication. |
| signingCertificateType | [emailCertificateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-emailcertificatetype?view=graph-rest-beta) | Signing Certificate type for this Email profile. Possible values are: `none`, `certificate`, `derivedCredential`. |
| encryptionCertificateType | [emailCertificateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-emailcertificatetype?view=graph-rest-beta) | Encryption Certificate type for this Email profile. Possible values are: `none`, `certificate`, `derivedCredential`. |
| perAppVPNProfileId | String | Profile ID of the Per-App VPN policy to be used to access emails from the native Mail client |

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
| identityCertificate | [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta) | Identity certificate. |
| smimeSigningCertificate | [iosCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofile?view=graph-rest-beta) | S/MIME signing certificate. |
| smimeEncryptionCertificate | [iosCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofile?view=graph-rest-beta) | S/MIME encryption certificate. |
| derivedCredentialSettings | [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) | Tenant level settings for the Derived Credentials to be used for authentication. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosEasEmailProfileConfiguration",
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
  "usernameSource": "String",
  "usernameAADSource": "String",
  "userDomainNameSource": "String",
  "customDomainName": "String",
  "accountName": "String",
  "authenticationMethod": "String",
  "blockMovingMessagesToOtherEmailAccounts": true,
  "blockSendingEmailFromThirdPartyApps": true,
  "blockSyncingRecentlyUsedEmailAddresses": true,
  "durationOfEmailToSync": "String",
  "emailAddressSource": "String",
  "easServices": "String",
  "easServicesUserOverrideEnabled": true,
  "hostName": "String",
  "requireSmime": true,
  "smimeEnablePerMessageSwitch": true,
  "smimeEncryptByDefaultEnabled": true,
  "smimeSigningEnabled": true,
  "smimeSigningUserOverrideEnabled": true,
  "smimeEncryptByDefaultUserOverrideEnabled": true,
  "smimeSigningCertificateUserOverrideEnabled": true,
  "smimeEncryptionCertificateUserOverrideEnabled": true,
  "requireSsl": true,
  "useOAuth": true,
  "signingCertificateType": "String",
  "encryptionCertificateType": "String",
  "perAppVPNProfileId": "String"
}
```
