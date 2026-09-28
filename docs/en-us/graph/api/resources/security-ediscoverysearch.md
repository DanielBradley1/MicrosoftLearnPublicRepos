<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-31 -->

# ediscoverySearch resource type

Namespace: microsoft.graph.security

Represents an eDiscovery search. For details, see [Collect data for a case in eDiscovery \(Premium\)](https://learn.microsoft.com/en-us/microsoft-365/compliance/collecting-data-for-ediscovery).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-searches?view=graph-rest-1.0) | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) collection | Get a list of the [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-searches?view=graph-rest-1.0) | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | Create a new [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-update?view=graph-rest-1.0) | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | Update the properties of an [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-delete-searches?view=graph-rest-1.0) | None | Delete an [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) object. |
| [Estimate statistics](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-estimatestatistics?view=graph-rest-1.0) | None | Run an estimate statistics operation on the data contained in the eDiscovery search. |
| [Purge data](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-purgedata?view=graph-rest-1.0) | None | Delete Exchange mailbox items or Microsoft Teams messages contained in an eDiscovery search. |
| [Export report](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-exportreport?view=graph-rest-1.0) | None | Export an item report from an estimated [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Export result](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-exportresult?view=graph-rest-1.0) | None | Export results from an estimated [ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [List additional sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-list-additionalsources?view=graph-rest-1.0) | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) collection | Get the list of [additional sources](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Add additional sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-post-additionalsources?view=graph-rest-1.0) | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) | Create a new [additional source](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Get last estimate statistics operation](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-list-lastestimatestatisticsoperation?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryEstimateOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0) collection | Get the last [ediscoveryEstimateOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0) objects and their properties. |
| [List custodian sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-list-custodiansources?view=graph-rest-1.0) | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) collection | Get the list of custodial data sources associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Add custodian sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-post-custodiansources?view=graph-rest-1.0) | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) | Create a new custodian source associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Remove custodian sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-delete-custodiansources?view=graph-rest-1.0) | None | Remove a [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) object. |
| [List non-custodial data sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-list-noncustodialsources?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) collection | Get the list of non-custodialSources associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Add non-custodial data sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-post-noncustodialsources?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) | Create a new non-custodial source associated with an [eDiscovery search](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0). |
| [Remove non-custodial data sources](https://learn.microsoft.com/en-us/graph/api/security-ediscoverysearch-delete-noncustodialsources?view=graph-rest-1.0) | None | Remove an [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentQuery | String | The query string in KQL \(Keyword Query Language\) query. For details, see [Keyword queries and search conditions for Content Search and eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/keyword-queries-and-search-conditions). You can refine searches by using fields paired with values; for example, *subject:"Quarterly Financials" AND Date>=06/01/2016 AND Date<=07/01/2016*. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the **eDiscovery search**. |
| createdDateTime | DateTimeOffset | The date and time the **eDiscovery search** was created. |
| dataSourceScopes | microsoft.graph.security.dataSourceScopes | When specified, the collection spans across a service for an entire workload. The possible values are: `none`, `allTenantMailboxes`, `allTenantSites`, `allCaseCustodians`, `allCaseNoncustodialDataSources`. |
| description | String | The description of the **eDiscovery search**. |
| displayName | String | The display name of the **eDiscovery search**. |
| id | String | The ID for the **eDiscovery search**. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user who modified the **eDiscovery search**. |
| lastModifiedDateTime | DateTimeOffset | The last date and time the **eDiscovery search** was modified. |

### dataSourceScopes values

| Member | Description |
| :--- | --- |
| none | Don't specify any scopes - locations would be referenced separately. |
| allTenantMailboxes | Include all tenant mailboxes in the **eDiscovery search**. |
| allTenantSites | Include all tenant sites in the **eDiscovery search**. |
| allCaseCustodians | Include all custodian locations in the **eDiscovery search**. |
| allCaseNoncustodialDataSources | Include all non-custodial data sources in the **eDiscovery search**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| additionalSources | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) collection | Adds an additional source to the **eDiscovery search**. |
| addToReviewSetOperation | [microsoft.graph.security.ediscoveryAddToReviewSetOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryaddtoreviewsetoperation?view=graph-rest-1.0) | Adds the results of the **eDiscovery search** to the specified **reviewSet**. |
| custodianSources | [microsoft.graph.security.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0) collection | **Custodian** sources that are included in the **eDiscovery search**. |
| lastEstimateStatisticsOperation | [microsoft.graph.security.ediscoveryEstimateOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryestimateoperation?view=graph-rest-1.0) | The last estimate operation associated with the **eDiscovery search**. |
| noncustodialSources | [microsoft.graph.security.ediscoveryNoncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverynoncustodialdatasource?view=graph-rest-1.0) collection | **noncustodialDataSource** sources that are included in the **eDiscovery search** |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoverySearch",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "contentQuery": "String",
  "dataSourceScopes": "String"
}
```
