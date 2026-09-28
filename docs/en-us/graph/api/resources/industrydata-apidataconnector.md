<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# apiDataConnector resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base type for API connectors, which establish a connection to a data source that is available from an API. This is an abstract type.

Inherits from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta).

Base type of [oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apiFormat | microsoft.graph.industryData.apiFormat | The API format of the external system being connected to. The possible values are: `oneRoster`, `unknownFutureValue`. |
| baseUrl | String | The base URL, including the scheme, host, and path for the API, with or without a trailing '/'. For example, "https://example.com/ims/oneRoster/v1p1" |
| credential | [microsoft.graph.industryData.credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta) | A credential to use to connect to the API. |
| displayName | String | The name of the data connector. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sourceSystem | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | The **sourceSystemDefinition** object that this connector is connected to. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.apiDataConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "apiFormat": "String",
  "baseUrl": "String",
  "credential": {
    "@odata.type": "microsoft.graph.industryData.credential"
  }
}
```
