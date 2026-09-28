<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# industryDataConnector resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base type for connectors that provides the resources to establish a connection with a data source. This is an abstract type.

Base type of [fileDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-filedataconnector?view=graph-rest-beta) and [oneRosterApiDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-onerosterapidataconnector?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-list?view=graph-rest-beta) | [microsoft.graph.industryData.industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) collection | Get a list of the [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-get?view=graph-rest-beta) | [microsoft.graph.industryData.industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) | Read the properties and relationships of an [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-delete?view=graph-rest-beta) | None | Delete an [industryDataConnector](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-industrydataconnector?view=graph-rest-beta) object. |
| [Validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) | None | Perform validations applicable for the specific instance of the data connector. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the data connector. Maximum supported length is 100 characters. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sourceSystem | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | The **sourceSystemDefinition** this connector is connected to. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.industryDataConnector",
  "displayName": "String"
}
```
