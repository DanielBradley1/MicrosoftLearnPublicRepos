<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessing?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicyScopeProcessing resource type

Namespace: microsoft.graph.identityGovernance

Represents current and latest retained scope-processing information for a lifecycle policy. Returned in the **scopeProcessing** property of a [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentStartedDateTime | DateTimeOffset | The date and time when the current scope-processing operation started. |
| currentStatus | microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingStatus | The current scope-processing status. The possible values are: `idle`, `notStarted`, `evaluating`, `processing`, `unknownFutureValue`. |
| lastSuccessfulProcessingDateTime | DateTimeOffset | The date and time when scope processing last completed successfully. |
| latestAttempt | [microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingAttempt](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessingattempt?view=graph-rest-1.0) | The latest retained scope-processing attempt. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessing",
  "currentStartedDateTime": "String (timestamp)",
  "currentStatus": "String",
  "lastSuccessfulProcessingDateTime": "String (timestamp)",
  "latestAttempt": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingAttempt"
  }
}
```
