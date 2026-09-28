<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filterclause?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# filterClause resource type

Namespace: microsoft.graph

Represents a single assertion that a candidate object must satisfy, and is evaluated to either `true` \(object satisfies the assertion\) or `false` \(object does not satisfy the assertion\). This object is configured in the **clauses** property of [filterGroup](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filtergroup?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operatorName | String | Name of the operator to be applied to the source and target operands. Must be one of the supported operators. Supported operators can be discovered. |
| sourceOperandName | String | Name of source operand \(the operand being tested\). The source operand name must match one of the attribute names on the source object. |
| targetOperand | [filterOperand](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filteroperand?view=graph-rest-1.0) | Values that the source operand will be tested against. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "operatorName": "String",
  "sourceOperandName": "String",
  "targetOperand": {
    "@odata.type": "microsoft.graph.filterOperand"
  }
}
```
