<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# managedAppRegistration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The ManagedAppEntity is the base entity type for all other entity types under app management workflow. The ManagedAppRegistration resource represents the details of an app, with management capability, used by a member of the organization.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppRegistrations](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappregistration-list?view=graph-rest-1.0) | [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) objects. |
| [Get managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappregistration-get?view=graph-rest-1.0) | [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) | Read properties and relationships of the [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-1.0) object. |
| [getUserIdsWithFlaggedAppRegistration function](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappregistration-getuseridswithflaggedappregistration?view=graph-rest-1.0) | String collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time of creation |
| lastSyncDateTime | DateTimeOffset | Date and time of last the app synced with management service. |
| applicationVersion | String | App version |
| managementSdkVersion | String | App management SDK version |
| platformVersion | String | Operating System version |
| deviceType | String | Host device type |
| deviceTag | String | App management SDK generated tag, which helps relate apps hosted on the same device. Not guaranteed to relate apps in all conditions. |
| deviceName | String | Host device name |
| flaggedReasons | [managedAppFlaggedReason](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappflaggedreason?view=graph-rest-1.0) collection | Zero or more reasons an app registration is flagged. E.g. app running on rooted device |
| userId | String | The user Id to who this app registration belongs. |
| appIdentifier | [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-1.0) | The app package Identifier |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliedPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | Zero or more policys already applied on the registered app when it last synchronized with managment service. |
| intendedPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) collection | Zero or more policies admin intended for the app as of now. |
| operations | [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) collection | Zero or more long running operations triggered on the app registration. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppRegistration",
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
    "@odata.type": "microsoft.graph.androidMobileAppIdentifier",
    "packageId": "String"
  },
  "id": "String (identifier)",
  "version": "String"
}
```
