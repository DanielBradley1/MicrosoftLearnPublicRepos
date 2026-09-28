<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# iosScepCertificateProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

iOS SCEP certificate profile.

Inherits from [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosScepCertificateProfiles](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosscepcertificateprofile-list?view=graph-rest-beta) | [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) collection | List properties and relationships of the [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) objects. |
| [Get iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosscepcertificateprofile-get?view=graph-rest-beta) | [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) | Read properties and relationships of the [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) object. |
| [Create iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosscepcertificateprofile-create?view=graph-rest-beta) | [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) | Create a new [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) object. |
| [Delete iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosscepcertificateprofile-delete?view=graph-rest-beta) | None | Deletes a [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta). |
| [Update iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosscepcertificateprofile-update?view=graph-rest-beta) | [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) | Update the properties of a [iosScepCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosscepcertificateprofile?view=graph-rest-beta) object. |

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
| renewalThresholdPercentage | Int32 | Certificate renewal threshold percentage. Valid values 1 to 99 Inherited from [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta) |
| subjectNameFormat | [appleSubjectNameFormat](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applesubjectnameformat?view=graph-rest-beta) | Certificate Subject Name Format. Inherited from [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta). Possible values are: `commonName`, `commonNameAsEmail`, `custom`, `commonNameIncludingEmail`, `commonNameAsIMEI`, `commonNameAsSerialNumber`. |
| subjectAlternativeNameType | [subjectAlternativeNameType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-subjectalternativenametype?view=graph-rest-beta) | Certificate Subject Alternative Name type. Inherited from [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta). Possible values are: `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier`. |
| certificateValidityPeriodValue | Int32 | Value for the Certificate Validity Period. Inherited from [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta) |
| certificateValidityPeriodScale | [certificateValidityPeriodScale](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatevalidityperiodscale?view=graph-rest-beta) | Scale for the Certificate Validity Period. Inherited from [iosCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscertificateprofilebase?view=graph-rest-beta). Possible values are: `days`, `months`, `years`. |
| scepServerUrls | String collection | SCEP Server Url\(s\). |
| subjectNameFormatString | String | Custom format to use with SubjectNameFormat = Custom. Example: CN={{EmailAddress}},E={{EmailAddress}},OU=Enterprise Users,O=Contoso Corporation,L=Redmond,ST=WA,C=US |
| keyUsage | [keyUsages](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyusages?view=graph-rest-beta) | SCEP Key Usage. Possible values are: `keyEncipherment`, `digitalSignature`. |
| keySize | [keySize](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keysize?view=graph-rest-beta) | SCEP Key Size. Possible values are: `size1024`, `size2048`, `size4096`. |
| extendedKeyUsages | [extendedKeyUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-extendedkeyusage?view=graph-rest-beta) collection | Extended Key Usage \(EKU\) settings. This collection can contain a maximum of 500 elements. |
| subjectAlternativeNameFormatString | String | Custom String that defines the AAD Attribute. |
| certificateStore | [certificateStore](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatestore?view=graph-rest-beta) | Target store certificate. Possible values are: `user`, `machine`. |
| customSubjectAlternativeNames | [customSubjectAlternativeName](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-customsubjectalternativename?view=graph-rest-beta) collection | Custom Subject Alternative Name Settings. The OnPremisesUserPrincipalName variable is support as well as others documented here: [https://go.microsoft.com/fwlink/?LinkId=2027630](https://go.microsoft.com/fwlink/?LinkId=2027630). This collection can contain a maximum of 500 elements. |

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
| rootCertificate | [iosTrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iostrustedrootcertificate?view=graph-rest-beta) | Trusted Root Certificate. |
| managedDeviceCertificateStates | [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) collection | Certificate state for devices. This collection can contain a maximum of 2147483647 elements. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosScepCertificateProfile",
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
  "renewalThresholdPercentage": 1024,
  "subjectNameFormat": "String",
  "subjectAlternativeNameType": "String",
  "certificateValidityPeriodValue": 1024,
  "certificateValidityPeriodScale": "String",
  "scepServerUrls": [
    "String"
  ],
  "subjectNameFormatString": "String",
  "keyUsage": "String",
  "keySize": "String",
  "extendedKeyUsages": [
    {
      "@odata.type": "microsoft.graph.extendedKeyUsage",
      "name": "String",
      "objectIdentifier": "String"
    }
  ],
  "subjectAlternativeNameFormatString": "String",
  "certificateStore": "String",
  "customSubjectAlternativeNames": [
    {
      "@odata.type": "microsoft.graph.customSubjectAlternativeName",
      "sanType": "String",
      "name": "String"
    }
  ]
}
```
