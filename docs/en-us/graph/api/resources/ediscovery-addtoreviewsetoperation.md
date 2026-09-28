<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-addtoreviewsetoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# addToReviewSetOperation resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Represents an operation to add a [sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) to a [reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta).

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.ediscovery.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseaction-values) | The case action for this entity will always be `addToReviewSet`. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta) |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The user who created the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the operation was started. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta) |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| percentProgress | Int32 | The progress of the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-beta) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). |
| status | [microsoft.graph.ediscovery.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) | The status of the case operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta). The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`. |

### dataCollectionScope values

| Member | Description |
| :--- | --- |
| allVersions | Include all versions of files from sites. |
| linkedFiles | Include **cloud attachment** with emails in the collection. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reviewSet | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) | The review set to which items matching the source collection query are added to. |
| sourceCollection | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | The sourceCollection that items are being added from. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.addToReviewSetOperation",
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
