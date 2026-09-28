<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-estimatestatisticsoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# estimateStatisticsOperation resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents the operation that handles estimating the count and size of a [sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta). For details, see [Collect data for a case in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/collecting-data-for-ediscovery).

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.ediscovery.caseAction | The type of operation. The case action for this entity will always be `estimateStatistics`. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time the operation was started. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| indexedItemCount | Int64 | The estimated count of items for the **sourceCollection** that matched the content query. |
| indexedItemsSize | Int64 | The estimated size of items for the **sourceCollection** that matched the content query. |
| mailboxCount | Int32 | The number of mailboxes that had search hits. |
| percentProgress | Int32 | The progress of the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| siteCount | Int32 | The number of mailboxes that had search hits. |
| status | [microsoft.graph.ediscovery.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) | The status of the case operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`. |
| unindexedItemCount | Int64 | The estimated count of unindexed items for the collection. |
| unindexedItemsSize | Int64 | The estimated size of unindexed items for the collection. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sourceCollection | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | eDiscovery collection, commonly known as a search. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#compliance/ediscovery/cases/47746044-fd0b-4a30-acfc-5272b691ba5b/operations/$entity",
    "@odata.type": "#microsoft.graph.ediscovery.estimateStatisticsOperation",
    "createdDateTime": "2021-01-12T18:47:23.3974907Z",
    "completedDateTime": "2021-01-12T18:47:51.1461805Z",
    "percentProgress": 100,
    "status": "succeeded",
    "action": "estimateStatistics",
    "id": "82edd40e182a464fa02c24a36fa94873",
    "indexedItemCount": 2,
    "indexedItemsSize": 39276,
    "unindexedItemCount": 0,
    "unindexedItemsSize": 0,
    "mailboxCount": 1,
    "siteCount": 0,
    "createdBy": {
        "user": {
            "id": "c1db6f13-332a-4d84-b111-914383ff9fc9",
            "displayName": null,
            "userPrincipalName": "admin@contoso.com"
        }
    }
}
```
