<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# evaluation resource type

Namespace: microsoft.graph.security.securityCopilot

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an evaluation in a Security Copilot [prompt](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-prompt?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-prompt-list-evaluations?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.evaluation](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta) collection | Get a list of the evaluation objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-prompt-post-evaluations?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.evaluation](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta) | Create a new evaluation object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-securitycopilot-evaluation-get?view=graph-rest-beta) | [microsoft.graph.security.securityCopilot.evaluation](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.security.securityCopilot.evaluation](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | Evaluation completion time. |
| createdDateTime | DateTimeOffset | Evaluation created time. |
| executionCount | Int64 | Evaluation execution count. |
| id | String | Represents the unique ID of the Security Copilot evaluation. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isCancelled | Boolean | Evaluation cancellation status. |
| lastModifiedDateTime | DateTimeOffset | Evaluation modified time. |
| result | [microsoft.graph.security.securityCopilot.evaluationResult](https://learn.microsoft.com/en-us/graph/api/resources/security-securitycopilot-evaluationresult?view=graph-rest-beta) | Evaluation results collection. |
| runStartDateTime | DateTimeOffset | Evaluation Run start time. |
| state | microsoft.graph.security.securityCopilot.evaluationState | Evaluation state during poll. The possible values are: `unknown`, `created`, `running`, `completed`, `cancelled`, `pending`, `deferred`, `waitingForInput`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.securityCopilot.evaluation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "runStartDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "executionCount": "Integer",
  "isCancelled": "Boolean",
  "result": {
    "@odata.type": "microsoft.graph.security.securityCopilot.evaluationResult"
  },
  "state": "String"
}
```
