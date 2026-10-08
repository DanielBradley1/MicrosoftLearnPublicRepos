<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessing?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyScopeProcessing resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents current and latest retained scope-processing information for a lifecycle policy. Returned in the **scopeProcessing** property of a [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentStartedDateTime | DateTimeOffset | The date and time when the current scope-processing operation started. |
| currentStatus | [microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicyscopeprocessingstatus-values) | The current scope-processing status. The possible values are: `idle`, `notStarted`, `evaluating`, `processing`, `unknownFutureValue`. |
| lastSuccessfulProcessingDateTime | DateTimeOffset | The date and time when scope processing last completed successfully. |
| latestAttempt | [microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessingAttempt](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessingattempt?view=graph-rest-beta) | The latest retained scope-processing attempt. |

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
