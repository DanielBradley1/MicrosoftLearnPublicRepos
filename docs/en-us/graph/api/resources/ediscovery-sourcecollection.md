<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# sourceCollection resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents an eDiscovery collection, commonly known as a search. For details, see [Collect data for a case in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/collecting-data-for-ediscovery).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Add additional sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-post-additionalsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | Add an additional **dataSource** object to the source collection. |
| [Add custodian sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-post-custodiansources?view=graph-rest-beta) | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | Add a custodian **dataSource** object to the source collection. |
| [Add noncustodial source](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-post-noncustodialsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.noncustodialSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) collection | Add a noncustodial source **noncustodialSource** object to the source collection. |
| [List](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-sourcecollections?view=graph-rest-beta) | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) collection | Get a list of the **sourceCollection** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-sourcecollections?view=graph-rest-beta) | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | Create a new **sourceCollection** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | Read the properties and relationships of a **sourceCollection** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | Update the properties of a **sourceCollection** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-delete?view=graph-rest-beta) | None | Delete a **sourceCollection** object. |
| [Estimate statistics](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-estimatestatistics?view=graph-rest-beta) | None | Run an estimate of the number of emails and documents in the source collection. |
| [List additional sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-list-additionalsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | Get a list of additional **dataSource** objects associated with a source collection. |
| [List custodian sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-list-custodiansources?view=graph-rest-beta) | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | Get a list of custodian **dataSource** objects associated with a source collection. |
| [List noncustodial sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-list-noncustodialsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.noncustodialSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) collection | Get a list of noncustodial sources **noncustodialSource** objects associated with a source collection. |
| [Purge data](https://learn.microsoft.com/en-us/graph/api/ediscovery-sourcecollection-purgedata?view=graph-rest-beta) | None | Run a purge data operation on the Teams data contained in the source collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentQuery | String | The query string in KQL \(Keyword Query Language\) query. For details, see [Keyword queries and search conditions for Content Search and eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/keyword-queries-and-search-conditions). You can refine searches by using fields paired with values; for example, *subject:"Quarterly Financials" AND Date>=06/01/2016 AND Date<=07/01/2016*. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the **sourceCollection**. |
| createdDateTime | DateTimeOffset | The date and time the **sourceCollection** was created. |
| dataSourceScopes | microsoft.graph.ediscovery.dataSourceScopes | When specified, the collection spans across a service for an entire workload. The possible values are: `none`, `allTenantMailboxes`, `allTenantSites`, `allCaseCustodians`, `allCaseNoncustodialDataSources`. |
| description | String | The description of the **sourceCollection**. |
| displayName | String | The display name of the **sourceCollection**. |
| id | String | The ID for the **sourceCollection**. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The last user who modified the **sourceCollection**. |
| lastModifiedDateTime | DateTimeOffset | The last date and time the **sourceCollection** was modified. |

### dataSourceScopes values

| Member | Description |
| :--- | --- |
| none | Don't specify any scopes - locations would be referenced separately. |
| allTenantMailboxes | Include all tenant mailboxes in the **sourceCollection**. |
| allTenantSites | Include all tenant sites in the **sourceCollection**. |
| allCaseCustodians | Include all custodian locations in the **sourceCollection**. |
| allCaseNoncustodialDataSources | Include all noncustodial data sources in the **sourceCollection**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| additionalSources | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | Adds an additional source to the **sourceCollection**. |
| addToReviewSetOperation | [microsoft.graph.ediscovery.addToReviewSetOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-addtoreviewsetoperation?view=graph-rest-beta) | Adds the results of the **sourceCollection** to the specified **reviewSet**. |
| custodianSources | [microsoft.graph.ediscovery.dataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-datasource?view=graph-rest-beta) collection | **Custodian** sources that are included in the **sourceCollection**. |
| lastEstimateStatisticsOperation | [microsoft.graph.ediscovery.estimateStatisticsOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-estimatestatisticsoperation?view=graph-rest-beta) | The last estimate operation associated with the **sourceCollection**. |
| noncustodialSources | [microsoft.graph.ediscovery.noncustodialDataSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-noncustodialdatasource?view=graph-rest-beta) collection | **noncustodialDataSource** sources that are included in the **sourceCollection** |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.sourceCollection",
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
