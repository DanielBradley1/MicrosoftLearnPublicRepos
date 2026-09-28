<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# macOSPkgApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for the MacOSPkgApp.

Inherits from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSPkgApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-macospkgapp-list?view=graph-rest-beta) | [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) collection | List properties and relationships of the [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) objects. |
| [Get macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macospkgapp-get?view=graph-rest-beta) | [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) | Read properties and relationships of the [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) object. |
| [Create macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macospkgapp-create?view=graph-rest-beta) | [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) | Create a new [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) object. |
| [Delete macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macospkgapp-delete?view=graph-rest-beta) | None | Deletes a [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta). |
| [Update macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macospkgapp-update?view=graph-rest-beta) | [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) | Update the properties of a [macOSPkgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macospkgapp?view=graph-rest-beta) object. |

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
| committedContentVersion | String | The internal committed content version. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-beta) |
| fileName | String | The name of the main Lob application file. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-beta) |
| size | Int64 | The total size, including all uploaded files. This property is read-only. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-beta) |
| primaryBundleId | String | The bundleId of the primary app in the PKG. This maps to the CFBundleIdentifier in the app's bundle configuration. |
| primaryBundleVersion | String | The version of the primary app in the PKG. This maps to the CFBundleShortVersion in the app's bundle configuration. |
| includedApps | [macOSIncludedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosincludedapp?view=graph-rest-beta) collection | The list of apps expected to be installed by the PKG. This collection can contain a maximum of 500 elements. |
| ignoreVersionDetection | Boolean | When TRUE, indicates that the app's version will NOT be used to detect if the app is installed on a device. When FALSE, indicates that the app's version will be used to detect if the app is installed on a device. Set this to true for apps that use a self update feature. The default value is FALSE. |
| minimumSupportedOperatingSystem | [macOSMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosminimumoperatingsystem?view=graph-rest-beta) | ComplexType macOSMinimumOperatingSystem that indicates the minimum operating system applicable for the application. |
| preInstallScript | [macOSAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosappscript?view=graph-rest-beta) | ComplexType macOSAppScript the contains the post-install script for the app. This will execute on the macOS device after the app is installed. |
| postInstallScript | [macOSAppScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosappscript?view=graph-rest-beta) | ComplexType macOSAppScript the contains the post-install script for the app. This will execute on the macOS device after the app is installed. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-beta) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| targetAssignments | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) collection | The list of target assignments for this mobile app. Initially, this property will just expose deployment assignments. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| relationships | [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) collection | The set of direct relationships for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| contentVersions | [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-beta) collection | The list of content versions for this app. This property is read-only. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSPkgApp",
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
  "committedContentVersion": "String",
  "fileName": "String",
  "size": 1024,
  "primaryBundleId": "String",
  "primaryBundleVersion": "String",
  "includedApps": [
    {
      "@odata.type": "microsoft.graph.macOSIncludedApp",
      "bundleId": "String",
      "bundleVersion": "String"
    }
  ],
  "ignoreVersionDetection": true,
  "minimumSupportedOperatingSystem": {
    "@odata.type": "microsoft.graph.macOSMinimumOperatingSystem",
    "v10_7": true,
    "v10_8": true,
    "v10_9": true,
    "v10_10": true,
    "v10_11": true,
    "v10_12": true,
    "v10_13": true,
    "v10_14": true,
    "v10_15": true,
    "v11_0": true,
    "v12_0": true,
    "v13_0": true,
    "v14_0": true,
    "v15_0": true,
    "v26_0": true
  },
  "preInstallScript": {
    "@odata.type": "microsoft.graph.macOSAppScript",
    "scriptContent": "String"
  },
  "postInstallScript": {
    "@odata.type": "microsoft.graph.macOSAppScript",
    "scriptContent": "String"
  }
}
```
