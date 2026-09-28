<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# azureDataLakeConnector resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a connection to data uploaded to an Azure Data Lake.

Inherits from [fileDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filedataconnector?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-azuredatalakeconnector-post?view=graph-rest-beta) | [microsoft.graph.industryData.azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta) | Create a new **azureDataLakeConnector** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-azuredatalakeconnector-update?view=graph-rest-beta) | [microsoft.graph.industryData.azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta) | Update the properties of an **azureDataLakeConnector** object. |
| [Get upload session](https://learn.microsoft.com/en-us/graph/api/industrydata-azuredatalakeconnector-getuploadsession?view=graph-rest-beta) | [microsoft.graph.industryData.fileUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileuploadsession?view=graph-rest-beta) | Retrieve an upload session used to supply file-based data to an inbound flow. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the data connector. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). |
| fileFormat | [microsoft.graph.industryData.fileFormatReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileformatreferencevalue?view=graph-rest-beta) | The file format that external systems can upload using this connector. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sourceSystem | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | The **sourceSystemDefinition** object that this connector is connected to. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.azureDataLakeConnector",
  "displayName": "String",
  "fileFormat": {
    "@odata.type": "microsoft.graph.industryData.fileFormatReferenceValue"
  }
}
```
