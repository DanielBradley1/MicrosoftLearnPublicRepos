<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappregistration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosManagedAppRegistration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the synchronization details of an ios app, with management capabilities, for a specific user. The ManagedAppRegistration resource represents the details of an app, with management capability, used by a member of the organization.

Inherits from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosManagedAppRegistrations](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappregistration-list?view=graph-rest-1.0) | [iosManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappregistration?view=graph-rest-1.0) collection | List properties and relationships of the [iosManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappregistration?view=graph-rest-1.0) objects. |
| [Get iosManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-iosmanagedappregistration-get?view=graph-rest-1.0) | [iosManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappregistration?view=graph-rest-1.0) | Read properties and relationships of the [iosManagedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-iosmanagedappregistration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of creation Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| lastSyncDateTime | DateTimeOffset | Date and time of last the app synced with management service. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| applicationVersion | String | App version Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| managementSdkVersion | String | App management SDK version Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| platformVersion | String | Operating System version Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| deviceType | String | Host device type Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| deviceTag | String | App management SDK generated tag, which helps relate apps hosted on the same device. Not guaranteed to relate apps in all conditions. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| deviceName | String | Host device name Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| flaggedReasons | [managedAppFlaggedReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappflaggedreason?view=graph-rest-1.0) collection | Zero or more reasons an app registration is flagged. E.g. app running on rooted device Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| userId | String | The user Id to who this app registration belongs. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| appIdentifier | [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-1.0) | The app package Identifier Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliedPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | Zero or more policys already applied on the registered app when it last synchronized with managment service. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| intendedPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | Zero or more policies admin intended for the app as of now. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |
| operations | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) collection | Zero or more long running operations triggered on the app registration. Inherited from [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosManagedAppRegistration",
  "createdDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "applicationVersion": "String",
  "managementSdkVersion": "String",
  "platformVersion": "String",
  "deviceType": "String",
  "deviceTag": "String",
  "deviceName": "String",
  "flaggedReasons": [
    "String"
  ],
  "userId": "String",
  "appIdentifier": {
    "@odata.type": "microsoft.graph.iosMobileAppIdentifier",
    "bundleId": "String"
  },
  "id": "String (identifier)",
  "version": "String"
}
```
