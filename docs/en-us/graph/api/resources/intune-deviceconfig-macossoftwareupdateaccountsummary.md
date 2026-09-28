<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSSoftwareUpdateAccountSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS software update account summary report for a device and user

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSSoftwareUpdateAccountSummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateaccountsummary-list?view=graph-rest-beta) | [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) collection | List properties and relationships of the [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) objects. |
| [Get macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateaccountsummary-get?view=graph-rest-beta) | [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) | Read properties and relationships of the [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) object. |
| [Create macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateaccountsummary-create?view=graph-rest-beta) | [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) | Create a new [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) object. |
| [Delete macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateaccountsummary-delete?view=graph-rest-beta) | None | Deletes a [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta). |
| [Update macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateaccountsummary-update?view=graph-rest-beta) | [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) | Update the properties of a [macOSSoftwareUpdateAccountSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateaccountsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | The name of the report |
| deviceId | String | The device ID. |
| userId | String | The user ID. |
| deviceName | String | The device name. |
| userPrincipalName | String | The user principal name |
| osVersion | String | The OS version. |
| successfulUpdateCount | Int32 | Number of successful updates on the device. |
| failedUpdateCount | Int32 | Number of failed updates on the device. |
| totalUpdateCount | Int32 | Number of total updates on the device. |
| lastUpdatedDateTime | DateTimeOffset | Last date time the report for this device was updated. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categorySummaries | [macOSSoftwareUpdateCategorySummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatecategorysummary?view=graph-rest-beta) collection | Summary of the updates by category. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateAccountSummary",
  "id": "String (identifier)",
  "displayName": "String",
  "deviceId": "String",
  "userId": "String",
  "deviceName": "String",
  "userPrincipalName": "String",
  "osVersion": "String",
  "successfulUpdateCount": 1024,
  "failedUpdateCount": 1024,
  "totalUpdateCount": 1024,
  "lastUpdatedDateTime": "String (timestamp)"
}
```
