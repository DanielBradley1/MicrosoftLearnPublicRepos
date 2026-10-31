<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycriteriablock?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# slaPolicyCriteriaBlock resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a group of conditions combined by a logical operator in the **setCriteria**, **exitCriteria**, or **pauseCriteria** property of an [slaPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicydefinition?view=graph-rest-beta), or the **filters** property of an [slaPolicyTimer](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicytimer?view=graph-rest-beta).

A block can also appear in the **conditions** property of another block. The maximum nesting depth is two.

Inherits from [slaPolicyConditionBase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicyconditionbase?view=graph-rest-beta).

For request bodies, set `@odata.type` to `#microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock` when supplying a group. Each nested condition uses `@odata.type` to identify either an [slaPolicyCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycondition?view=graph-rest-beta) or another **slaPolicyCriteriaBlock**. Response payloads can omit `@odata.type` on the criteria block itself.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [microsoft.graph.security.caseManagement.slaPolicyConditionBase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicyconditionbase?view=graph-rest-beta) collection | The leaf conditions or nested groups evaluated by this block. The maximum nesting depth is two. |
| logicalOperator | [microsoft.graph.security.caseManagement.slaPolicyLogicalOperator](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-casemanagement?view=graph-rest-beta#slapolicylogicaloperator-values) | The logical operator that combines the conditions. The possible values are: `and`, `or`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock",
  "logicalOperator": "String",
  "conditions": [
    {
      "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCondition"
    }
  ]
}
```
