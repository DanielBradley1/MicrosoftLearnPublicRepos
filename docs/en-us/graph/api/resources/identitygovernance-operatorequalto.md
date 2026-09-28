<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-operatorequalto?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# operatorEqualTo resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta) that matches users whose date attribute is exactly **offsetInDays** days from the current date.

Inherits from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventTiming | microsoft.graph.identityGovernance.workflowTriggerOperatorEventTiming | Specifies whether the operator evaluates dates before, after, or on the date in the user attribute. The possible values are: `before`, `after`, `on`, `unknownFutureValue`. When **offsetInDays** is `0`, this value must be `on`; otherwise, use `before` or `after`. Inherited from [workflowTriggerTimeBasedOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtriggertimebasedoperator?view=graph-rest-beta). |
| offsetInDays | Int32 | The exact number of days between the current date and the date in the user attribute. The value must be a nonnegative integer. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.operatorEqualTo",
  "eventTiming": "String",
  "offsetInDays": "Integer"
}
```
