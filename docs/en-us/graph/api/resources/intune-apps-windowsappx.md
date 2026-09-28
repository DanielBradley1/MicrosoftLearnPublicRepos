<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# windowsAppX resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for Windows AppX Line Of Business apps.

Inherits from [mobileLobApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilelobapp?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsAppXs](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsappx-list?view=graph-rest-1.0) | [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) collection | List properties and relationships of the [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) objects. |
| [Get windowsAppX](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsappx-get?view=graph-rest-1.0) | [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) | Read properties and relationships of the [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) object. |
| [Create windowsAppX](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsappx-create?view=graph-rest-1.0) | [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) | Create a new [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) object. |
| [Delete windowsAppX](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsappx-delete?view=graph-rest-1.0) | None | Deletes a [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0). |
| [Update windowsAppX](https://learn.microsoft.com/en-us/graph/api/intune-apps-windowsappx-update?view=graph-rest-1.0) | [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) | Update the properties of a [windowsAppX](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsappx?view=graph-rest-1.0) object. |

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
| applicableArchitectures | [windowsArchitecture](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsarchitecture?view=graph-rest-1.0) | The Windows architecture\(s\) on which this app can run. The possible values are: `none`, `x86`, `x64`, `arm`, `neutral`; default value is `none`. The possible values are: `none`, `x86`, `x64`, `arm`, `neutral`. |
| identityName | String | The identity name of the uploaded app package. For example: "Contoso.DemoApp". |
| identityPublisherHash | String | The identity publisher hash of the uploaded app package. This is the hash of the publisher from the manifest. For example: "AB82CD0XYZ". |
| identityResourceIdentifier | String | The identity resource identifier of the uploaded app package. For example: "TestResourceId". |
| isBundle | Boolean | When TRUE, indicates that the app is a bundle. When FALSE, indicates that the app is not a bundle. By default, property is set to FALSE. |
| minimumSupportedOperatingSystem | [windowsMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsminimumoperatingsystem?view=graph-rest-1.0) | The value for the minimum applicable operating system. Valid values for a WindowsAppX app include `v8_0`, `v8_1` and `v10_0`. If the app is a bundle, the minimum supported OS has to be at least `v8_1`. |
| identityVersion | String | The identity version of the uploaded app package. For example: "1.0.0.0". |

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
  "@odata.type": "#microsoft.graph.windowsAppX",
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
  "applicableArchitectures": "String",
  "identityName": "String",
  "identityPublisherHash": "String",
  "identityResourceIdentifier": "String",
  "isBundle": true,
  "minimumSupportedOperatingSystem": {
    "@odata.type": "microsoft.graph.windowsMinimumOperatingSystem",
    "v8_0": true,
    "v8_1": true,
    "v10_0": true
  },
  "identityVersion": "String"
}
```
