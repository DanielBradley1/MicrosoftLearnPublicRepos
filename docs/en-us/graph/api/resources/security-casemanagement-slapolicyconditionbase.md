<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicyconditionbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# slaPolicyConditionBase resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base for objects in the **conditions** property of an [slaPolicyCriteriaBlock](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycriteriablock?view=graph-rest-beta).

This is an abstract complex type and can't be instantiated directly. It has no key or properties. Use one of the following derived types:

- [slaPolicyCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycondition?view=graph-rest-beta), which compares a case property with one or more values.
- [slaPolicyCriteriaBlock](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycriteriablock?view=graph-rest-beta), which combines conditions with a logical operator.

For request bodies, use `@odata.type` to specify the concrete condition type: `#microsoft.graph.security.caseManagement.slaPolicyCondition` for a leaf condition or `#microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock` for a group. The maximum nesting depth is two.

## Methods

None.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type. This abstract type can't be instantiated directly; use one of its derived types when supplying a condition object.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyConditionBase"
}
```
