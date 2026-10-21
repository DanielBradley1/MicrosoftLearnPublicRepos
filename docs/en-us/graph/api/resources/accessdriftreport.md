<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# accessDriftReport resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a transient entity for downloading access drift report files. This resource provides actions to generate a time-limited download URI or stream the report file directly.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [downloadFile](https://learn.microsoft.com/en-us/graph/api/accessdriftreport-downloadfile?view=graph-rest-beta) | Stream | Download the latest access drift report file directly. |
| [generateDownloadUri](https://learn.microsoft.com/en-us/graph/api/accessdriftreport-generatedownloaduri?view=graph-rest-beta) | [accessDriftReport](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreport?view=graph-rest-beta) | Generate a time-limited download URI for the latest access drift report. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| downloadUri | String | The time-limited SAS URI for downloading the report file. This property is populated only in the response of the **generateDownloadUri** action. |
| expiresAt | DateTimeOffset | The date and time when the download URI expires. This property is populated only in the response of the **generateDownloadUri** action. |
| id | String | A randomly generated identifier for this report instance. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resourceType | [accessDriftReportResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftreportresourcetype-values) | The resource type of the report. The possible values are: `application`, `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessDriftReport",
  "id": "String (identifier)",
  "downloadUri": "String",
  "expiresAt": "String (timestamp)",
  "resourceType": "String"
}
```
