<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# noncustodialDataSource resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Noncustodial data sources let you add data to a case without having to associate it to a custodian. To learn more, visit [Add noncustodial data sources to an Advanced eDiscovery case](https://learn.microsoft.com/en-us/microsoft-365/compliance/non-custodial-data-sources)

Inherits from [dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/ediscovery-noncustodialdatasource-list?view=graph-rest-beta) | [microsoft.graph.ediscovery.noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) collection | Get a list of the [noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ediscovery-noncustodialdatasource-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) | Read the properties and relationships of a [noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) object. |
| [Release](https://learn.microsoft.com/en-us/graph/api/ediscovery-noncustodialdatasource-release?view=graph-rest-beta) | None | Releases a noncustodial data source. |
| [List datasource](https://learn.microsoft.com/en-us/graph/api/ediscovery-noncustodialdatasource-list-datasource?view=graph-rest-beta) | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | Get the dataSource resources from the dataSource navigation property. |
| [Create](https://learn.microsoft.com/en-us/graph/api/ediscovery-noncustodialdatasource-post?view=graph-rest-beta) | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) | Create a new dataSource object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applyHoldToSource | Boolean | Indicates if hold is applied to noncustodial data source \(such as mailbox or site\). |
| createdDateTime | DateTimeOffset | Created date and time of the nonCustodialDataSource. Inherited from [microsoft.graph.ediscovery.dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta). |
| displayName | String | Display name of the noncustodialDataSource. Inherited from [microsoft.graph.ediscovery.dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta). |
| id | String | Unique identifier of the nonCustodialDataSource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | Last modified date and time of the nonCustodialDataSource. Inherited from [microsoft.graph.ediscovery.dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta). |
| releasedDateTime | DateTimeOffset | Date and time that the nonCustodialDataSource was released from the case. Inherited from [microsoft.graph.ediscovery.dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta). |
| status | microsoft.graph.ediscovery.dataSourceContainerStatus | Latest status of the nonCustodialDataSource. Inherited from [microsoft.graph.ediscovery.dataSourceContainer](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasourcecontainer?view=graph-rest-beta). The possible values are: `Active`, `Released`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dataSource | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) | User source or SharePoint site data source as noncustodial data source. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.noncustodialDataSource",
  "id": "String (identifier)",
  "status": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "releasedDateTime": "String (timestamp)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "applyHoldToSource": "Boolean"
}
```
