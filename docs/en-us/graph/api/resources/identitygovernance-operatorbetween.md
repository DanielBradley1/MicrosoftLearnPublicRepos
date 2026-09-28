<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorbetween?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# operatorBetween resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta) that matches users whose date attribute falls between two offsets from the current date.

Inherits from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming | Specifies whether the operator evaluates dates before or after the date in the user attribute. The possible values are: `before`, `after`, `unknownFutureValue`. Inherited from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta). |
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
