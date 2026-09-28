<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# iosStoreApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for iOS store apps.

Inherits from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosStoreApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosstoreapp-list?view=graph-rest-1.0) | [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) collection | List properties and relationships of the [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) objects. |
| [Get iosStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosstoreapp-get?view=graph-rest-1.0) | [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) | Read properties and relationships of the [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) object. |
| [Create iosStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosstoreapp-create?view=graph-rest-1.0) | [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) | Create a new [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) object. |
| [Delete iosStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosstoreapp-delete?view=graph-rest-1.0) | None | Deletes a [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0). |
| [Update iosStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-iosstoreapp-update?view=graph-rest-1.0) | [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) | Update the properties of a [iosStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosstoreapp?view=graph-rest-1.0) object. |

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
| bundleId | String | The Identity Name. |
| appStoreUrl | String | The Apple App Store URL |
| applicableDeviceType | [iosDeviceType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosdevicetype?view=graph-rest-1.0) | The iOS architecture for which this app can run on. |
| minimumSupportedOperatingSystem | [iosMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosminimumoperatingsystem?view=graph-rest-1.0) | The value for the minimum applicable operating system. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosStoreApp",
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
  "bundleId": "String",
  "appStoreUrl": "String",
  "applicableDeviceType": {
    "@odata.type": "microsoft.graph.iosDeviceType",
    "iPad": true,
    "iPhoneAndIPod": true
  },
  "minimumSupportedOperatingSystem": {
    "@odata.type": "microsoft.graph.iosMinimumOperatingSystem",
    "v8_0": true,
    "v9_0": true,
    "v10_0": true,
    "v11_0": true,
    "v12_0": true,
    "v13_0": true,
    "v14_0": true,
    "v15_0": true
  }
}
```
