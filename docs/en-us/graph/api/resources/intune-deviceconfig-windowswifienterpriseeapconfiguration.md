<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windowsWifiEnterpriseEAPConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity provides descriptions of the declared methods, properties and relationships exposed by the Wifi CSP.

Inherits from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsWifiEnterpriseEAPConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswifienterpriseeapconfiguration-list?view=graph-rest-beta) | [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) objects. |
| [Get windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswifienterpriseeapconfiguration-get?view=graph-rest-beta) | [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) object. |
| [Create windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswifienterpriseeapconfiguration-create?view=graph-rest-beta) | [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) | Create a new [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) object. |
| [Delete windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswifienterpriseeapconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta). |
| [Update windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowswifienterpriseeapconfiguration-update?view=graph-rest-beta) | [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) | Update the properties of a [windowsWifiEnterpriseEAPConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswifienterpriseeapconfiguration?view=graph-rest-beta) object. |

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
| wifiSecurityType | [wiFiSecurityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifisecuritytype?view=graph-rest-beta) | Specify the Wifi Security Type. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta). Possible values are: `open`, `wpaPersonal`, `wpaEnterprise`, `wep`, `wpa2Personal`, `wpa2Enterprise`, `unknownFutureValue`, `wpa3Personal`. |
| meteredConnectionLimit | [meteredConnectionLimitType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-meteredconnectionlimittype?view=graph-rest-beta) | Specify the metered connection limit type for the wifi connection. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta). Possible values are: `unrestricted`, `fixed`, `variable`. |
| ssid | String | Specify the SSID of the wifi connection. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| networkName | String | Specify the network configuration name. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| connectAutomatically | Boolean | Specify whether the wifi connection should connect automatically when in range. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| connectToPreferredNetwork | Boolean | Specify whether the wifi connection should connect to more preferred networks when already connected to this one. Requires ConnectAutomatically to be true. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| connectWhenNetworkNameIsHidden | Boolean | Specify whether the wifi connection should connect automatically even when the SSID is not broadcasting. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| proxySetting | [wiFiProxySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiproxysetting?view=graph-rest-beta) | Specify the proxy setting for Wi-Fi configuration Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta). Possible values are: `none`, `manual`, `automatic`, `unknownFutureValue`. |
| proxyManualAddress | String | Specify the IP address for the proxy server. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| proxyManualPort | Int32 | Specify the port for the proxy server. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| proxyAutomaticConfigurationUrl | String | Specify the URL for the proxy server configuration script. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| forceFIPSCompliance | Boolean | Specify whether to force FIPS compliance. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| preSharedKey | String | This is the pre-shared key for WPA Personal Wi-Fi network. Inherited from [windowsWifiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowswificonfiguration?view=graph-rest-beta) |
| networkSingleSignOn | [networkSingleSignOnType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-networksinglesignontype?view=graph-rest-beta) | Specify the network single sign on type. Possible values are: `disabled`, `prelogon`, `postlogon`. |
| maximumAuthenticationTimeoutInSeconds | Int32 | Specify maximum authentication timeout \(in seconds\). Valid range: 1-120 |
| userBasedVirtualLan | Boolean | Specifiy whether to change the virtual LAN used by the device based on the user’s credentials. Cannot be used when NetworkSingleSignOnType is set to ​Disabled. |
| promptForAdditionalAuthenticationCredentials | Boolean | Specify whether the wifi connection should prompt for additional authentication credentials. |
| enablePairwiseMasterKeyCaching | Boolean | Specify whether the wifi connection should enable pairwise master key caching. |
| maximumPairwiseMasterKeyCacheTimeInMinutes | Int32 | Specify maximum pairwise master key cache time \(in minutes\). Valid range: 5-1440 |
| maximumNumberOfPairwiseMasterKeysInCache | Int32 | Specify maximum number of pairwise master keys in cache. Valid range: 1-255 |
| enablePreAuthentication | Boolean | Specify whether pre-authentication should be enabled. |
| maximumPreAuthenticationAttempts | Int32 | Specify maximum pre-authentication attempts. Valid range: 1-16 |
| eapType | [eapType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-eaptype?view=graph-rest-beta) | Extensible Authentication Protocol \(EAP\). Indicates the type of EAP protocol set on the Wi-Fi endpoint \(router\). Possible values are: `eapTls`, `leap`, `eapSim`, `eapTtls`, `peap`, `eapFast`, `teap`. |
| trustedServerCertificateNames | String collection | Specify trusted server certificate names. |
| authenticationMethod | [wiFiAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiauthenticationmethod?view=graph-rest-beta) | Specify the authentication method. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`. |
| innerAuthenticationProtocolForEAPTTLS | [nonEapAuthenticationMethodForEapTtlsType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-noneapauthenticationmethodforeapttlstype?view=graph-rest-beta) | Specify inner authentication protocol for EAP TTLS. Possible values are: `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo`. |
| outerIdentityPrivacyTemporaryValue | String | Specify the string to replace usernames for privacy when using EAP TTLS or PEAP. |
| requireCryptographicBinding | Boolean | Specify whether to enable cryptographic binding when EAP type is selected as PEAP. |
| performServerValidation | Boolean | Specify whether to enable verification of server's identity by validating the certificate when EAP type is selected as PEAP. |
| disableUserPromptForServerValidation | Boolean | Specify whether to prevent the user from being prompted to authorize new servers for trusted certification authorities when EAP type is selected as PEAP. |
| authenticationPeriodInSeconds | Int32 | Specify the number of seconds for the client to wait after an authentication attempt before failing. Valid range 1-3600. |
| authenticationRetryDelayPeriodInSeconds | Int32 | Specify the number of seconds between a failed authentication and the next authentication attempt. Valid range 1-3600. |
| eapolStartPeriodInSeconds | Int32 | Specify the number of seconds to wait before sending an EAPOL \(Extensible Authentication Protocol over LAN\) Start message. Valid range 1-3600. |
| maximumEAPOLStartMessages | Int32 | Specifiy the maximum number of EAPOL \(Extensible Authentication Protocol over LAN\) Start messages to be sent before returning failure. Valid range 1-100. |
| maximumAuthenticationFailures | Int32 | Specify the maximum authentication failures allowed for a set of credentials. Valid range 1-100. |
| cacheCredentials | Boolean | Specify whether to cache user credentials on the device so that users don’t need to keep entering them each time they connect. |
| authenticationType | [wifiAuthenticationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiauthenticationtype?view=graph-rest-beta) | Specify whether to authenticate the user, the device, either, or to use guest authentication \(none\). If you’re using certificate authentication, make sure the certificate type matches the authentication type. Possible values are: `none`, `user`, `machine`, `machineOrUser`, `guest`. |

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
| rootCertificatesForServerValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) collection | Specify root certificate for server validation. This collection can contain a maximum of 500 elements. |
| identityCertificateForClientAuthentication | [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta) | Specify identity certificate for client authentication. |
| rootCertificateForClientValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) | Specify root certificate for client validation. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsWifiEnterpriseEAPConfiguration",
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
  "wifiSecurityType": "String",
  "meteredConnectionLimit": "String",
  "ssid": "String",
  "networkName": "String",
  "connectAutomatically": true,
  "connectToPreferredNetwork": true,
  "connectWhenNetworkNameIsHidden": true,
  "proxySetting": "String",
  "proxyManualAddress": "String",
  "proxyManualPort": 1024,
  "proxyAutomaticConfigurationUrl": "String",
  "forceFIPSCompliance": true,
  "preSharedKey": "String",
  "networkSingleSignOn": "String",
  "maximumAuthenticationTimeoutInSeconds": 1024,
  "userBasedVirtualLan": true,
  "promptForAdditionalAuthenticationCredentials": true,
  "enablePairwiseMasterKeyCaching": true,
  "maximumPairwiseMasterKeyCacheTimeInMinutes": 1024,
  "maximumNumberOfPairwiseMasterKeysInCache": 1024,
  "enablePreAuthentication": true,
  "maximumPreAuthenticationAttempts": 1024,
  "eapType": "String",
  "trustedServerCertificateNames": [
    "String"
  ],
  "authenticationMethod": "String",
  "innerAuthenticationProtocolForEAPTTLS": "String",
  "outerIdentityPrivacyTemporaryValue": "String",
  "requireCryptographicBinding": true,
  "performServerValidation": true,
  "disableUserPromptForServerValidation": true,
  "authenticationPeriodInSeconds": 1024,
  "authenticationRetryDelayPeriodInSeconds": 1024,
  "eapolStartPeriodInSeconds": 1024,
  "maximumEAPOLStartMessages": 1024,
  "maximumAuthenticationFailures": 1024,
  "cacheCredentials": true,
  "authenticationType": "String"
}
```
