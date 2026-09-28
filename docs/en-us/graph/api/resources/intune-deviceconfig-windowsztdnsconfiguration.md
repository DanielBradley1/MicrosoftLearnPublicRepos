<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# windowsZtdnsConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Zero Trust DNS configuration profile

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsZtdnsConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-list?view=graph-rest-beta) | [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) objects. |
| [Get windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-get?view=graph-rest-beta) | [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) object. |
| [Create windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-create?view=graph-rest-beta) | [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) | Create a new [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) object. |
| [Delete windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta). |
| [Update windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-update?view=graph-rest-beta) | [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) | Update the properties of a [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) object. |

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
| auditModeEnabled | Boolean | Indicates the audit operational mode. When true, unsecured traffic will be logged but not blocked. When false, unsecured DNS traffic will be blocked unless specifically exempted. |
| exemptionRules | [windowsZtdnsExemptionRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsexemptionrule?view=graph-rest-beta) collection | Exemptions to the ZTDNS rules, allowing access to specific addresses or subnets via unsecured lookup. This collection can contain a maximum of 500 elements. |
| extendedKeyUsagesForClientAuthentication | [extendedKeyUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-extendedkeyusage?view=graph-rest-beta) collection | Extended key usage definitions for client authentication with secure DNS servers. This collection can contain a maximum of 500 elements. |
| hostsFileResolutionEnabled | Boolean | Indicates whether the DNS Client can resolve queries using the hosts file. |
| loopbackDnsForwarderEnabled | Boolean | Creates a localhost DNS server for securely forwarding plaintext queries to trusted DNS servers. |
| loopbackTrafficBlocked | Boolean | Indicates whether traffic to loopback addresses should be blocked. |
| maximumConnectionTimeInSeconds | Int32 | Maximum time in seconds for which connections to an IP address will be allowed after successful name resolution. Valid values 30 to 604800 |
| secureDnsServers | [windowsZtdnsSecureDnsServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnssecurednsserver?view=graph-rest-beta) collection | Collection of secure DNS servers used to resolve ZTDNS queries. Must contain at least one item. This collection can contain a maximum of 500 elements. |

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
| rootCertificatesForClientValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) collection | Root certificates for client authentication. This collection can contain a maximum of 500 elements. |
| rootCertificatesForServerValidation | [windows81TrustedRootCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81trustedrootcertificate?view=graph-rest-beta) collection | Root certificates for server validation. This collection can contain a maximum of 500 elements. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsZtdnsConfiguration",
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
  "auditModeEnabled": true,
  "exemptionRules": [
    {
      "@odata.type": "microsoft.graph.windowsZtdnsExemptionRule",
      "description": "String",
      "displayName": "String",
      "ipAddresses": [
        "String"
      ]
    }
  ],
  "extendedKeyUsagesForClientAuthentication": [
    {
      "@odata.type": "microsoft.graph.extendedKeyUsage",
      "name": "String",
      "objectIdentifier": "String"
    }
  ],
  "hostsFileResolutionEnabled": true,
  "loopbackDnsForwarderEnabled": true,
  "loopbackTrafficBlocked": true,
  "maximumConnectionTimeInSeconds": 1024,
  "secureDnsServers": [
    {
      "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServer",
      "displayName": "String",
      "dnsOverHttpsConfiguration": {
        "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServerDnsOverHttpsConfiguration",
        "httpsPort": 1024,
        "queryUrl": "String"
      },
      "dnsOverTlsConfiguration": {
        "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServerDnsOverTlsConfiguration",
        "certificateSubjectName": "String",
        "tlsPort": 1024
      },
      "ipAddress": "String"
    }
  ]
}
```
