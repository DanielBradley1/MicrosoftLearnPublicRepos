<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# mobileApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An abstract class containing the base properties for Intune mobile apps. Note: Listing mobile apps with `$expand=assignments` has been deprecated. Instead get the list of apps without the `$expand` query on `assignments`. Then, perform the expansion on individual applications.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileapp-list?view=graph-rest-1.0) | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) collection | List properties and relationships of the [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) objects. |
| [Get mobileApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileapp-get?view=graph-rest-1.0) | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) | Read properties and relationships of the [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapp?view=graph-rest-1.0) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileapp-assign?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. |
| displayName | String | The admin provided or imported title of the app. |
| description | String | The description of the app. |
| publisher | String | The publisher of the app. |
| largeIcon | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-1.0) | The large icon, to be displayed in the app details and used for upload of the icon. |
| createdDateTime | DateTimeOffset | The date and time the app was created. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the app was last modified. This property is read-only. |
| isFeatured | Boolean | The value indicating whether the app is marked as featured by the admin. |
| privacyInformationUrl | String | The privacy statement Url. |
| informationUrl | String | The more information Url. |
| owner | String | The owner of the app. |
| developer | String | The developer of the app. |
| notes | String | Notes for the app. |
| publishingState | [mobileAppPublishingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapppublishingstate?view=graph-rest-1.0) | The publishing state for the app. The app cannot be assigned unless the app is published. This property is read-only. The possible values are: `notPublished`, `processing`, `published`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-1.0) collection | The list of categories for this app. |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-1.0) collection | The list of group assignments for this mobile app. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileApp",
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
  "publishingState": "String"
}
```
