<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# macOSMdatpApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for the macOS Microsoft Defender Advanced Threat Protection \(MDATP\) App. This is deprecated for MacOSMicrosoftDefenderApp in 2305 \(May 2023\).

Inherits from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSMdatpApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosmdatpapp-list?view=graph-rest-beta) | [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) collection | List properties and relationships of the [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) objects. |
| [Get macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosmdatpapp-get?view=graph-rest-beta) | [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) | Read properties and relationships of the [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) object. |
| [Create macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosmdatpapp-create?view=graph-rest-beta) | [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) | Create a new [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) object. |
| [Delete macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosmdatpapp-delete?view=graph-rest-beta) | None | Deletes a [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta). |
| [Update macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-macosmdatpapp-update?view=graph-rest-beta) | [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) | Update the properties of a [macOSMdatpApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosmdatpapp?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| displayName | String | The admin provided or imported title of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| description | String | The description of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| publisher | String | The publisher of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| largeIcon | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | The large icon, to be displayed in the app details and used for upload of the icon. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the app was created. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | The date and time the app was last modified. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| isFeatured | Boolean | The value indicating whether the app is marked as featured by the admin. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| privacyInformationUrl | String | The privacy statement Url. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| informationUrl | String | The more information Url. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| owner | String | The owner of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| developer | String | The developer of the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| notes | String | Notes for the app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| uploadState | Int32 | The upload state. The possible values are: 0 - `Not Ready`, 1 - `Ready`, 2 - `Processing`. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| publishingState | [mobileAppPublishingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapppublishingstate?view=graph-rest-beta) | The publishing state for the app. The app cannot be assigned unless the app is published. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta). The possible values are: `notPublished`, `processing`, `published`. |
| isAssigned | Boolean | The value indicating whether the app is assigned to at least one group. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of scope tag ids for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| dependentAppCount | Int32 | The total number of dependencies the child app has. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| supersedingAppCount | Int32 | The total number of apps this app directly or indirectly supersedes. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| supersededAppCount | Int32 | The total number of apps this app is directly or indirectly superseded by. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-beta) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| relationships | [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) collection | The set of direct relationships for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSMdatpApp",
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
  "supersededAppCount": 1024
}
```
