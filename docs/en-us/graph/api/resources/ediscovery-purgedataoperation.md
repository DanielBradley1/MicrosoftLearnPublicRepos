<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-purgedataoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# purgeDataOperation resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents an operation to permanently delete data in a sourceCollection. This operation is currently scoped to Microsoft Teams messages only; more data sources will be in scope in the future.

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.ediscovery.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseaction-values) | The type of action the operation represents. The possible values are: `addToReviewSet`,`applyTags`,`contentExport`,`convertToPdf`,`estimateStatistics`,`purgeData`. |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user that created the operation. |
| createdDateTime | DateTimeOffset | The date and time the operation was created. |
| id | String | The ID for the operation. Read-only. |
| percentProgress | Int32 | The progress of the operation. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) | Contains success and failure-specific result information. |
| status | [microsoft.graph.ediscovery.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.purgeDataOperation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "percentProgress": "Integer",
  "status": "String",
  "action": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "resultInfo": {
    "@odata.type": "microsoft.graph.resultInfo"
  }
}
```
