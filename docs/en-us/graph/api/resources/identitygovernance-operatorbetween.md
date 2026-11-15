<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorbetween?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# operatorBetween resource type

Namespace: microsoft.graph.identityGovernance

Represents a [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0) that matches users whose date attribute falls between two offsets from the current date.

Inherits from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0).

Configure this type in the **operator** property of [timeBasedAttributeTriggerV2](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | [microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-1.0#workflowtriggeroperatoreventtiming-values) | Specifies whether the operator evaluates dates before or after the date in the user attribute. The possible values are: `before`, `after`, `unknownFutureValue`. Inherited from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-1.0). |
| greaterThanOffsetInDays | Int32 | The exclusive lower bound of the date range, in days. The value must be a nonnegative integer and less than **lessThanOffsetInDays**. |
| lessThanOffsetInDays | Int32 | The exclusive upper bound of the date range, in days. The value must be a nonnegative integer and greater than **greaterThanOffsetInDays**. The difference between the upper and lower bounds can't exceed 180 days. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.operatorBetween",
  "eventTiming": "String",
  "greaterThanOffsetInDays": "Integer",
  "lessThanOffsetInDays": "Integer"
}
```
