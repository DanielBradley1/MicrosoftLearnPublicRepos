<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsManagedAppRegistration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the synchronization details of a Windows app, with management capabilities, for a specific user. The ManagedAppRegistration resource represents the details of an app, with management capability, used by a member of the organization.

Inherits from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsManagedAppRegistrations](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappregistration-list?view=graph-rest-beta) | [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) collection | List properties and relationships of the [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) objects. |
| [Get windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappregistration-get?view=graph-rest-beta) | [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) | Read properties and relationships of the [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) object. |
| [Create windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappregistration-create?view=graph-rest-beta) | [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) | Create a new [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) object. |
| [Delete windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappregistration-delete?view=graph-rest-beta) | None | Deletes a [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta). |
| [Update windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsmanagedappregistration-update?view=graph-rest-beta) | [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) | Update the properties of a [windowsManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsmanagedappregistration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of creation Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| lastSyncDateTime | DateTimeOffset | Date and time of last the app synced with management service. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| applicationVersion | String | App version Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| managementSdkVersion | String | App management SDK version Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| platformVersion | String | Operating System version Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| deviceType | String | Host device type Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| deviceTag | String | App management SDK generated tag, which helps relate apps hosted on the same device. Not guaranteed to relate apps in all conditions. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| deviceName | String | Host device name Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| managedDeviceId | String | The Managed Device identifier of the host device. Value could be empty even when the host device is managed. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| azureADDeviceId | String | The Azure Active Directory Device identifier of the host device. Value could be empty even when the host device is Azure Active Directory registered. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| deviceModel | String | The device model for the current app registration Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| deviceManufacturer | String | The device manufacturer for the current app registration Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| flaggedReasons | [managedAppFlaggedReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappflaggedreason?view=graph-rest-beta) collection | Zero or more reasons an app registration is flagged. E.g. app running on rooted device Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| userId | String | The user Id to who this app registration belongs. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| appIdentifier | [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-beta) | The app package Identifier Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| version | String | Version of the entity. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliedPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) collection | Zero or more policys already applied on the registered app when it last synchronized with managment service. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| intendedPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) collection | Zero or more policies admin intended for the app as of now. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| managedAppLogCollectionRequests | [managedAppLogCollectionRequest](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapplogcollectionrequest?view=graph-rest-beta) collection | Zero or more log collection requests triggered for the app. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |
| operations | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-beta) collection | Zero or more long running operations triggered on the app registration. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsManagedAppRegistration",
  "createdDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "applicationVersion": "String",
  "managementSdkVersion": "String",
  "platformVersion": "String",
  "deviceType": "String",
  "deviceTag": "String",
  "deviceName": "String",
  "managedDeviceId": "String",
  "azureADDeviceId": "String",
  "deviceModel": "String",
  "deviceManufacturer": "String",
  "flaggedReasons": [
    "String"
  ],
  "userId": "String",
  "appIdentifier": {
    "@odata.type": "microsoft.graph.windowsAppIdentifier",
    "windowsAppId": "String"
  },
  "id": "String (identifier)",
  "version": "String"
}
```
