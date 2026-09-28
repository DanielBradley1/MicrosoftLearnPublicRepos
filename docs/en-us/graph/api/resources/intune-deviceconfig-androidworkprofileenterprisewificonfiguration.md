<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# androidWorkProfileEnterpriseWiFiConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

By providing the configurations in this profile you can instruct the Android Work Profile device to connect to desired Wi-Fi endpoint. By specifying the authentication method and security types expected by Wi-Fi endpoint you can make the Wi-Fi connection seamless for end user.

Inherits from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidWorkProfileEnterpriseWiFiConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofileenterprisewificonfiguration-list?view=graph-rest-beta) | [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) collection | List properties and relationships of the [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) objects. |
| [Get androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofileenterprisewificonfiguration-get?view=graph-rest-beta) | [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) | Read properties and relationships of the [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) object. |
| [Create androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofileenterprisewificonfiguration-create?view=graph-rest-beta) | [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) | Create a new [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) object. |
| [Delete androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofileenterprisewificonfiguration-delete?view=graph-rest-beta) | None | Deletes a [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta). |
| [Update androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofileenterprisewificonfiguration-update?view=graph-rest-beta) | [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) | Update the properties of a [androidWorkProfileEnterpriseWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileenterprisewificonfiguration?view=graph-rest-beta) object. |

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
| networkName | String | The name of the Wi-Fi network. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| ssid | String | This is the name of the Wi-Fi network that is broadcast to all devices. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| connectAutomatically | Boolean | When set to true, device will connect automatically to the Wi-Fi network when in range, skipping the user prompt. When false, user will need to connect manually through Settings on the Android device. Default value is false. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| connectWhenNetworkNameIsHidden | Boolean | When set to true, this profile forces the device to connect to a network that doesn't broadcast its SSID to all devices. When false, device will not automatically connect to hidden networks. Default value is false. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| wiFiSecurityType | [androidWiFiSecurityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidwifisecuritytype?view=graph-rest-beta) | The possible security types for Android Wi-Fi profiles. Default value Open, indicates no authentication required for the network. The security protocols supported are WEP, WPA and WPA2. WpaEnterprise and Wpa2Enterprise options are available for Enterprise Wi-Fi profiles. Wep and WpaPersonal \(supports WPA and WPA2\) options are available for Basic Wi-Fi profiles. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta). Possible values are: `open`, `wpaEnterprise`, `wpa2Enterprise`, `wep`, `wpaPersonal`, `unknownFutureValue`. |
| preSharedKey | String | Specify the pre-shared key for a WEP or WPA personal Wi-Fi network. Restrictions depend on the value set for wiFiSecurityType. If WEP type security is used, then preSharedKey must be a valid passphrase \(5 or 13 characters\) or a valid HEX key \(10 or 26 hexidecimal characters\). If WPA security type is used, then preSharedKey can be any string between 8 and 64 characters long. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| preSharedKeyIsSet | Boolean | When set to true, indicates that the pre-shared key is configured. When set to false, indicates that pre-shared key is not configured \(any values set for preSharedKey will be ignored\). Default value is false. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| proxySettings | [wiFiProxySetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiproxysetting?view=graph-rest-beta) | Proxy Type for this Wi-Fi connection Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta). Possible values are: `none`, `manual`, `automatic`, `unknownFutureValue`. |
| proxyAutomaticConfigurationUrl | String | URL of the proxy server automatic configuration script when automatic configuration is selected. This URL is typically the location of PAC \(Proxy Auto Configuration\) file. Inherited from [androidWorkProfileWiFiConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilewificonfiguration?view=graph-rest-beta) |
| eapType | [androidEapType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androideaptype?view=graph-rest-beta) | Indicates the type of EAP protocol set on the Wi-Fi endpoint \(router\). Possible values are: `eapTls`, `eapTtls`, `peap`. |
| trustedServerCertificateNames | String collection | Trusted server certificate names when EAP Type is configured to EAP-TLS/TTLS/FAST or PEAP. This is the common name used in the certificates issued by your trusted certificate authority \(CA\). If you provide this information, you can bypass the dynamic trust dialog that is displayed on end users' devices when they connect to this Wi-Fi network. |
| authenticationMethod | [wiFiAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wifiauthenticationmethod?view=graph-rest-beta) | Indicates the Authentication Method the client \(device\) needs to use when the EAP Type is configured to PEAP or EAP-TTLS. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`. |
| innerAuthenticationProtocolForEapTtls | [nonEapAuthenticationMethodForEapTtlsType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-noneapauthenticationmethodforeapttlstype?view=graph-rest-beta) | Non-EAP Method for Authentication \(Inner Identity\) when EAP Type is EAP-TTLS and Authenticationmethod is Username and Password. Possible values are: `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo`. |
| innerAuthenticationProtocolForPeap | [nonEapAuthenticationMethodForPeap](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-noneapauthenticationmethodforpeap?view=graph-rest-beta) | Non-EAP Method for Authentication \(Inner Identity\) when EAP Type is PEAP and Authenticationmethod is Username and Password. Possible values are: `none`, `microsoftChapVersionTwo`. |
| outerIdentityPrivacyTemporaryValue | String | Enable identity privacy \(Outer Identity\) when EAP Type is configured to EAP-TTLS or PEAP. The String provided here is used to mask the username of individual users when they attempt to connect to Wi-Fi network. |

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
| rootCertificateForServerValidation | [androidWorkProfileTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofiletrustedrootcertificate?view=graph-rest-beta) | Trusted Root Certificate for Server Validation when EAP Type is configured to EAP-TLS, EAP-TTLS or PEAP. This is the certificate presented by the Wi-Fi endpoint when the device attempts to connect to Wi-Fi endpoint. The device \(or user\) must accept this certificate to continue the connection attempt. |
| identityCertificateForClientAuthentication | [androidWorkProfileCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilecertificateprofilebase?view=graph-rest-beta) | Identity Certificate for client authentication when EAP Type is configured to EAP-TLS, EAP-TTLS \(with Certificate Authentication\), or PEAP \(with Certificate Authentication\). This is the certificate presented by client to the Wi-Fi endpoint. The authentication server sitting behind the Wi-Fi endpoint must accept this certificate to successfully establish a Wi-Fi connection. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidWorkProfileEnterpriseWiFiConfiguration",
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
  "preSharedKey": "String",
  "preSharedKeyIsSet": true,
  "proxySettings": "String",
  "proxyAutomaticConfigurationUrl": "String",
  "eapType": "String",
  "trustedServerCertificateNames": [
    "String"
  ],
  "authenticationMethod": "String",
  "innerAuthenticationProtocolForEapTtls": "String",
  "innerAuthenticationProtocolForPeap": "String",
  "outerIdentityPrivacyTemporaryValue": "String"
}
```
