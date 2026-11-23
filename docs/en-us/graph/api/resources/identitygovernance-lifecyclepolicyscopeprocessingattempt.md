<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessingattempt?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyScopeProcessingAttempt resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the latest retained scope-processing attempt for a lifecycle policy. Returned in the **latestAttempt** property of [lifecyclePolicyScopeProcessing](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessing?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | The date and time when the attempt completed. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | The error associated with an unsuccessful attempt. |
| startedDateTime | DateTimeOffset | The date and time when the attempt started. |
| status | [microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingAttemptStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicyscopeprocessingattemptstatus-values) | The outcome or current state of the attempt. The possible values are: `notStarted`, `evaluating`, `processing`, `completed`, `failed`, `timedOut`, `invalidScope`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingAttempt",
  "completedDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "startedDateTime": "String (timestamp)",
  "status": "String"
}
```
