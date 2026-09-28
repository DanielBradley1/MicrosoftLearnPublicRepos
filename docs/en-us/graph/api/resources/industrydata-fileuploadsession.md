<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileuploadsession?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# fileUploadSession resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the file upload session that contains details about the session and container.

The [azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta) uses CSV files uploaded to a secure container that lives only for a finite period of time and is created by calling [azureDataLakeConnector: getUploadSession](https://learn.microsoft.com/en-us/graph/api/industrydata-azuredatalakeconnector-getuploadsession?view=graph-rest-beta). You can then upload the required CSV files to the provided shared access signature \(SAS\) URI in **sessionUri**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| containerExpirationDateTime | DateTimeOffset | The expiration date and time for the container. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| containerId | String | The container ID where the files are uploaded. |
| sessionExpirationDateTime | DateTimeOffset | The expiration date and time for the file upload session. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| sessionUrl | String | The Azure Storage SAS URI to upload source files to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.fileUploadSession",
  "containerExpirationDateTime": "String (timestamp)",
  "containerId": "String",
  "sessionExpirationDateTime": "String (timestamp)",
  "sessionUrl": "String"
}
```
