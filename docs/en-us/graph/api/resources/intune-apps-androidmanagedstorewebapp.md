<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidManagedStoreWebApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for web apps configured to be distributed via the managed Android app store.

Inherits from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidManagedStoreWebApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidmanagedstorewebapp-list?view=graph-rest-beta) | [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) collection | List properties and relationships of the [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) objects. |
| [Get androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidmanagedstorewebapp-get?view=graph-rest-beta) | [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) | Read properties and relationships of the [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) object. |
| [Create androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidmanagedstorewebapp-create?view=graph-rest-beta) | [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) | Create a new [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) object. |
| [Delete androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidmanagedstorewebapp-delete?view=graph-rest-beta) | None | Deletes a [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta). |
| [Update androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-androidmanagedstorewebapp-update?view=graph-rest-beta) | [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) | Update the properties of a [androidManagedStoreWebApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstorewebapp?view=graph-rest-beta) object. |

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
| packageId | String | The package identifier. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| appIdentifier | String | The Identity Name. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| usedLicenseCount | Int32 | The number of VPP licenses in use. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| totalLicenseCount | Int32 | The total number of VPP licenses. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| appStoreUrl | String | The Play for Work Store app URL. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| isPrivate | Boolean | Indicates whether the app is only available to a given enterprise's users. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| isSystemApp | Boolean | Indicates whether the app is a preinstalled system app. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| appTracks | [androidManagedStoreAppTrack](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapptrack?view=graph-rest-beta) collection | The tracks that are visible to this enterprise. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |
| supportsOemConfig | Boolean | Whether this app supports OEMConfig policy. This property is read-only. Inherited from [androidManagedStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidmanagedstoreapp?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-beta) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| targetAssignments | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) collection | The list of target assignments for this mobile app. Initially, this property will just expose deployment assignments. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| relationships | [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) collection | The set of direct relationships for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidManagedStoreWebApp",
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
  "packageId": "String",
  "appIdentifier": "String",
  "usedLicenseCount": 1024,
  "totalLicenseCount": 1024,
  "appStoreUrl": "String",
  "isPrivate": true,
  "isSystemApp": true,
  "appTracks": [
    {
      "@odata.type": "microsoft.graph.androidManagedStoreAppTrack",
      "trackId": "String",
      "trackAlias": "String"
    }
  ],
  "supportsOemConfig": true
}
```
