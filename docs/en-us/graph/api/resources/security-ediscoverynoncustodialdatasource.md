<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# ediscoveryNoncustodialDataSource resource type

Namespace: microsoft.graph.security

Enables the addition of data to an eDiscovery case without associating it with a custodian. For details, see [Add noncustodial data sources to an eDiscovery \(Premium\) case](https://learn.microsoft.com/en-us/microsoft-365/compliance/non-custodial-data-sources).

Inherits from [dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/security-datasourcecontainer?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List non-custodial data sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-list-noncustodialsources?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) collection | Get a list of the [ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) objects and their properties. |
| [Add non-custodial data sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-post-noncustodialsources?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) | Create a new [ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoverynoncustodialdatasource-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) object. |
| [Update index](https://learn.microsoft.com/en-us/graph/api/security-ediscoverynoncustodialdatasource-updateindex?view=graph-rest-1.0) | None | Triggers a indexOperation to make a noncustodial data source and associated data sources searchable. |
| [Release](https://learn.microsoft.com/en-us/graph/api/security-ediscoverynoncustodialdatasource-release?view=graph-rest-1.0) | None | Release a noncustodial data source from a case. |
| [Apply hold](https://learn.microsoft.com/en-us/graph/api/security-ediscoverynoncustodialdatasource-applyhold?view=graph-rest-1.0) | None | Start the process of applying hold to eDiscovery noncustodial data sources. |
| [Remove hold](https://learn.microsoft.com/en-us/graph/api/security-ediscoverynoncustodialdatasource-removehold?view=graph-rest-1.0) | None | Start the process of removing hold from eDiscovery noncustodial data sources. |
| [Get last index operation](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-lastindexoperation?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0) collection | Get a list of the [ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0) associated with an [ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Created date and time of the nonCustodialDataSource. Inherited from [microsoft.graph.security.datasourcecontainer](https://learn.microsoft.com/en-us/graph/api/resources/security-datasourcecontainer?view=graph-rest-1.0). |
| displayName | String | Display name of the noncustodialDataSource. Inherited from [microsoft.graph.security.datasourcecontainer](https://learn.microsoft.com/en-us/graph/api/resources/security-datasourcecontainer?view=graph-rest-1.0). |
| holdStatus | microsoft.graph.security.dataSourceHoldStatus | The hold status of the nonCustodialDataSource. The possible values are: `notApplied`, `applied`, `applying`, `removing`, `partial` |
| id | String | Unique identifier of the nonCustodialDataSource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | Last modified date and time of the nonCustodialDataSource. Inherited from [microsoft.graph.security.datasourcecontainer](https://learn.microsoft.com/en-us/graph/api/resources/security-datasourcecontainer?view=graph-rest-1.0). |
| releasedDateTime | DateTimeOffset | Date and time that the nonCustodialDataSource was released from the case. Inherited from [microsoft.graph.security.datasourcecontainer](https://learn.microsoft.com/en-us/graph/api/resources/security-datasourcecontainer?view=graph-rest-1.0). |
| status | microsoft.graph.security.dataSourceContainerStatus | Latest status of the nonCustodialDataSource. Inherited from [microsoft.graph.security.datasourcecontainer](https://learn.microsoft.com/en-us/graph/api/resources/security-datasourcecontainer?view=graph-rest-1.0). The possible values are: `Active`, `Released`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dataSource | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) | User source or SharePoint site data source as noncustodial data source. |
| lastIndexOperation | [microsoft.graph.security.ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0) | Operation entity that represents the latest indexing for the noncustodial data source. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryNoncustodialDataSource",
  "id": "String (identifier)",
  "status": "String",
  "holdStatus": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "releasedDateTime": "String (timestamp)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)"
}
```
