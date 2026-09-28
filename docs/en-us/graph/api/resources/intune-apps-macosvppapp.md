<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# macOsVppApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for MacOS Volume-Purchased Program \(VPP\) Apps.

Inherits from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOsVppApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppapp-list?view=graph-rest-beta) | [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) collection | List properties and relationships of the [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) objects. |
| [Get macOsVppApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppapp-get?view=graph-rest-beta) | [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) | Read properties and relationships of the [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) object. |
| [Create macOsVppApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppapp-create?view=graph-rest-beta) | [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) | Create a new [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) object. |
| [Delete macOsVppApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppapp-delete?view=graph-rest-beta) | None | Deletes a [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta). |
| [Update macOsVppApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosvppapp-update?view=graph-rest-beta) | [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) | Update the properties of a [macOsVppApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapp?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| displayName | String | The admin provided or imported title of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| description | String | The description of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| publisher | String | The publisher of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| largeIcon | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | The large icon, to be displayed in the app details and used for upload of the icon. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the app was created. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the app was last modified. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| isFeatured | Boolean | The value indicating whether the app is marked as featured by the admin. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| privacyInformationUrl | String | The privacy statement Url. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| informationUrl | String | The more information Url. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| owner | String | The owner of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| developer | String | The developer of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| notes | String | Notes for the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| uploadState | Int32 | The upload state. Possible values are: 0 - `Not Ready`, 1 - `Ready`, 2 - `Processing`. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| publishingState | [mobileAppPublishingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapppublishingstate?view=graph-rest-beta) | The publishing state for the app. The app cannot be assigned unless the app is published. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta). Possible values are: `notPublished`, `processing`, `published`. |
| isAssigned | Boolean | The value indicating whether the app is assigned to at least one group. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of scope tag ids for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| dependentAppCount | Int32 | The total number of dependencies the child app has. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| supersedingAppCount | Int32 | The total number of apps this app directly or indirectly supersedes. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| supersededAppCount | Int32 | The total number of apps this app is directly or indirectly superseded by. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| usedLicenseCount | Int32 | The number of VPP licenses in use. |
| totalLicenseCount | Int32 | The total number of VPP licenses. |
| releaseDateTime | DateTimeOffset | The VPP application release date and time. |
| appStoreUrl | String | The store URL. |
| licensingType | [vppLicensingType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-vpplicensingtype?view=graph-rest-beta) | The supported License Type. |
| vppTokenOrganizationName | String | The organization associated with the Apple Volume Purchase Program Token |
| vppTokenAccountType | [vppTokenAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-vpptokenaccounttype?view=graph-rest-beta) | The type of volume purchase program which the given Apple Volume Purchase Program Token is associated with. Possible values are: `business`, `education`. Possible values are: `business`, `education`. |
| vppTokenAppleId | String | The Apple Id associated with the given Apple Volume Purchase Program Token. |
| bundleId | String | The Identity Name. |
| vppTokenId | String | Identifier of the VPP token associated with this app. |
| vppTokenDisplayName | String | Display name of the VPP token associated with this app. |
| revokeLicenseActionResults | [macOsVppAppRevokeLicensesActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppapprevokelicensesactionresult?view=graph-rest-beta) collection | Results of revoke license actions on this app. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-beta) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| targetAssignments | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) collection | The list of target assignments for this mobile app. Initially, this property will just expose deployment assignments. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| relationships | [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) collection | The set of direct relationships for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| assignedLicenses | [macOsVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosvppappassignedlicense?view=graph-rest-beta) collection | The licenses assigned to this app. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOsVppApp",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "publisher": "String",
  "largeIcon": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "isFeatured": true,
  "privacyInformationUrl": "String",
  "informationUrl": "String",
  "owner": "String",
  "developer": "String",
  "notes": "String",
  "uploadState": 1024,
  "publishingState": "String",
  "isAssigned": true,
  "roleScopeTagIds": [
    "String"
  ],
  "dependentAppCount": 1024,
  "supersedingAppCount": 1024,
  "supersededAppCount": 1024,
  "usedLicenseCount": 1024,
  "totalLicenseCount": 1024,
  "releaseDateTime": "String (timestamp)",
  "appStoreUrl": "String",
  "licensingType": {
    "@odata.type": "microsoft.graph.vppLicensingType",
    "supportUserLicensing": true,
    "supportDeviceLicensing": true,
    "supportsUserLicensing": true,
    "supportsDeviceLicensing": true
  },
  "vppTokenOrganizationName": "String",
  "vppTokenAccountType": "String",
  "vppTokenAppleId": "String",
  "bundleId": "String",
  "vppTokenId": "String",
  "vppTokenDisplayName": "String",
  "revokeLicenseActionResults": [
    {
      "@odata.type": "microsoft.graph.macOsVppAppRevokeLicensesActionResult",
      "userId": "String",
      "managedDeviceId": "String",
      "totalLicensesCount": 1024,
      "failedLicensesCount": 1024,
      "actionFailureReason": "String",
      "actionName": "String",
      "actionState": "String",
      "startDateTime": "String (timestamp)",
      "lastUpdatedDateTime": "String (timestamp)"
    }
  ]
}
```
