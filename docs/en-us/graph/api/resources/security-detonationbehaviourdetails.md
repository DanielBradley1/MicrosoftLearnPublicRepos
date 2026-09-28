<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detonationbehaviourdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# detonationBehaviourDetails resource type \(deprecated\)

Namespace: microsoft.graph.security

Shows the exact events that took place during detonation. It's returned in the **detonationBehaviourDetails** property of [detonationDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationdetails?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionStatus | String | The status of the action performed during detonation \(e.g., "Successful", "Failed", "Blocked"\). |
| behaviourCapability | String | Categorizes the capability or type of behavior observed. |
| behaviourGroup | String | Groups related behaviors together for classification purposes. |
| details | String | More contextual information about the observed behavior or action. |
| eventDateTime | DateTimeOffset | The date and time when the behavior or action was observed during detonation. |
| operation | String | The specific operation or action that was performed. |
| processId | String | The unique identifier of the process involved in the behavior. |
| processName | String | The name of the process that performed or was involved in the behavior. |
| target | String | The target of the operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.detonationBehaviourDetails",
  "behaviourCapability": "String",
  "behaviourGroup": "String",
  "eventDateTime": "String (timestamp)",
  "processName": "String",
  "processId": "String",
  "operation": "String",
  "target": "String",
  "details": "String",
  "actionStatus": "String"
}
```
