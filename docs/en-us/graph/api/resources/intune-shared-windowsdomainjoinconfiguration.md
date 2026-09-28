<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-14 -->

# windowsDomainJoinConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Domain Join device configuration.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |  |
| :--- | :--- | :--- | --- |
| [List windowsDomainJoinConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsdomainjoinconfiguration-list?view=graph-rest-beta) | [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) objects. |  |
| [Get windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsdomainjoinconfiguration-get?view=graph-rest-beta) | [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) | Read properties and relationships of the [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) object. |  |
| [Create windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsdomainjoinconfiguration-create?view=graph-rest-beta) | [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) | Create a new [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) object. |  |
| [Delete windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsdomainjoinconfiguration-delete?view=graph-rest-beta) | None | Deletes a [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta). | Delete a [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) object. |
| [Update windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-windowsdomainjoinconfiguration-update?view=graph-rest-beta) | [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) | Update the properties of a [windowsDomainJoinConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-windowsdomainjoinconfiguration?view=graph-rest-beta) object. |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| **Device configuration** |  |  |
| activeDirectoryDomainName | String | Active Directory domain name to join. |
| computerNameStaticPrefix | String | Fixed prefix to be used for computer name. |
| computerNameSuffixRandomCharCount | Int32 | Dynamically generated characters used as suffix for computer name. Valid values 3 to 14 |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| organizationalUnit | String | Organizational unit \(OU\) where the computer account will be created. If this parameter is NULL, the well known computer object container will be used as published in the domain. |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| supportsScopeTags | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Device configuration** |  |  |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-beta) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-beta) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-beta) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| groupAssignments | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| networkAccessConfigurations | [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) collection | Reference to device configurations required for network connectivity |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-beta) collection | Device configuration installation stauts by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-beta) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource. Note: The response object shown here may be truncated for brevity. Response objects will contain properties relevant to the context of the call.

```json
{
  "@odata.type": "#microsoft.graph.windowsDomainJoinConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "computerNameStaticPrefix": "String",
  "computerNameSuffixRandomCharCount": 1024,
  "activeDirectoryDomainName": "String"
}
```
