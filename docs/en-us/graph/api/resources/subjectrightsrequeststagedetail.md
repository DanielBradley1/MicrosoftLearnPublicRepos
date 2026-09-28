<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# subjectRightsRequestStageDetail resource type

Namespace: microsoft.graph

Represents the properties of the stages of a subject rights request.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Describes the error, if any, for the current stage. |
| stage | [subjectRightsRequestStage](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequeststage?view=graph-rest-1.0) | The stage of the subject rights request. |
| status | subjectRightsRequestStageStatus | Status of the current stage. The possible values are: `notStarted`, `current`, `completed`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectRightsRequestStageDetail",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "stage": "microsoft.graph.subjectRightsRequestStage",
  "status": "microsoft.graph.subjectRightsRequestStageStatus"
}
```
