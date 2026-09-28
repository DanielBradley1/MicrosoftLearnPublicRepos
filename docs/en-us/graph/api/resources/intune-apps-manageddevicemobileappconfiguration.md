<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# managedDeviceMobileAppConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An abstract class for Mobile app configuration for enrolled devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceMobileAppConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfiguration-list?view=graph-rest-1.0) | [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) objects. |
| [Get managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfiguration-get?view=graph-rest-1.0) | [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-apps-manageddevicemobileappconfiguration-assign?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| targetedMobileApps | String collection | the associated app. |
| createdDateTime | DateTimeOffset | DateTime the object was created. |
| description | String | Admin provided description of the Device Configuration. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| displayName | String | Admin provided name of the device configuration. |
| version | Int32 | Version of the device configuration. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) collection | The list of group assignemenets for app configration. |
| deviceStatuses | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) collection | List of ManagedDeviceMobileAppConfigurationDeviceStatus. |
| userStatuses | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) collection | List of ManagedDeviceMobileAppConfigurationUserStatus. |
| deviceStatusSummary | [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0) | App configuration device status summary. |
| userStatusSummary | [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0) | App configuration user status summary. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceMobileAppConfiguration",
  "id": "String (identifier)",
  "targetedMobileApps": [
    "String"
  ],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024
}
```
