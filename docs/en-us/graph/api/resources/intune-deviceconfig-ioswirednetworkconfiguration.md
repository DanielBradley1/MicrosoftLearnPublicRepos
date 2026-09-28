<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# iosWiredNetworkConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

IOS wired network configuration profile.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosWiredNetworkConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioswirednetworkconfiguration-list?view=graph-rest-beta) | [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) objects. |
| [Get iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioswirednetworkconfiguration-get?view=graph-rest-beta) | [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) | Read properties and relationships of the [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) object. |
| [Create iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioswirednetworkconfiguration-create?view=graph-rest-beta) | [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) | Create a new [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) object. |
| [Delete iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioswirednetworkconfiguration-delete?view=graph-rest-beta) | None | Deletes a [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta). |
| [Update iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioswirednetworkconfiguration-update?view=graph-rest-beta) | [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) | Update the properties of a [iosWiredNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkconfiguration?view=graph-rest-beta) object. |

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
| networkName | String | Network Name. |
| networkInterface | [wiredNetworkInterface](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wirednetworkinterface?view=graph-rest-beta) | Network interface. Possible values are: `anyEthernet`, `firstActiveEthernet`, `secondActiveEthernet`, `thirdActiveEthernet`, `firstEthernet`, `secondEthernet`, `thirdEthernet`. |
| eapType | [iosWiredNetworkEapType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioswirednetworkeaptype?view=graph-rest-beta) | Extensible Authentication Protocol \(EAP\). Indicates the type of EAP protocol set on the wired network. Possible values are: `eapTls`, `eapTtls`, `peap`, `eapFast`, `eapAka`, `unknownFutureValue`. |
| eapFastConfiguration | [eapFastConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-eapfastconfiguration?view=graph-rest-beta) | EAP-FAST Configuration Option when EAP-FAST is the selected EAP Type. Possible values are: `noProtectedAccessCredential`, `useProtectedAccessCredential`, `useProtectedAccessCredentialAndProvision`, `useProtectedAccessCredentialAndProvisionAnonymously`. |
| trustedServerCertificateNames | String collection | Trusted server certificate names when EAP Type is configured to EAP-TLS/TTLS or PEAP. This is the common name used in the certificates issued by your trusted certificate authority \(CA\). If you provide this information, you can bypass the dynamic trust dialog that is displayed on end users devices when they connect to this wired network. |
| authenticationMethod | [wiredNetworkAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-wirednetworkauthenticationmethod?view=graph-rest-beta) | Authentication Method when EAP Type is configured to PEAP or EAP-TTLS. Possible values are: `certificate`, `usernameAndPassword`, `derivedCredential`, `unknownFutureValue`. |
| nonEapAuthenticationMethodForEapTtls | [nonEapAuthenticationMethodForEapTtlsType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-noneapauthenticationmethodforeapttlstype?view=graph-rest-beta) | Non-EAP Method for Authentication \(Inner Identity\) when EAP Type is EAP-TTLS and Authenticationmethod is Username and Password. Possible values are: `unencryptedPassword`, `challengeHandshakeAuthenticationProtocol`, `microsoftChap`, `microsoftChapVersionTwo`. |
| outerIdentityPrivacyMaskValue | String | Enable identity privacy \(Outer Identity\) when EAP Type is configured to EAP-TLS, EAP-TTLS or PEAP. This property masks usernames with the text you enter. For example, if you use 'anonymous', each user that authenticates with this wired network using their real username is displayed as 'anonymous'. |

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
| rootCertificateForServerValidation | [iosTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iostrustedrootcertificate?view=graph-rest-beta) | Trusted Root Certificate for Server Validation when EAP Type is configured to EAP-TLS/TTLS or PEAP. |
| rootCertificatesForServerValidation | [iosTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iostrustedrootcertificate?view=graph-rest-beta) collection | Trusted Root Certificates for Server Validation when EAP Type is configured to EAP-TLS/TTLS/FAST or PEAP. If you provide this value you do not need to provide trustedServerCertificateNames, and vice versa. This collection can contain a maximum of 500 elements. |
| identityCertificateForClientAuthentication | [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta) | Identity Certificate for client authentication when EAP Type is configured to EAP-TLS, EAP-TTLS \(with Certificate Authentication\), or PEAP \(with Certificate Authentication\). |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosWiredNetworkConfiguration",
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
  "networkInterface": "String",
  "eapType": "String",
  "eapFastConfiguration": "String",
  "trustedServerCertificateNames": [
    "String"
  ],
  "authenticationMethod": "String",
  "nonEapAuthenticationMethodForEapTtls": "String",
  "outerIdentityPrivacyMaskValue": "String"
}
```
