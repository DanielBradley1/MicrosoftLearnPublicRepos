<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# macOSSoftwareUpdateStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS software update state summary for a device and user

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSSoftwareUpdateStateSummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatestatesummary-list?view=graph-rest-beta) | [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) collection | List properties and relationships of the [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) objects. |
| [Get macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatestatesummary-get?view=graph-rest-beta) | [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) | Read properties and relationships of the [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) object. |
| [Create macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatestatesummary-create?view=graph-rest-beta) | [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) | Create a new [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) object. |
| [Delete macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatestatesummary-delete?view=graph-rest-beta) | None | Deletes a [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta). |
| [Update macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdatestatesummary-update?view=graph-rest-beta) | [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) | Update the properties of a [macOSSoftwareUpdateStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | Human readable name of the software update |
| productKey | String | Product key of the software update. |
| updateCategory | [macOSSoftwareUpdateCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategory?view=graph-rest-beta) | Software update category. Possible values are: `critical`, `configurationDataFile`, `firmware`, `other`. |
| updateVersion | String | Version of the software update |
| state | [macOSSoftwareUpdateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatestate?view=graph-rest-beta) | State of the software update. Possible values are: `success`, `downloading`, `downloaded`, `installing`, `idle`, `available`, `scheduled`, `downloadFailed`, `downloadInsufficientSpace`, `downloadInsufficientPower`, `downloadInsufficientNetwork`, `installInsufficientSpace`, `installInsufficientPower`, `installFailed`, `commandFailed`. |
| lastUpdatedDateTime | DateTimeOffset | Last date time the report for this device and product key was updated. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateStateSummary",
  "id": "String (identifier)",
  "displayName": "String",
  "productKey": "String",
  "updateCategory": "String",
  "updateVersion": "String",
  "state": "String",
  "lastUpdatedDateTime": "String (timestamp)"
}
```
