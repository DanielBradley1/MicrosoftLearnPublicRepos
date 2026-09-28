<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# androidForWorkSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Settings for Android For Work.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworksettings-get?view=graph-rest-beta) | [androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksettings?view=graph-rest-beta) | Read properties and relationships of the [androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksettings?view=graph-rest-beta) object. |
| [Update androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworksettings-update?view=graph-rest-beta) | [androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksettings?view=graph-rest-beta) | Update the properties of a [androidForWorkSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksettings?view=graph-rest-beta) object. |
| [requestSignupUrl action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworksettings-requestsignupurl?view=graph-rest-beta) | String |  |
| [completeSignup action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworksettings-completesignup?view=graph-rest-beta) | None |  |
| [syncApps action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworksettings-syncapps?view=graph-rest-beta) | None |  |
| [unbind action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworksettings-unbind?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Android for Work settings identifier |
| bindStatus | [androidForWorkBindStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkbindstatus?view=graph-rest-beta) | Bind status of the tenant with the Google EMM API. Possible values are: `notBound`, `bound`, `boundAndValidated`, `unbinding`. |
| lastAppSyncDateTime | DateTimeOffset | Last completion time for app sync |
| lastAppSyncStatus | [androidForWorkSyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworksyncstatus?view=graph-rest-beta) | Last application sync result. Possible values are: `success`, `credentialsNotValid`, `androidForWorkApiError`, `managementServiceError`, `unknownError`, `none`. |
| ownerUserPrincipalName | String | Owner UPN that created the enterprise |
| ownerOrganizationName | String | Organization name used when onboarding Android for Work |
| lastModifiedDateTime | DateTimeOffset | Last modification time for Android for Work settings |
| enrollmentTarget | [androidForWorkEnrollmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmenttarget?view=graph-rest-beta) | Indicates which users can enroll devices in Android for Work device management. Possible values are: `none`, `all`, `targeted`, `targetedAsEnrollmentRestrictions`. |
| targetGroupIds | String collection | Specifies which AAD groups can enroll devices in Android for Work device management if enrollmentTarget is set to 'Targeted' |
| deviceOwnerManagementEnabled | Boolean | Indicates if this account is flighting for Android Device Owner Management with CloudDPC. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidForWorkSettings",
  "id": "String (identifier)",
  "bindStatus": "String",
  "lastAppSyncDateTime": "String (timestamp)",
  "lastAppSyncStatus": "String",
  "ownerUserPrincipalName": "String",
  "ownerOrganizationName": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "enrollmentTarget": "String",
  "targetGroupIds": [
    "String"
  ],
  "deviceOwnerManagementEnabled": true
}
```
