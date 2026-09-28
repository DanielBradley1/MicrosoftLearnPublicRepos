<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# androidForWorkMobileAppConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties, inherited properties and actions for AFW mobile app configurations.

Inherits from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidForWorkMobileAppConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidforworkmobileappconfiguration-list?view=graph-rest-beta) | [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) objects. |
| [Get androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidforworkmobileappconfiguration-get?view=graph-rest-beta) | [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) | Read properties and relationships of the [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) object. |
| [Create androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidforworkmobileappconfiguration-create?view=graph-rest-beta) | [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) | Create a new [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) object. |
| [Delete androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidforworkmobileappconfiguration-delete?view=graph-rest-beta) | None | Deletes a [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta). |
| [Update androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidforworkmobileappconfiguration-update?view=graph-rest-beta) | [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) | Update the properties of a [androidForWorkMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidforworkmobileappconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| targetedMobileApps | String collection | the associated app. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this App configuration entity. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| packageId | String | Android For Work app configuration package id. |
| payloadJson | String | Android For Work app configuration JSON payload. |
| permissionActions | [androidPermissionAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidpermissionaction?view=graph-rest-beta) collection | List of Android app permissions and corresponding permission actions. |
| profileApplicability | [androidProfileApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidprofileapplicability?view=graph-rest-beta) | Android Enterprise profile applicability \(AndroidWorkProfile, DeviceOwner, or default \(applies to both\)\). Possible values are: `default`, `androidWorkProfile`, `androidDeviceOwner`. |
| connectedAppsEnabled | Boolean | Setting to specify whether to allow ConnectedApps experience for this app. |
| credentialProviderRoleState | [androidAppCredentialProviderRoleState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidappcredentialproviderrolestate?view=graph-rest-beta) | Indicates whether the app is allowed to act as a credential provider. Applies to Android 14 and above. The default value is 'notConfigured'. Possible values are: 'notConfigured' and 'allowed'. When set to 'notConfigured', the Android OS will determine whether the app is allowed to act as a credential provider or not. Possible values are: `notConfigured`, `allowed`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [managedDeviceMobileAppConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationassignment?view=graph-rest-beta) collection | The list of group assignemenets for app configration. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| deviceStatuses | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-beta) collection | List of ManagedDeviceMobileAppConfigurationDeviceStatus. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| userStatuses | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-beta) collection | List of ManagedDeviceMobileAppConfigurationUserStatus. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| deviceStatusSummary | [managedDeviceMobileAppConfigurationDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicesummary?view=graph-rest-beta) | App configuration device status summary. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |
| userStatusSummary | [managedDeviceMobileAppConfigurationUserSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationusersummary?view=graph-rest-beta) | App configuration user status summary. Inherited from [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidForWorkMobileAppConfiguration",
  "id": "String (identifier)",
  "targetedMobileApps": [
    "String"
  ],
  "roleScopeTagIds": [
    "String"
  ],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "packageId": "String",
  "payloadJson": "String",
  "permissionActions": [
    {
      "@odata.type": "microsoft.graph.androidPermissionAction",
      "permission": "String",
      "action": "String"
    }
  ],
  "profileApplicability": "String",
  "connectedAppsEnabled": true,
  "credentialProviderRoleState": "String"
}
```
