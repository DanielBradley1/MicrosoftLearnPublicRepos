<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# deploymentState resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes and controls the current state of a deployment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| effectiveValue | microsoft.graph.windowsUpdates.deploymentStateValue | Specifies the state of the deployment. Supports a subset of the values for **deploymentStateValue**. The possible values are: `scheduled`, `offering`, `paused`, `unknownFutureValue`. Read-only. |
| reasons | [microsoft.graph.windowsUpdates.deploymentStateReason](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentstatereason?view=graph-rest-beta) collection | Specifies the reasons the deployment has its state value. Read-only. |
| requestedValue | microsoft.graph.windowsUpdates.requestedDeploymentStateValue | Specifies the requested state of the deployment. Supports a subset of the values for **requestedDeploymentStateValue**. The possible values are: `none`, `paused`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.deploymentState",
  "effectiveValue": "String",
  "reasons": [{"@odata.type": "microsoft.graph.windowsUpdates.deploymentStateReason"}],
  "requestedValue": "String"
}
```
