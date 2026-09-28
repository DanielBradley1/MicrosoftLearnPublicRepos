<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicysyncoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# ediscoveryHoldPolicySyncOperation resource type

Namespace: microsoft.graph.security

Represents an operation that adds or updates a legal hold policy.

For more information, see [Manage holds in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-hold-manage).

Inherits from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseaction-values) | The type of action the operation represents. The possible values are: `contentExport`, `applyTags`, `convertToPdf`, `index`, `estimateStatistics`, `addToReviewSet`, `holdUpdate`, `unknownFutureValue`, `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `purgeData`, `exportReport`, `exportResult`, `holdPolicySync`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| completedDateTime | DateTimeOffset | The date and time the operation was completed. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user that created the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time the operation was created. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| id | String | The ID for the operation. Read-only. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| percentProgress | Int32 | The progress of the operation. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| reportFileMetadata | [microsoft.graph.security.reportFileMetadata](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreportfilemetadata?view=graph-rest-1.0) collection | Contains the properties for report file metadata, including **downloadUrl**, **fileName**, and **size**. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Contains success and failure-specific result information. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |
| status | [microsoft.graph.security.caseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0#caseoperationstatus-values) | The status of the case operation. The possible values are: `notStarted`, `submissionFailed`, `running`, `succeeded`, `partiallySucceeded`, `failed`, `unknownFutureValue`. Inherited from [caseOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-caseoperation?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryHoldPolicySyncOperation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "action": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "percentProgress": "Integer",
  "status": "String",
  "resultInfo": {
    "@odata.type": "microsoft.graph.resultInfo"
  },
  "reportFileMetadata": [
    {
      "@odata.type": "microsoft.graph.security.reportFileMetadata"
    }
  ]
}
```
