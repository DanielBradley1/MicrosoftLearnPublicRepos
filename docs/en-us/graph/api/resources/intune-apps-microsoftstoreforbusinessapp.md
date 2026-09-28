<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# microsoftStoreForBusinessApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Microsoft Store for Business Apps. This class does not support Create, Delete, or Update.

Inherits from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftStoreForBusinessApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinessapp-list?view=graph-rest-1.0) | [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) collection | List properties and relationships of the [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) objects. |
| [Get microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinessapp-get?view=graph-rest-1.0) | [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) | Read properties and relationships of the [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) object. |
| [Create microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinessapp-create?view=graph-rest-1.0) | [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) | Create a new [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) object. |
| [Delete microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinessapp-delete?view=graph-rest-1.0) | None | Deletes a [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0). |
| [Update microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinessapp-update?view=graph-rest-1.0) | [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) | Update the properties of a [microsoftStoreForBusinessApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinessapp?view=graph-rest-1.0) object. |

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
| usedLicenseCount | Int32 | The number of Microsoft Store for Business licenses in use. |
| totalLicenseCount | Int32 | The total number of Microsoft Store for Business licenses. |
| productKey | String | The app product key |
| licenseType | [microsoftStoreForBusinessLicenseType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesslicensetype?view=graph-rest-1.0) | The app license type. The possible values are: `offline`, `online`. |
| packageIdentityName | String | The app package identifier |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftStoreForBusinessApp",
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
  "usedLicenseCount": 1024,
  "totalLicenseCount": 1024,
  "productKey": "String",
  "licenseType": "String",
  "packageIdentityName": "String"
}
```
