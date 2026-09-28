<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81certificateprofilebase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows81CertificateProfileBase resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Configuration.

Inherits from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows81CertificateProfileBases](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81certificateprofilebase-list?view=graph-rest-beta) | [windows81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81certificateprofilebase?view=graph-rest-beta) collection | List properties and relationships of the [windows81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81certificateprofilebase?view=graph-rest-beta) objects. |
| [Get windows81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81certificateprofilebase-get?view=graph-rest-beta) | [windows81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81certificateprofilebase?view=graph-rest-beta) | Read properties and relationships of the [windows81CertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81certificateprofilebase?view=graph-rest-beta) object. |

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
| renewalThresholdPercentage | Int32 | Certificate renewal threshold percentage. Valid values 1 to 99 Inherited from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta) |
| keyStorageProvider | [keyStorageProviderOption](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keystorageprovideroption?view=graph-rest-beta) | Key Storage Provider \(KSP\) Inherited from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta). Possible values are: `useTpmKspOtherwiseUseSoftwareKsp`, `useTpmKspOtherwiseFail`, `usePassportForWorkKspOtherwiseFail`, `useSoftwareKsp`. |
| subjectNameFormat | [subjectNameFormat](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-subjectnameformat?view=graph-rest-beta) | Certificate Subject Name Format Inherited from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta). Possible values are: `commonName`, `commonNameIncludingEmail`, `commonNameAsEmail`, `custom`, `commonNameAsIMEI`, `commonNameAsSerialNumber`, `commonNameAsAadDeviceId`, `commonNameAsIntuneDeviceId`, `commonNameAsDurableDeviceId`. |
| subjectAlternativeNameType | [subjectAlternativeNameType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-subjectalternativenametype?view=graph-rest-beta) | Certificate Subject Alternative Name Type Inherited from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta). Possible values are: `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier`. |
| certificateValidityPeriodValue | Int32 | Value for the Certificate Validity Period Inherited from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta) |
| certificateValidityPeriodScale | [certificateValidityPeriodScale](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatevalidityperiodscale?view=graph-rest-beta) | Scale for the Certificate Validity Period Inherited from [windowsCertificateProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowscertificateprofilebase?view=graph-rest-beta). Possible values are: `days`, `months`, `years`. |
| extendedKeyUsages | [extendedKeyUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-extendedkeyusage?view=graph-rest-beta) collection | Extended Key Usage \(EKU\) settings. This collection can contain a maximum of 500 elements. |
| customSubjectAlternativeNames | [customSubjectAlternativeName](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-customsubjectalternativename?view=graph-rest-beta) collection | Custom Subject Alternative Name Settings. This collection can contain a maximum of 500 elements. |

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

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows81CertificateProfileBase",
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
  "keyStorageProvider": "String",
  "subjectNameFormat": "String",
  "subjectAlternativeNameType": "String",
  "certificateValidityPeriodValue": 1024,
  "certificateValidityPeriodScale": "String",
  "extendedKeyUsages": [
    {
      "@odata.type": "microsoft.graph.extendedKeyUsage",
      "name": "String",
      "objectIdentifier": "String"
    }
  ],
  "customSubjectAlternativeNames": [
    {
      "@odata.type": "microsoft.graph.customSubjectAlternativeName",
      "sanType": "String",
      "name": "String"
    }
  ]
}
```
