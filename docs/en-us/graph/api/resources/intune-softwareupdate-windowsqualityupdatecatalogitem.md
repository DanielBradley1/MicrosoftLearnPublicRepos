<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdateCatalogItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows update catalog item entity

Inherits from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsQualityUpdateCatalogItems](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatecatalogitem-list?view=graph-rest-beta) | [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) collection | List properties and relationships of the [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) objects. |
| [Get windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatecatalogitem-get?view=graph-rest-beta) | [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) | Read properties and relationships of the [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) object. |
| [Create windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatecatalogitem-create?view=graph-rest-beta) | [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) | Create a new [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) object. |
| [Delete windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatecatalogitem-delete?view=graph-rest-beta) | None | Deletes a [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta). |
| [Update windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatecatalogitem-update?view=graph-rest-beta) | [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) | Update the properties of a [windowsQualityUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitem?view=graph-rest-beta) object. |
| [retrieveWindowsQualityUpdateCatalogItemDetails function](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatecatalogitem-retrievewindowsqualityupdatecatalogitemdetails?view=graph-rest-beta) | [windowsQualityUpdateCatalogItemPolicyDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitempolicydetail?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The catalog item id. Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| displayName | String | The display name for the catalog item. Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| releaseDateTime | DateTimeOffset | The date the catalog item was released Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| endOfSupportDate | DateTimeOffset | The last supported date for a catalog item Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| kbArticleId | String | Identifies the knowledge base article associated with the Windows quality update catalog item. Read-only |
| classification | [windowsQualityUpdateCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecategory?view=graph-rest-beta) | The category of the Windows quality update. Possible values are: all, security, nonSecurity. Read-only. Possible values are: `all`, `security`, `nonSecurity`, `unknownFutureValue`, `quickMachineRecovery`. |
| qualityUpdateCadence | [windowsQualityUpdateCadence](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecadence?view=graph-rest-beta) | The publishing cadence of the quality update. Possible values are: monthly, outOfBand. This property cannot be modified and is automatically populated when the catalog is created. Read-only. Possible values are: `monthly`, `outOfBand`, `unknownFutureValue`. |
| isExpeditable | Boolean | When TRUE, indicates that the quality updates qualify for expedition. When FALSE, indicates the quality updates do not quality for expedition. Default value is FALSE. Read-only |
| productRevisions | [windowsQualityUpdateCatalogProductRevision](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogproductrevision?view=graph-rest-beta) collection | The operating system product revisions that are released as part of this quality update. Read-only. |
| cveSeverityInformation | [windowsQualityUpdateCveSeverityInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecveseverityinformation?view=graph-rest-beta) | CVE information for catalog items |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateCatalogItem",
  "id": "String (identifier)",
  "displayName": "String",
  "releaseDateTime": "String (timestamp)",
  "endOfSupportDate": "String (timestamp)",
  "kbArticleId": "String",
  "classification": "String",
  "qualityUpdateCadence": "String",
  "isExpeditable": true,
  "productRevisions": [
    {
      "@odata.type": "microsoft.graph.windowsQualityUpdateCatalogProductRevision",
      "displayName": "String",
      "releaseDateTime": "String (timestamp)",
      "versionName": "String",
      "productName": "String",
      "osBuild": {
        "@odata.type": "microsoft.graph.windowsQualityUpdateProductBuildVersionDetail",
        "majorVersionNumber": 1024,
        "minorVersionNumber": 1024,
        "buildNumber": 1024,
        "updateBuildRevision": 1024
      },
      "knowledgeBaseArticle": {
        "@odata.type": "microsoft.graph.windowsQualityUpdateProductKnowledgeBaseArticle",
        "articleId": "String",
        "articleUrl": "String"
      }
    }
  ],
  "cveSeverityInformation": {
    "@odata.type": "microsoft.graph.windowsQualityUpdateCveSeverityInformation",
    "maxSeverityLevel": "String",
    "maxBaseScore": "4.2",
    "exploitedCves": [
      {
        "@odata.type": "microsoft.graph.windowsQualityUpdateCveDetail",
        "cveNumber": "String",
        "cveInformationUrl": "String"
      }
    ]
  }
}
```
