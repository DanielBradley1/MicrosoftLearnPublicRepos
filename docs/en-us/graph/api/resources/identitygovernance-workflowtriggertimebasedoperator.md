<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# workflowTriggerTimeBasedOperator resource type

Namespace: microsoft.graph.identityGovernance

Represents an abstract [workflowExecutionTriggerOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontriggeroperator?view=graph-rest-1.0) that evaluates a user's date attribute relative to the current date. This type can't be instantiated directly.

Configure this type in the **operator** property of [timeBasedAttributeTriggerV2](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-1.0).

The following types are derived from this type:

- [operatorBetween](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorbetween?view=graph-rest-1.0)
- [operatorEqualTo](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorequalto?view=graph-rest-1.0)
- [operatorLessThanEqualTo](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorlessthanequalto?view=graph-rest-1.0)

The type of an operator is differentiated by its `@odata.type` property.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | [microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-1.0#workflowtriggeroperatoreventtiming-values) | Specifies whether the operator evaluates dates before, after, or on the date in the user attribute. The possible values are: `before`, `after`, `on`, `unknownFutureValue`. Each derived type defines the values it supports. |

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
