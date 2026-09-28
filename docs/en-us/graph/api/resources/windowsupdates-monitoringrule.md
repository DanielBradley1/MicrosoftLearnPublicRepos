<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-monitoringrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# monitoringRule resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Rule defining a signal and threshold to monitor, and the action to perform when met.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.windowsUpdates.monitoringAction | The action triggered when the threshold for the given signal is reached. The possible values are: `alertError`, `pauseDeployment`, `offerFallback`, `unknownFutureValue`. The `offerFallback` member is only supported on feature update deployments of Windows 11 and must be paired with the `ineligible` signal. The fallback version offered is the version 22H2 of Windows 10. |
| signal | microsoft.graph.windowsUpdates.monitoringSignal | The signal to monitor. The possible values are: `rollback`, `ineligible`, `unknownFutureValue`. The `ineligible` member is only supported on feature update deployments of Windows 11 and must be paired with the `offerFallback` action. |
| threshold | Int32 | The threshold for a signal at which to trigger the action. An integer from `1` to `100` \(inclusive\). This value is ignored when the signal is `ineligible` and the action is `offerFallback`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.monitoringRule",
  "action": "String",
  "signal": "String",
  "threshold": "Int32"
}
```
