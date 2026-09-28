<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# sourceSystemDefinition resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an external data source in the real world. The data that is ingested is associated to a source system to identify the record owner.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/industrydata-sourcesystemdefinition-post?view=graph-rest-beta) | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | Create a new [sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-sourcesystemdefinition-list?view=graph-rest-beta) | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) collection | Get a list of the [sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-sourcesystemdefinition-get?view=graph-rest-beta) | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | Read the properties and relationships of a [sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/industrydata-sourcesystemdefinition-update?view=graph-rest-beta) | [microsoft.graph.industryData.sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) | Update the properties of a [sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/industrydata-sourcesystemdefinition-delete?view=graph-rest-beta) | None | Delete a [sourceSystemDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sourcesystemdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the source system. Maximum supported length is 100 characters. |
| userMatchingSettings | [microsoft.graph.industryData.userMatchingSetting](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermatchingsetting?view=graph-rest-beta) collection | A collection of user matching settings by [roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta). |
| vendor | String | The name of the vendor who supplies the source system. Maximum supported length is 100 characters. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.sourceSystemDefinition",
  "displayName": "String",
  "userMatchingSettings": [
    {
      "@odata.type": "microsoft.graph.industryData.userMatchingSetting"
    }
  ],
  "vendor": "String"
}
```
