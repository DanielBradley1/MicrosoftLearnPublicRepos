<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# macOSEnterpriseWiFiConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS Wi-Fi WPA-Enterprise/WPA2-Enterprise configuration profile.

Inherits from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSEnterpriseWiFiConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosenterprisewificonfiguration-list?view=graph-rest-beta) | [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) collection | List properties and relationships of the [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) objects. |
| [Get macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosenterprisewificonfiguration-get?view=graph-rest-beta) | [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) | Read properties and relationships of the [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) object. |
| [Create macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosenterprisewificonfiguration-create?view=graph-rest-beta) | [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) | Create a new [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) object. |
| [Delete macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosenterprisewificonfiguration-delete?view=graph-rest-beta) | None | Deletes a [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta). |
| [Update macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosenterprisewificonfiguration-update?view=graph-rest-beta) | [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) | Update the properties of a [macOSEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosenterprisewificonfiguration?view=graph-rest-beta) object. |

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
| networkName | String | Indicates the Wi-Fi configuration profile name. Used to identify the configuration profile. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| ssid | String | This is the name of the Wi-Fi network that is broadcast to all devices. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| connectAutomatically | Boolean | Indicates whether to automatically connect to this network when it is in range of the device. When TRUE will skip the user prompt and automatically connect the device to Wi-Fi network. Default is false. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| connectWhenNetworkNameIsHidden | Boolean | Indicates whether the device should connect to the network when it is not broadcasting its name \(SSID\). When TRUE, this profile forces the device to connect to a network that doesn't broadcast its SSID to all devices. Default is false. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| wiFiSecurityType | [wiFiSecurityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifisecuritytype?view=graph-rest-beta) | Indicates whether the Wi-Fi endpoint uses an EAP-based security type. Possible values are: open, wpaPersonal, wpaEnterprise, wep, wpa2Personal, and wpa2Enterprise Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta). Possible values are: `open`, `wpaPersonal`, `wpaEnterprise`, `wep`, `wpa2Personal`, `wpa2Enterprise`, `unknownFutureValue`, `wpa3Personal`. |
| proxySettings | [wiFiProxySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiproxysetting?view=graph-rest-beta) | Proxy Type for this Wi-Fi connection Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta). Possible values are: `none`, `manual`, `automatic`, `unknownFutureValue`. |
| proxyManualAddress | String | Indicates IP Address or DNS hostname of the proxy server when manual configuration is selected. Used for proxy settings. Example: 10.0.0.2 Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| proxyManualPort | Int32 | Indicates the proxy server TCP port to use when proxySettings is manual. Used for proxy settings. Example: 8080 Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| proxyAutomaticConfigurationUrl | String | Indicates URL of the proxy server automatic configuration \(PAC\) script when proxySettings is automatic. Used to find the location of PAC \(Proxy Auto Configuration\) file. Example: itproxy.contoso.com Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| deploymentChannel | [appleDeploymentChannel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-appledeploymentchannel?view=graph-rest-beta) | Indicates the deployment channel type used to deploy the configuration profile. Once set, cannot be changed. Possible values are deviceChannel, and userChannel. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta). Possible values are: `deviceChannel`, `userChannel`, `unknownFutureValue`. |
| wifiRequirePhysicalMacAddressEnabled | Boolean | Indicates whether devices connecting with this Wi-Fi profile must use their physical MAC address instead of a randomized MAC address. When TRUE, it uses the actual Wi-Fi MAC address. When FALSE, it enables the MAC address randomization. Applies to macOS 15 and later. Default is false. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| preSharedKey | String | This is the pre-shared key for WPA Personal Wi-Fi network. Inherited from [macOSWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoswificonfiguration?view=graph-rest-beta) |
| eapType | [eapType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-eaptype?view=graph-rest-beta) | Extensible Authentication Protocol \(EAP\). Indicates the type of EAP protocol set on the Wi-Fi endpoint \(router\). Possible values are: `eapTls`, `leap`, `eapSim`, `eapTtls`, `peap`, `eapFast`, `teap`. |
| eapFastConfiguration | [eapFastConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-eapfastconfiguration?view=graph-rest-beta) | EAP-FAST Configuration Option when EAP-FAST is the selected EAP Type. Possible values are: `noProtectedAccessCredential`, `useProtectedAccessCredential`, `useProtectedAccessCredentialAndProvision`, `useProtectedAccessCredentialAndProvisionAnonymously`. |
| trustedServerCertificateNames | String collection | Trusted server certificate names when EAP Type is configured to EAP-TLS/TTLS/FAST or PEAP. This is the common name used in the certificates issued by your trusted certificate authority \(CA\). If you provide this information, you can bypass the dynamic trust dialog that is displayed on end users devices when they connect to this Wi-Fi network. |
| authenticationMethod | [wiFiAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiauthenticationmethod?view=graph-rest-beta) | Authentication Method when EAP Type is configured to PEAP or EAP-TTLS. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`. |
| innerAuthenticationProtocolForEapTtls | [nonEapAuthenticationMethodForEapTtlsType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-noneapauthenticationmethodforeapttlstype?view=graph-rest-beta) | Non-EAP Method for Authentication \(Inner Identity\) when EAP Type is EAP-TTLS and Authenticationmethod is Username and Password. Possible values are: `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo`. |
| outerIdentityPrivacyTemporaryValue | String | Enable identity privacy \(Outer Identity\) when EAP Type is configured to EAP-TTLS, EAP-FAST or PEAP. This property masks usernames with the text you enter. For example, if you use 'anonymous', each user that authenticates with this Wi-Fi connection using their real username is displayed as 'anonymous'. |

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
| rootCertificateForServerValidation | [macOSTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macostrustedrootcertificate?view=graph-rest-beta) | Trusted Root Certificate for Server Validation when EAP Type is configured to EAP-TLS/TTLS/FAST or PEAP. |
| rootCertificatesForServerValidation | [macOSTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macostrustedrootcertificate?view=graph-rest-beta) collection | Trusted Root Certificates for Server Validation when EAP Type is configured to EAP-TLS/TTLS/FAST or PEAP. If you provide this value you do not need to provide trustedServerCertificateNames, and vice versa. This collection can contain a maximum of 500 elements. |
| identityCertificateForClientAuthentication | [macOSCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscertificateprofilebase?view=graph-rest-beta) | Identity Certificate for client authentication when EAP Type is configured to EAP-TLS, EAP-TTLS \(with Certificate Authentication\), or PEAP \(with Certificate Authentication\). |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSEnterpriseWiFiConfiguration",
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
  "networkName": "String",
  "ssid": "String",
  "connectAutomatically": true,
  "connectWhenNetworkNameIsHidden": true,
  "wiFiSecurityType": "String",
  "proxySettings": "String",
  "proxyManualAddress": "String",
  "proxyManualPort": 1024,
  "proxyAutomaticConfigurationUrl": "String",
  "deploymentChannel": "String",
  "wifiRequirePhysicalMacAddressEnabled": true,
  "preSharedKey": "String",
  "eapType": "String",
  "eapFastConfiguration": "String",
  "trustedServerCertificateNames": [
    "String"
  ],
  "authenticationMethod": "String",
  "innerAuthenticationProtocolForEapTtls": "String",
  "outerIdentityPrivacyTemporaryValue": "String"
}
```
