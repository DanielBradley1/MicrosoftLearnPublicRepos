<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# officeSuiteApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties and inherited properties for the Office365 Suite App.

Inherits from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List officeSuiteApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-officesuiteapp-list?view=graph-rest-beta) | [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) collection | List properties and relationships of the [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) objects. |
| [Get officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-officesuiteapp-get?view=graph-rest-beta) | [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) | Read properties and relationships of the [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) object. |
| [Create officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-officesuiteapp-create?view=graph-rest-beta) | [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) | Create a new [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) object. |
| [Delete officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-officesuiteapp-delete?view=graph-rest-beta) | None | Deletes a [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta). |
| [Update officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-officesuiteapp-update?view=graph-rest-beta) | [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) | Update the properties of a [officeSuiteApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteapp?view=graph-rest-beta) object. |

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
| autoAcceptEula | Boolean | The value to accept the EULA automatically on the enduser's device. |
| productIds | [officeProductId](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officeproductid?view=graph-rest-beta) collection | The Product Ids that represent the Office365 Suite SKU. |
| excludedApps | [excludedApps](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-excludedapps?view=graph-rest-beta) | The property to represent the apps which are excluded from the selected Office365 Product Id. |
| useSharedComputerActivation | Boolean | The property to represent that whether the shared computer activation is used not for Office365 app suite. |
| updateChannel | [officeUpdateChannel](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officeupdatechannel?view=graph-rest-beta) | The property to represent the Office365 Update Channel. Possible values are: `none`, `current`, `deferred`, `firstReleaseCurrent`, `firstReleaseDeferred`, `monthlyEnterprise`. |
| officeSuiteAppDefaultFileFormat | [officeSuiteDefaultFileFormatType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuitedefaultfileformattype?view=graph-rest-beta) | The property to represent the Office365 default file format type. Possible values are: `notConfigured`, `officeOpenXMLFormat`, `officeOpenDocumentFormat`, `unknownFutureValue`. |
| officePlatformArchitecture | [windowsArchitecture](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsarchitecture?view=graph-rest-beta) | The property to represent the Office365 app suite version. Possible values are: `none`, `x86`, `x64`, `arm`, `neutral`, `arm64`. |
| localesToInstall | String collection | The property to represent the locales which are installed when the apps from Office365 is installed. It uses standard RFC 6033. Ref: [https://technet.microsoft.com/library/cc179219\(v=office.16\).aspx\|](https://technet.microsoft.com/library/cc179219\(v=office.16\).aspx%7C) |
| installProgressDisplayLevel | [officeSuiteInstallProgressDisplayLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-officesuiteinstallprogressdisplaylevel?view=graph-rest-beta) | To specify the level of display for the Installation Progress Setup UI on the Device. Possible values are: `none`, `full`. |
| shouldUninstallOlderVersionsOfOffice | Boolean | The property to determine whether to uninstall existing Office MSI if an Office365 app suite is deployed to the device or not. |
| targetVersion | String | The property to represent the specific target version for the Office365 app suite that should be remained deployed on the devices. |
| updateVersion | String | The property to represent the update version in which the specific target version is available for the Office365 app suite. |
| officeConfigurationXml | Binary | The property to represent the XML configuration file that can be specified for Office ProPlus Apps. Takes precedence over all other properties. When present, the XML configuration file will be used to create the app. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The list of categories for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| assignments | [mobileAppAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappassignment?view=graph-rest-beta) collection | The list of group assignments for this mobile app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| targetAssignments | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) collection | The list of target assignments for this mobile app. Initially, this property will just expose deployment assignments. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |
| relationships | [mobileAppRelationship](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileapprelationship?view=graph-rest-beta) collection | The set of direct relationships for this app. Inherited from [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.officeSuiteApp",
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
  "autoAcceptEula": true,
  "productIds": [
    "String"
  ],
  "excludedApps": {
    "@odata.type": "microsoft.graph.excludedApps",
    "access": true,
    "bing": true,
    "excel": true,
    "groove": true,
    "infoPath": true,
    "lync": true,
    "oneDrive": true,
    "oneNote": true,
    "outlook": true,
    "powerPoint": true,
    "publisher": true,
    "sharePointDesigner": true,
    "teams": true,
    "visio": true,
    "word": true
  },
  "useSharedComputerActivation": true,
  "updateChannel": "String",
  "officeSuiteAppDefaultFileFormat": "String",
  "officePlatformArchitecture": "String",
  "localesToInstall": [
    "String"
  ],
  "installProgressDisplayLevel": "String",
  "shouldUninstallOlderVersionsOfOffice": true,
  "targetVersion": "String",
  "updateVersion": "String",
  "officeConfigurationXml": "binary"
}
```
