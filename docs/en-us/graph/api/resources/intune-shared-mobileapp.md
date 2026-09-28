<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# mobileApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An abstract class containing the base properties for Intune mobile apps.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileApps](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-list?view=graph-rest-beta) | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) collection | List properties and relationships of the [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) objects. |
| [Get mobileApp](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-get?view=graph-rest-beta) | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) | Read properties and relationships of the [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) object. |
| **Apps** |  |  |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-assign?view=graph-rest-beta) | None |  |
| [getMobileAppCount function](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-getmobileappcount?view=graph-rest-beta) | Int64 |  |
| [getTopMobileApps function](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-gettopmobileapps?view=graph-rest-beta) | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) collection |  |
| [updateRelationships action](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-updaterelationships?view=graph-rest-beta) | None |  |
| [getRelatedAppStates function](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-getrelatedappstates?view=graph-rest-beta) | [mobileAppRelationshipState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationshipstate?view=graph-rest-beta) collection |  |
| **Policy Set** |  |  |
| [hasPayloadLinks action](https://learn.microsoft.com/en-us/graph/api/intune-shared-mobileapp-haspayloadlinks?view=graph-rest-beta) | [hasPayloadLinkResultItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | The admin provided or imported title of the app. |
| description | String | The description of the app. |
| publisher | String | The publisher of the app. |
| largeIcon | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | The large icon, to be displayed in the app details and used for upload of the icon. |
| createdDateTime | DateTimeOffset | The date and time the app was created. |
| lastModifiedDateTime | DateTimeOffset | The date and time the app was last modified. |
| isFeatured | Boolean | The value indicating whether the app is marked as featured by the admin. |
| privacyInformationUrl | String | The privacy statement Url. |
| informationUrl | String | The more information Url. |
| owner | String | The owner of the app. |
| developer | String | The developer of the app. |
| notes | String | Notes for the app. |
| uploadState | Int32 | The upload state. |
| publishingState | [mobileAppPublishingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapppublishingstate?view=graph-rest-beta) | The publishing state for the app. The app cannot be assigned unless the app is published. The possible values are: `notPublished`, `processing`, `published`. |
| isAssigned | Boolean | The value indicating whether the app is assigned to at least one group. |
| roleScopeTagIds | String collection | List of scope tag ids for this mobile app. |
| dependentAppCount | Int32 | The total number of dependencies the child app has. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Apps** |  |  |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The list of categories for this app. |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-beta) collection | The list of group assignments for this mobile app. |
| installSummary | [mobileAppInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallsummary?view=graph-rest-beta) | Mobile App Install Summary. |
| deviceStatuses | [mobileAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappinstallstatus?view=graph-rest-beta) collection | The list of installation states for this mobile app. |
| userStatuses | [userAppInstallStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-userappinstallstatus?view=graph-rest-beta) collection | The list of installation states for this mobile app. |
| relationships | [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) collection | List of relationships for this mobile app. |

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
  "uploadState": 1024,
  "publishingState": "String",
  "isAssigned": true,
  "roleScopeTagIds": [
    "String"
  ],
  "dependentAppCount": 1024
}
```
