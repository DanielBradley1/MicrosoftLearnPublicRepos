<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# macOSDmgApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for the MacOS DMG \(Apple Disk Image\) App.

Inherits from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSDmgApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosdmgapp-list?view=graph-rest-1.0) | [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) collection | List properties and relationships of the [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) objects. |
| [Get macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosdmgapp-get?view=graph-rest-1.0) | [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) | Read properties and relationships of the [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) object. |
| [Create macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosdmgapp-create?view=graph-rest-1.0) | [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) | Create a new [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) object. |
| [Delete macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosdmgapp-delete?view=graph-rest-1.0) | None | Deletes a [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0). |
| [Update macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosdmgapp-update?view=graph-rest-1.0) | [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) | Update the properties of a [macOSDmgApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosdmgapp?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| displayName | String | The admin provided or imported title of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| description | String | The description of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| publisher | String | The publisher of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| largeIcon | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-1.0) | The large icon, to be displayed in the app details and used for upload of the icon. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the app was created. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | The date and time the app was last modified. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| isFeatured | Boolean | The value indicating whether the app is marked as featured by the admin. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| privacyInformationUrl | String | The privacy statement Url. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| informationUrl | String | The more information Url. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| owner | String | The owner of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| developer | String | The developer of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| notes | String | Notes for the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| publishingState | [mobileAppPublishingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapppublishingstate?view=graph-rest-1.0) | The publishing state for the app. The app cannot be assigned unless the app is published. This property is read-only. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0). The possible values are: `notPublished`, `processing`, `published`. |
| committedContentVersion | String | The internal committed content version. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-1.0) |
| fileName | String | The name of the main Lob application file. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-1.0) |
| size | Int64 | The total size, including all uploaded files. This property is read-only. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-1.0) |
| primaryBundleId | String | The bundleId of the primary .app in the DMG \(Apple Disk Image\). This maps to the CFBundleIdentifier in the app's bundle configuration. |
| primaryBundleVersion | String | The version of the primary .app in the DMG \(Apple Disk Image\). This maps to the CFBundleShortVersion in the app's bundle configuration. |
| includedApps | [macOSIncludedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosincludedapp?view=graph-rest-1.0) collection | The list of .apps expected to be installed by the DMG \(Apple Disk Image\). This collection can contain a maximum of 500 elements. |
| ignoreVersionDetection | Boolean | When TRUE, indicates that the app's version will NOT be used to detect if the app is installed on a device. When FALSE, indicates that the app's version will be used to detect if the app is installed on a device. Set this to true for apps that use a self update feature. The default value is FALSE. |
| minimumSupportedOperatingSystem | [macOSMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosminimumoperatingsystem?view=graph-rest-1.0) | ComplexType macOSMinimumOperatingSystem that indicates the minimum operating system applicable for the application. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| contentVersions | [mobileAppContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontent?view=graph-rest-1.0) collection | The list of content versions for this app. This property is read-only. Inherited from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSDmgApp",
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
  "publishingState": "String",
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
    "v13_0": true
  }
}
```
