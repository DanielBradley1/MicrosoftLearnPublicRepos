<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# vppToken resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

You purchase multiple licenses for iOS apps through the Apple Volume Purchase Program for Business or Education. This involves setting up an Apple VPP account from the Apple website and uploading the Apple VPP Business or Education token to Intune. You can then synchronize your volume purchase information with Intune and track your volume-purchased app use. You can upload multiple Apple VPP Business or Education tokens.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List vppTokens](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-list?view=graph-rest-1.0) | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) collection | List properties and relationships of the [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) objects. |
| [Get vppToken](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-get?view=graph-rest-1.0) | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) | Read properties and relationships of the [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) object. |
| [Create vppToken](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-create?view=graph-rest-1.0) | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) | Create a new [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) object. |
| [Delete vppToken](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-delete?view=graph-rest-1.0) | None | Deletes a [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0). |
| [Update vppToken](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-update?view=graph-rest-1.0) | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) | Update the properties of a [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) object. |
| [syncLicenses action](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-vpptoken-synclicenses?view=graph-rest-1.0) | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-1.0) | Syncs licenses associated with a specific appleVolumePurchaseProgramToken |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | This is automatically generated when the appleVolumePurchaseProgramToken is created. It is the Key of the entity. |
| organizationName | String | The organization associated with the Apple Volume Purchase Program Token |
| vppTokenAccountType | [vppTokenAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-vpptokenaccounttype?view=graph-rest-1.0) | The type of volume purchase program which the given Apple Volume Purchase Program Token is associated with. The possible values are: `business`, `education`. The possible values are: `business`, `education`. |
| appleId | String | The apple Id associated with the given Apple Volume Purchase Program Token. |
| expirationDateTime | DateTimeOffset | The expiration date time of the Apple Volume Purchase Program Token. |
| lastSyncDateTime | DateTimeOffset | The last time when an application sync was done with the Apple volume purchase program service using the the Apple Volume Purchase Program Token. |
| token | String | The Apple Volume Purchase Program Token string downloaded from the Apple Volume Purchase Program. |
| lastModifiedDateTime | DateTimeOffset | Last modification date time associated with the Apple Volume Purchase Program Token. |
| state | [vppTokenState](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenstate?view=graph-rest-1.0) | Current state of the Apple Volume Purchase Program Token. The possible values are: `unknown`, `valid`, `expired`, `invalid`, `assignedToExternalMDM`. The possible values are: `unknown`, `valid`, `expired`, `invalid`, `assignedToExternalMDM`. |
| lastSyncStatus | [vppTokenSyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokensyncstatus?view=graph-rest-1.0) | Current sync status of the last application sync which was triggered using the Apple Volume Purchase Program Token. The possible values are: `none`, `inProgress`, `completed`, `failed`. The possible values are: `none`, `inProgress`, `completed`, `failed`. |
| automaticallyUpdateApps | Boolean | Whether or not apps for the VPP token will be automatically updated. |
| countryOrRegion | String | Whether or not apps for the VPP token will be automatically updated. |
| lastAppCount | Int32 | The number of apps under the Apple Volume Purchase Program Token since the last token sync. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vppToken",
  "id": "String (identifier)",
  "organizationName": "String",
  "vppTokenAccountType": "String",
  "appleId": "String",
  "expirationDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "token": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "state": "String",
  "lastSyncStatus": "String",
  "automaticallyUpdateApps": true,
  "countryOrRegion": "String",
  "lastAppCount": 1024
}
```
