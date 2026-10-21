<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreportrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# accessDriftReportRequest resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the parameters for generating or downloading a tenant-wide access drift report.

This object is supplied as the **request** parameter of the [downloadFile](https://learn.microsoft.com/en-us/graph/api/accessdriftreport-downloadfile?view=graph-rest-beta) and [generateDownloadUri](https://learn.microsoft.com/en-us/graph/api/accessdriftreport-generatedownloaduri?view=graph-rest-beta) actions of [accessDriftReport](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftreport?view=graph-rest-beta).

The report includes all catalogs and resources for the specified resource type. To retrieve catalog-scoped access drift data, use the access drift summary and details APIs with a catalog filter.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogId | String | Reserved for future use. This property is currently ignored, and the report includes data from all catalogs. |
| reportFormat | String | The file format of the report. The supported values are `csv` and `parquet`. For the **generateDownloadUri** action, specify `parquet`. |
| resourceIds | String collection | Reserved for future use. This property is currently ignored, and the report includes all resources of the specified resource type. |
| resourceType | [accessDriftReportResourceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#accessdriftreportresourcetype-values) | The type of resource for the report. The possible values are: `application`, `group`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessDriftReportRequest",
  "catalogId": "String",
  "reportFormat": "String",
  "resourceIds": [
    "String"
  ],
  "resourceType": "String"
}
```
