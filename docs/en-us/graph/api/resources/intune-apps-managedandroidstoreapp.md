<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# managedAndroidStoreApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for Android store apps that you can manage with an Intune app protection policy.

Inherits from [managedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedapp?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAndroidStoreApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-managedandroidstoreapp-list?view=graph-rest-1.0) | [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) collection | List properties and relationships of the [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) objects. |
| [Get managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-managedandroidstoreapp-get?view=graph-rest-1.0) | [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) | Read properties and relationships of the [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) object. |
| [Create managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-managedandroidstoreapp-create?view=graph-rest-1.0) | [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) | Create a new [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) object. |
| [Delete managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-managedandroidstoreapp-delete?view=graph-rest-1.0) | None | Deletes a [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0). |
| [Update managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-managedandroidstoreapp-update?view=graph-rest-1.0) | [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) | Update the properties of a [managedAndroidStoreApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedandroidstoreapp?view=graph-rest-1.0) object. |

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
| appAvailability | [managedAppAvailability](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedappavailability?view=graph-rest-1.0) | The Application's availability. This property is read-only. Inherited from [managedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedapp?view=graph-rest-1.0). The possible values are: `global`, `lineOfBusiness`. |
| version | String | The Application's version. Inherited from [managedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-managedapp?view=graph-rest-1.0) |
| packageId | String | The app's package ID. |
| appStoreUrl | String | The Android AppStoreUrl. |
| minimumSupportedOperatingSystem | [androidMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidminimumoperatingsystem?view=graph-rest-1.0) | The value for the minimum supported operating system. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAndroidStoreApp",
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
  "appAvailability": "String",
  "version": "String",
  "packageId": "String",
  "appStoreUrl": "String",
  "minimumSupportedOperatingSystem": {
    "@odata.type": "microsoft.graph.androidMinimumOperatingSystem",
    "v4_0": true,
    "v4_0_3": true,
    "v4_1": true,
    "v4_2": true,
    "v4_3": true,
    "v4_4": true,
    "v5_0": true,
    "v5_1": true,
    "v6_0": true,
    "v7_0": true,
    "v7_1": true,
    "v8_0": true,
    "v8_1": true,
    "v9_0": true,
    "v10_0": true,
    "v11_0": true
  }
}
```
