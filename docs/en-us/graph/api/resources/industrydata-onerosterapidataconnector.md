<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# oneRosterApiDataConnector resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a connection to an OneRoster API data source.

Inherits from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-onerosterapidataconnector-post?view=graph-rest-beta) | [microsoft.graph.industryData.oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta) | Create a new **oneRosterApiDataConnector** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-onerosterapidataconnector-update?view=graph-rest-beta) | [microsoft.graph.industryData.oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta) | Update the properties of a **oneRosterApiDataConnector** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apiFormat | microsoft.graph.industryData.apiFormat | The API format of the external system being connected to. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta).The possible values are: `oneRoster`, `unknownFutureValue`. |
| apiVersion | String | The API version of the OneRoster source. Example: 1.1, 1.2 |
| baseUrl | String | The base URL including the scheme, host, and path for the API \(with or without a trailing '/'\). Example: `https://example.com/ims/oneRoster/v1p1`. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). |
| credential | [microsoft.graph.industryData.credential](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta) | The base type for all supported credentials. Inherited from [apiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-apidataconnector?view=graph-rest-beta). |
| displayName | String | The name of the data connector. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta). |
| isContactsEnabled | Boolean | Indicates whether the user specified to import optional contacts data. |
| isDemographicsEnabled | Boolean | Indicates whether the user specified to import optional demographics data. |
| isFlagsEnabled | Boolean | Indicates whether the user specified to import optional flags data. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sourceSystem | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | The **sourceSystemDefinition** object that this connector is connected to. Inherited from [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.oneRosterApiDataConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "apiFormat": "String",
  "baseUrl": "String",
  "credential": {
    "@odata.type": "microsoft.graph.industryData.credential"
  },
  "apiVersion": "String",
  "isDemographicsEnabled": "Boolean",
  "isFlagsEnabled": "Boolean",
  "isContactsEnabled": "Boolean"
}
```
