<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsPhone81AppXBundle resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for Windows Phone 8.1 AppX Bundle Line Of Business apps. Inherits from graph.windowsPhone81AppX \(which is also to be deprecated at the same time\). Will be deprecated in February 2023.

Inherits from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsPhone81AppXBundles](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsphone81appxbundle-list?view=graph-rest-beta) | [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) collection | List properties and relationships of the [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) objects. |
| [Get windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsphone81appxbundle-get?view=graph-rest-beta) | [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) | Read properties and relationships of the [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) object. |
| [Create windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsphone81appxbundle-create?view=graph-rest-beta) | [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) | Create a new [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) object. |
| [Delete windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsphone81appxbundle-delete?view=graph-rest-beta) | None | Deletes a [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta). |
| [Update windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsphone81appxbundle-update?view=graph-rest-beta) | [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) | Update the properties of a [windowsPhone81AppXBundle](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appxbundle?view=graph-rest-beta) object. |

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
| applicableArchitectures | [windowsArchitecture](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsarchitecture?view=graph-rest-beta) | The Windows architecture\(s\) for which this app can run on. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta). Possible values are: `none`, `x86`, `x64`, `arm`, `neutral`, `arm64`. |
| identityName | String | The Identity Name. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| identityPublisherHash | String | The Identity Publisher Hash. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| identityResourceIdentifier | String | The Identity Resource Identifier. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| minimumSupportedOperatingSystem | [windowsMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsminimumoperatingsystem?view=graph-rest-beta) | The value for the minimum applicable operating system. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| phoneProductIdentifier | String | The Phone Product Identifier. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| phonePublisherId | String | The Phone Publisher Id. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| identityVersion | String | The identity version. Inherited from [windowsPhone81AppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsphone81appx?view=graph-rest-beta) |
| appXPackageInformationList | [windowsPackageInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowspackageinformation?view=graph-rest-beta) collection | The list of AppX Package Information. |

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
  "@odata.type": "#microsoft.graph.windowsPhone81AppXBundle",
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
  "applicableArchitectures": "String",
  "identityName": "String",
  "identityPublisherHash": "String",
  "identityResourceIdentifier": "String",
  "minimumSupportedOperatingSystem": {
    "@odata.type": "microsoft.graph.windowsMinimumOperatingSystem",
    "v8_0": true,
    "v8_1": true,
    "v10_0": true,
    "v10_1607": true,
    "v10_1703": true,
    "v10_1709": true,
    "v10_1803": true,
    "v10_1809": true,
    "v10_1903": true,
    "v10_1909": true,
    "v10_2004": true,
    "v10_2H20": true,
    "v10_21H1": true
  },
  "phoneProductIdentifier": "String",
  "phonePublisherId": "String",
  "identityVersion": "String",
  "appXPackageInformationList": [
    {
      "@odata.type": "microsoft.graph.windowsPackageInformation",
      "applicableArchitecture": "String",
      "displayName": "String",
      "identityName": "String",
      "identityPublisher": "String",
      "identityResourceIdentifier": "String",
      "identityVersion": "String",
      "minimumSupportedOperatingSystem": {
        "@odata.type": "microsoft.graph.windowsMinimumOperatingSystem",
        "v8_0": true,
        "v8_1": true,
        "v10_0": true,
        "v10_1607": true,
        "v10_1703": true,
        "v10_1709": true,
        "v10_1803": true,
        "v10_1809": true,
        "v10_1903": true,
        "v10_1909": true,
        "v10_2004": true,
        "v10_2H20": true,
        "v10_21H1": true
      }
    }
  ]
}
```
