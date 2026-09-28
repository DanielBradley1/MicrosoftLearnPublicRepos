<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioseasemailprofileconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Update iosEasEmailProfileConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) object.

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
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/groupAssignments/{deviceConfigurationGroupAssignmentId}/deviceConfiguration
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsDomainJoinConfiguration/networkAccessConfigurations/{deviceConfigurationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta).

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

## Response

If successful, this method returns a `200 OK` response code and an updated [iosEasEmailProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioseasemailprofileconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations/{deviceConfigurationId}
Content-type: application/json
Content-length: 2187

{
  "@odata.type": "#microsoft.graph.iosEasEmailProfileConfiguration",
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
  "usernameSource": "primarySmtpAddress",
  "usernameAADSource": "primarySmtpAddress",
  "userDomainNameSource": "netBiosDomainName",
  "customDomainName": "Custom Domain Name value",
  "accountName": "Account Name value",
  "authenticationMethod": "certificate",
  "blockMovingMessagesToOtherEmailAccounts": true,
  "blockSendingEmailFromThirdPartyApps": true,
  "blockSyncingRecentlyUsedEmailAddresses": true,
  "durationOfEmailToSync": "oneDay",
  "emailAddressSource": "primarySmtpAddress",
  "easServices": "calendars",
  "easServicesUserOverrideEnabled": true,
  "hostName": "Host Name value",
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
  "signingCertificateType": "certificate",
  "encryptionCertificateType": "certificate",
  "perAppVPNProfileId": "Per App VPNProfile Id value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 2359

{
  "@odata.type": "#microsoft.graph.iosEasEmailProfileConfiguration",
  "id": "e03086da-86da-e030-da86-30e0da8630e0",
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
  "usernameSource": "primarySmtpAddress",
  "usernameAADSource": "primarySmtpAddress",
  "userDomainNameSource": "netBiosDomainName",
  "customDomainName": "Custom Domain Name value",
  "accountName": "Account Name value",
  "authenticationMethod": "certificate",
  "blockMovingMessagesToOtherEmailAccounts": true,
  "blockSendingEmailFromThirdPartyApps": true,
  "blockSyncingRecentlyUsedEmailAddresses": true,
  "durationOfEmailToSync": "oneDay",
  "emailAddressSource": "primarySmtpAddress",
  "easServices": "calendars",
  "easServicesUserOverrideEnabled": true,
  "hostName": "Host Name value",
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
  "signingCertificateType": "certificate",
  "encryptionCertificateType": "certificate",
  "perAppVPNProfileId": "Per App VPNProfile Id value"
}
```
