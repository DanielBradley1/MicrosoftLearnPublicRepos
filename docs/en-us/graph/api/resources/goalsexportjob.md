<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# goalsExportJob resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the export job for programmatically downloading a specified Viva Goals Explorer view. To learn more about Explorer views, see [Explorer](https://learn.microsoft.com/en-us/viva/goals/explorer).

Inherits from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/goals-list-exportjobs?view=graph-rest-beta) | [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) collection | Get a list of **goalsExportJob** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/goals-post-exportjobs?view=graph-rest-beta) | [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) | Create a new **goalsExportJob** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/goalsexportjob-get?view=graph-rest-beta) | [goalsExportJob](https://learn.microsoft.com/en-us/graph/api/resources/goalsexportjob?view=graph-rest-beta) | Read the properties and relationships of a **goalsExportJob** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The content of the **goalsExportJob**. |
| createdDateTime | DateTimeOffset | The start time of the operation. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| expirationDateTime | DateTimeOffset | The date and time of expiry of the result of the operation. |
| explorerViewId | String | The unique identifier of the explorer view to be exported. |
| goalsOrganizationId | String | The unique identifier of the [viva goals organization](https://learn.microsoft.com/en-us/viva/goals/understand-orgs-and-teams#organizations-in-viva-goals). |
| id | String | The unique identifier for the operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| resourceLocation | String | The URI of the resource on which the operation is performed. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). |
| status | longRunningOperationStatus | The status of the operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-beta). The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.goalsExportJob",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "status": "String",
  "resourceLocation": "String",
  "goalsOrganizationId": "String",
  "explorerViewId": "String",
  "expirationDateTime": "String (timestamp)",
  "content": "Stream"
}
```
