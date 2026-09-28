<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosLobAppProvisioningConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the iOS Lob App Provisioning Configuration resource.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosLobAppProvisioningConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfiguration-list?view=graph-rest-beta) | [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) objects. |
| [Get iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfiguration-get?view=graph-rest-beta) | [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) | Read properties and relationships of the [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) object. |
| [Create iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfiguration-create?view=graph-rest-beta) | [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) | Create a new [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) object. |
| [Delete iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfiguration-delete?view=graph-rest-beta) | None | Deletes a [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta). |
| [Update iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfiguration-update?view=graph-rest-beta) | [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) | Update the properties of a [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-apps-ioslobappprovisioningconfiguration-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |  |
| :--- | :--- | :--- | --- |
| id | String | The unique identifier of the LOB app provisioning configuration. This id is assigned during creation of the configuration. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. Read-only. |  |
| expirationDateTime | DateTimeOffset | Optional profile expiration date and time. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. Returned by default. |  |
| payloadFileName | String | Payload file name \(\*.mobileprovision | \*.xml\). |
| payload | Binary | Payload. \(UTF8 encoded byte array\) |  |
| roleScopeTagIds | String collection | List of Scope Tags for this iOS LOB app provisioning configuration entity. |  |
| createdDateTime | DateTimeOffset | DateTime the object was created. |  |
| description | String | Admin provided description of the Device Configuration. |  |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |  |
| displayName | String | Admin provided name of the device configuration. |  |
| version | Int32 | Version of the device configuration. |  |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groupAssignments | [mobileAppProvisioningConfigGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappprovisioningconfiggroupassignment?view=graph-rest-beta) collection | The associated group assignments. |
| assignments | [iosLobAppProvisioningConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-ioslobappprovisioningconfigurationassignment?view=graph-rest-beta) collection | The associated group assignments for IosLobAppProvisioningConfiguration, this determines which devices/users the IOS LOB app provisioning conifguration will be targeted to. |
| deviceStatuses | [managedDeviceMobileAppConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationdevicestatus?view=graph-rest-beta) collection | The list of device installation states for this mobile app configuration. |
| userStatuses | [managedDeviceMobileAppConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfigurationuserstatus?view=graph-rest-beta) collection | The list of user installation states for this mobile app configuration. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosLobAppProvisioningConfiguration",
  "id": "String (identifier)",
  "expirationDateTime": "String (timestamp)",
  "payloadFileName": "String",
  "payload": "binary",
  "roleScopeTagIds": [
    "String"
  ],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024
}
```
