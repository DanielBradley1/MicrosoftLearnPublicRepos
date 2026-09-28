<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# windowsWiredNetworkConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity provides descriptions of the declared methods, properties and relationships exposed by the Wired Network CSP.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsWiredNetworkConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswirednetworkconfiguration-list?view=graph-rest-beta) | [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) objects. |
| [Get windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswirednetworkconfiguration-get?view=graph-rest-beta) | [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) object. |
| [Create windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswirednetworkconfiguration-create?view=graph-rest-beta) | [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) | Create a new [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) object. |
| [Delete windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswirednetworkconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta). |
| [Update windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswirednetworkconfiguration-update?view=graph-rest-beta) | [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) | Update the properties of a [windowsWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswirednetworkconfiguration?view=graph-rest-beta) object. |

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
| authenticationType | [wiredNetworkAuthenticationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wirednetworkauthenticationtype?view=graph-rest-beta) | Specify whether to authenticate the user, the device, either, or to use guest authentication \(none\). If you're using certificate authentication, make sure the certificate type matches the authentication type. Possible values are: `none`, `user`, `machine`, `machineOrUser`, `guest`. Possible values are: `none`, `user`, `machine`, `machineOrUser`, `guest`, `unknownFutureValue`. |
| cacheCredentials | Boolean | When TRUE, caches user credentials on the device so that users don't need to keep entering them each time they connect. When FALSE, do not cache credentials. Default value is FALSE. |
| authenticationPeriodInSeconds | Int32 | Specify the number of seconds for the client to wait after an authentication attempt before failing. Valid range 1-3600. |
| authenticationRetryDelayPeriodInSeconds | Int32 | Specify the number of seconds between a failed authentication and the next authentication attempt. Valid range 1-3600. |
| eapolStartPeriodInSeconds | Int32 | Specify the number of seconds to wait before sending an EAPOL \(Extensible Authentication Protocol over LAN\) Start message. Valid range 1-3600. |
| maximumEAPOLStartMessages | Int32 | Specify the maximum number of EAPOL \(Extensible Authentication Protocol over LAN\) Start messages to be sent before returning failure. Valid range 1-100. |
| maximumAuthenticationFailures | Int32 | Specify the maximum authentication failures allowed for a set of credentials. Valid range 1-100. |
| enforce8021X | Boolean | When TRUE, the automatic configuration service for wired networks requires the use of 802.1X for port authentication. When FALSE, 802.1X is not required. Default value is FALSE. |
| authenticationBlockPeriodInMinutes | Int32 | Specify the duration for which automatic authentication attempts will be blocked from occuring after a failed authentication attempt. |
| eapType | [eapType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-eaptype?view=graph-rest-beta) | Extensible Authentication Protocol \(EAP\). Indicates the type of EAP protocol set on the Wi-Fi endpoint \(router\). Possible values are: `eapTls`, `leap`, `eapSim`, `eapTtls`, `peap`, `eapFast`, `teap`. Possible values are: `eapTls`, `leap`, `eapSim`, `eapTtls`, `peap`, `eapFast`, `teap`. |
| trustedServerCertificateNames | String collection | Specify trusted server certificate names. |
| authenticationMethod | [wiredNetworkAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wirednetworkauthenticationmethod?view=graph-rest-beta) | Specify the authentication method. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`, `unknownFutureValue`. |
| secondaryAuthenticationMethod | [wiredNetworkAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wirednetworkauthenticationmethod?view=graph-rest-beta) | Specify the secondary authentication method. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`, `unknownFutureValue`. |
| innerAuthenticationProtocolForEAPTTLS | [nonEapAuthenticationMethodForEapTtlsType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-noneapauthenticationmethodforeapttlstype?view=graph-rest-beta) | Specify inner authentication protocol for EAP TTLS. Possible values are: `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo`. Possible values are: `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo`. |
| outerIdentityPrivacyTemporaryValue | String | Specify the string to replace usernames for privacy when using EAP TTLS or PEAP. |
| performServerValidation | Boolean | When TRUE, enables verification of server's identity by validating the certificate when EAP type is selected as PEAP. When FALSE, the certificate is not validated. Default value is TRUE. |
| disableUserPromptForServerValidation | Boolean | When TRUE, prevents the user from being prompted to authorize new servers for trusted certification authorities when EAP type is selected as PEAP. When FALSE, does not prevent the user from being prompted. Default value is FALSE. |
| requireCryptographicBinding | Boolean | When TRUE, enables cryptographic binding when EAP type is selected as PEAP. When FALSE, does not enable cryptogrpahic binding. Default value is TRUE. |
| forceFIPSCompliance | Boolean | When TRUE, forces FIPS compliance. When FALSE, does not enable FIPS compliance. Default value is FALSE. |

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
| rootCertificatesForServerValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) collection | Specify root certificates for server validation. This collection can contain a maximum of 500 elements. |
| identityCertificateForClientAuthentication | [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta) | Specify identity certificate for client authentication. |
| secondaryIdentityCertificateForClientAuthentication | [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta) | Specify secondary identity certificate for client authentication. |
| rootCertificateForClientValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) | Specify root certificate for client validation. |
| secondaryRootCertificateForClientValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) | Specify secondary root certificate for client validation. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsWiredNetworkConfiguration",
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
  "authenticationType": "String",
  "cacheCredentials": true,
  "authenticationPeriodInSeconds": 1024,
  "authenticationRetryDelayPeriodInSeconds": 1024,
  "eapolStartPeriodInSeconds": 1024,
  "maximumEAPOLStartMessages": 1024,
  "maximumAuthenticationFailures": 1024,
  "enforce8021X": true,
  "authenticationBlockPeriodInMinutes": 1024,
  "eapType": "String",
  "trustedServerCertificateNames": [
    "String"
  ],
  "authenticationMethod": "String",
  "secondaryAuthenticationMethod": "String",
  "innerAuthenticationProtocolForEAPTTLS": "String",
  "outerIdentityPrivacyTemporaryValue": "String",
  "performServerValidation": true,
  "disableUserPromptForServerValidation": true,
  "requireCryptographicBinding": true,
  "forceFIPSCompliance": true
}
```
