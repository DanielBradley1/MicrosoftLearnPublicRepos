<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycondition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# slaPolicyCondition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a leaf condition that compares a case property with one or more values in the **conditions** property of an [slaPolicyCriteriaBlock](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycriteriablock?view=graph-rest-beta).

Inherits from [slaPolicyConditionBase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicyconditionbase?view=graph-rest-beta).

Set `@odata.type` to `#microsoft.graph.security.caseManagement.slaPolicyCondition` when supplying a leaf condition.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operator | [microsoft.graph.security.caseManagement.slaPolicyConditionOperator](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-casemanagement?view=graph-rest-beta#slapolicyconditionoperator-values) | The comparison operator. The default value is `equals`. The possible values are: `equals`, `notEquals`, `contains`, `doesNotContain`, `isEmpty`, `isNotEmpty`, `changed`, `changedTo`, `changedFrom`, `isBefore`, `isAfter`, `greaterThan`, `lessThan`, `anyOf`, `noneOf`, `unknownFutureValue`. |
| property | String | The name of the case property to evaluate, such as `priority`. |
| values | String collection | The comparison values for the condition. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCondition",
  "property": "String",
  "operator": "String",
  "values": [
    "String"
  ]
}
```
