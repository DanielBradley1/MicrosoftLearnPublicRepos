<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectenforcement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicySubjectEnforcement resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current enforcement state for a subject and lifecycle policy. Returned in the **enforcement** property of a [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isLocked | Boolean | Indicates whether enforcement is locked. |
| isTerminal | Boolean | Indicates whether enforcement reached a terminal state. |
| lastAction | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementActionState](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicyenforcementactionstate-values) | The last completed enforcement action. The possible values are: `none`, `warningStateEnabled`, `nonComplianceNotificationSent`, `firstNotificationSent`, `secondNotificationSent`, `finalNotificationSent`, `disabled`, `deleted`, `complianceRestored`, `unknownFutureValue`. |
| lastActionDateTime | DateTimeOffset | The date and time when the last enforcement action completed. |
| nextAction | [microsoft.graph.identityGovernance.lifecyclePolicyNextEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicynextenforcementaction-values) | The next enforcement action. The possible values are: `nonComplianceNotification`, `firstNotification`, `secondNotification`, `finalNotification`, `disable`, `disableNotification`, `delete`, `unknownFutureValue`. |
| nextActionDateTime | DateTimeOffset | The date and time when the next enforcement action is scheduled. |
| status | [microsoft.graph.identityGovernance.lifecyclePolicyEnforcementStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicyenforcementstatus-values) | The current enforcement status. The possible values are: `notRequired`, `notStarted`, `processing`, `waiting`, `actionDue`, `complete`, `unknown`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicySubjectEnforcement",
  "isLocked": "Boolean",
  "isTerminal": "Boolean",
  "lastAction": "String",
  "lastActionDateTime": "String (timestamp)",
  "nextAction": "String",
  "nextActionDateTime": "String (timestamp)",
  "status": "String"
}
```
