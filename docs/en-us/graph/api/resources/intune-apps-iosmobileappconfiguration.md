<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosMobileAppConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties, inherited properties and actions for iOS mobile app configurations.

Inherits from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosMobileAppConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosmobileappconfiguration-list?view=graph-rest-1.0) | [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) objects. |
| [Get iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosmobileappconfiguration-get?view=graph-rest-1.0) | [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) object. |
| [Create iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosmobileappconfiguration-create?view=graph-rest-1.0) | [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) | Create a new [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) object. |
| [Delete iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosmobileappconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0). |
| [Update iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosmobileappconfiguration-update?view=graph-rest-1.0) | [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) | Update the properties of a [iosMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosmobileappconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| targetedMobileApps | String collection | the associated app. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| encodedSettingXml | Binary | mdm app configuration Base64 binary. |
| settings | [appConfigurationSettingItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-appconfigurationsettingitem?view=graph-rest-1.0) collection | app configuration setting items. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-1.0) collection | The list of group assignemenets for app configration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| deviceStatuses | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-1.0) collection | List of ManagedDeviceMobileAppConfigurationDeviceStatus. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| userStatuses | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-1.0) collection | List of ManagedDeviceMobileAppConfigurationUserStatus. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| deviceStatusSummary | [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-1.0) | App configuration device status summary. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |
| userStatusSummary | [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-1.0) | App configuration user status summary. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosMobileAppConfiguration",
  "id": "String (identifier)",
  "targetedMobileApps": [
    "String"
  ],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "encodedSettingXml": "binary",
  "settings": [
    {
      "@odata.type": "microsoft.graph.appConfigurationSettingItem",
      "appConfigKey": "String",
      "appConfigKeyType": "String",
      "appConfigKeyValue": "String"
    }
  ]
}
```
