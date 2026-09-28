<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSSoftwareUpdateCategorySummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS software update category summary report for a device and user

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSSoftwareUpdateCategorySummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatecategorysummary-list?view=graph-rest-beta) | [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) collection | List properties and relationships of the [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) objects. |
| [Get macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatecategorysummary-get?view=graph-rest-beta) | [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) | Read properties and relationships of the [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) object. |
| [Create macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatecategorysummary-create?view=graph-rest-beta) | [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) | Create a new [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) object. |
| [Delete macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatecategorysummary-delete?view=graph-rest-beta) | None | Deletes a [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta). |
| [Update macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatecategorysummary-update?view=graph-rest-beta) | [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) | Update the properties of a [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | The name of the report |
| deviceId | String | The device ID. |
| userId | String | The user ID. |
| updateCategory | [macOSSoftwareUpdateCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategory?view=graph-rest-beta) | Software update type. Possible values are: `critical`, `configurationDataFile`, `firmware`, `other`. |
| successfulUpdateCount | Int32 | Number of successful updates on the device |
| failedUpdateCount | Int32 | Number of failed updates on the device |
| totalUpdateCount | Int32 | Number of total updates on the device |
| lastUpdatedDateTime | DateTimeOffset | Last date time the report for this device was updated. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| updateStateSummaries | [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) collection | Summary of the update states. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateCategorySummary",
  "id": "String (identifier)",
  "displayName": "String",
  "deviceId": "String",
  "userId": "String",
  "updateCategory": "String",
  "successfulUpdateCount": 1024,
  "failedUpdateCount": 1024,
  "totalUpdateCount": 1024,
  "lastUpdatedDateTime": "String (timestamp)"
}
```
