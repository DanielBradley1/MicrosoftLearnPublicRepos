<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/senddtmftonesoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# sendDtmfTonesOperation resource type

Namespace: microsoft.graph

Represents an operation to get the results of an action to send DTMF tones in a call.

Inherits from [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | A unique string that the client sends to Microsoft Graph to keep context in multiple requests. Maximum size is 256 characters. |
| completionReason | [sendDtmfCompletionReason](https://learn.microsoft.com/en-us/graph/api/resources/senddtmftonesoperation?view=graph-rest-1.0#senddtmfcompletionreason-values) | The results of the action. The possible values are: `unknown`, `completedSuccessfully`, `mediaOperationCanceled`, `unknownfutureValue`. |
| id | String | Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information with a specific status code, subcode, and message. Read-only. |
| status | String | The status of the operation. The possible values are: `notStarted`, `running`, `completed`, `failed`. |

### sendDtmfCompletionReason values

| Member | Description |
| :--- | :--- |
| unknown | Completion reason with unknown error. |
| completedSuccessfully | Successful completion. |
| mediaOperationCanceled | Media operation was canceled. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "string",
  "completionReason": "string",
  "id": "string",
  "resultInfo": {"@odata.type": "#microsoft.graph.resultInfo"},
  "status": "string"
}
```
