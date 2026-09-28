<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# securityBaselineCategoryStateSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The security baseline per category compliance state summary for the security baseline of the account.

Inherits from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List securityBaselineCategoryStateSummaries](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinecategorystatesummary-list?view=graph-rest-beta) | [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) collection | List properties and relationships of the [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) objects. |
| [Get securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinecategorystatesummary-get?view=graph-rest-beta) | [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) | Read properties and relationships of the [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) object. |
| [Create securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinecategorystatesummary-create?view=graph-rest-beta) | [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) | Create a new [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) object. |
| [Delete securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinecategorystatesummary-delete?view=graph-rest-beta) | None | Deletes a [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta). |
| [Update securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinecategorystatesummary-update?view=graph-rest-beta) | [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) | Update the properties of a [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| secureCount | Int32 | Number of secure devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| notSecureCount | Int32 | Number of not secure devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| unknownCount | Int32 | Number of unknown devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| errorCount | Int32 | Number of error devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| conflictCount | Int32 | Number of conflict devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| notApplicableCount | Int32 | Number of not applicable devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| displayName | String | The category name |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.securityBaselineCategoryStateSummary",
  "id": "String (identifier)",
  "secureCount": 1024,
  "notSecureCount": 1024,
  "unknownCount": 1024,
  "errorCount": 1024,
  "conflictCount": 1024,
  "notApplicableCount": 1024,
  "displayName": "String"
}
```
