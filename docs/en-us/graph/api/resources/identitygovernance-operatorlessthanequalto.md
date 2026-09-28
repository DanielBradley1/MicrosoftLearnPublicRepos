<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorlessthanequalto?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# operatorLessThanEqualTo resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta) that matches users whose date attribute is within **offsetInDays** days of the current date.

Inherits from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming | Specifies whether the operator evaluates dates before, after, or on the date in the user attribute. The possible values are: `before`, `after`, `on`, `unknownFutureValue`. When **offsetInDays** is `0`, this value must be `on`; otherwise, use `before` or `after`. Inherited from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta). |
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
