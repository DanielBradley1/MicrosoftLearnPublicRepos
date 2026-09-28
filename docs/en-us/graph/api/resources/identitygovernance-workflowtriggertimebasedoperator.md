<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# workflowTriggerTimeBasedOperator resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract [workflowExecutionTriggerOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontriggeroperator?view=graph-rest-beta) that evaluates a user's date attribute relative to the current date. This type can't be instantiated directly.

Configure this type in the **operator** property of [timeBasedAttributeTriggerV2](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-beta).

The following types are derived from this type:

- [operatorBetween](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorbetween?view=graph-rest-beta)
- [operatorEqualTo](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorequalto?view=graph-rest-beta)
- [operatorLessThanEqualTo](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorlessthanequalto?view=graph-rest-beta)

The type of an operator is differentiated by its `@odata.type` property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming | Specifies whether the operator evaluates dates before, after, or on the date in the user attribute. The possible values are: `before`, `after`, `on`, `unknownFutureValue`. Each derived type defines the values it supports. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowTriggerTimeBasedOperator",
  "eventTiming": "String"
}
```
