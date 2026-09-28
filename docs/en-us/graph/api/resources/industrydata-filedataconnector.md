<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filedataconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# fileDataConnector resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract type that provides the resources to establish a connection with a file-based data source.

Inherits from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta).

Base type of [azureDataLakeConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-azuredatalakeconnector?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the data connector. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sourceSystem | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | The **sourceSystemDefinition** this connector is connected to. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.fileDataConnector",
  "displayName": "String"
}
```
