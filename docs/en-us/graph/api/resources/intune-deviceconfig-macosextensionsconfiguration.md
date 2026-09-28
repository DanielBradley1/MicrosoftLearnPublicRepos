<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# macOSExtensionsConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS extensions configuration profile.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSExtensionsConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosextensionsconfiguration-list?view=graph-rest-beta) | [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) objects. |
| [Get macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosextensionsconfiguration-get?view=graph-rest-beta) | [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) | Read properties and relationships of the [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) object. |
| [Create macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosextensionsconfiguration-create?view=graph-rest-beta) | [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) | Create a new [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) object. |
| [Delete macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosextensionsconfiguration-delete?view=graph-rest-beta) | None | Deletes a [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta). |
| [Update macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macosextensionsconfiguration-update?view=graph-rest-beta) | [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) | Update the properties of a [macOSExtensionsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macosextensionsconfiguration?view=graph-rest-beta) object. |

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
| kernelExtensionOverridesAllowed | Boolean | If set to true, users can approve additional kernel extensions not explicitly allowed by configurations profiles. |
| kernelExtensionAllowedTeamIdentifiers | String collection | All kernel extensions validly signed by the team identifiers in this list will be allowed to load. |
| kernelExtensionsAllowed | [macOSKernelExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoskernelextension?view=graph-rest-beta) collection | A list of kernel extensions that will be allowed to load. . This collection can contain a maximum of 500 elements. |
| systemExtensionsBlockOverride | Boolean | Gets or sets whether to allow the user to approve additional system extensions not explicitly allowed by configuration profiles. |
| systemExtensionsAllowedTeamIdentifiers | String collection | Gets or sets a list of allowed team identifiers. Any system extension signed with any of the specified team identifiers will be approved. |
| systemExtensionsAllowed | [macOSSystemExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossystemextension?view=graph-rest-beta) collection | Gets or sets a list of allowed macOS system extensions. This collection can contain a maximum of 500 elements. |
| systemExtensionsAllowedTypes | [macOSSystemExtensionTypeMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossystemextensiontypemapping?view=graph-rest-beta) collection | Gets or sets a list of allowed macOS system extension types. This collection can contain a maximum of 500 elements. |

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
  "@odata.type": "#microsoft.graph.macOSExtensionsConfiguration",
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
  "kernelExtensionOverridesAllowed": true,
  "kernelExtensionAllowedTeamIdentifiers": [
    "String"
  ],
  "kernelExtensionsAllowed": [
    {
      "@odata.type": "microsoft.graph.macOSKernelExtension",
      "teamIdentifier": "String",
      "bundleId": "String"
    }
  ],
  "systemExtensionsBlockOverride": true,
  "systemExtensionsAllowedTeamIdentifiers": [
    "String"
  ],
  "systemExtensionsAllowed": [
    {
      "@odata.type": "microsoft.graph.macOSSystemExtension",
      "teamIdentifier": "String",
      "bundleId": "String"
    }
  ],
  "systemExtensionsAllowedTypes": [
    {
      "@odata.type": "microsoft.graph.macOSSystemExtensionTypeMapping",
      "teamIdentifier": "String",
      "allowedTypes": "String"
    }
  ]
}
```
