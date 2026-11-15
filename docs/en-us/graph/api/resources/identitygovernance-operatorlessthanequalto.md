<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorlessthanequalto?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# operatorLessThanEqualTo resource type

Namespace: microsoft.graph.identityGovernance

Represents a [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0) that matches users whose date attribute is within **offsetInDays** days of the current date.

Inherits from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0).

Configure this type in the **operator** property of [timeBasedAttributeTriggerV2](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | [microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-1.0#workflowtriggeroperatoreventtiming-values) | Specifies whether the operator evaluates dates before, after, or on the date in the user attribute. The possible values are: `before`, `after`, `on`, `unknownFutureValue`. When **offsetInDays** is `0`, this value must be `on`; otherwise, use `before` or `after`. Inherited from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0). |
| offsetInDays | Int32 | The maximum number of days between the current date and the date in the user attribute. The value must be a nonnegative integer. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.operatorLessThanEqualTo",
  "eventTiming": "String",
  "offsetInDays": "Integer"
}
```
