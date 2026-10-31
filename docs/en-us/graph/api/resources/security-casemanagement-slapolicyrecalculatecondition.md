<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicyrecalculatecondition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# slaPolicyRecalculateCondition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents elapsed-time reset settings in the **recalculateCondition** property of an [slaPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicydefinition?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| shouldResetTime | Boolean | Whether elapsed time resets when the policy is recalculated, for example, when a case reenters its scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyRecalculateCondition",
  "shouldResetTime": "Boolean"
}
```
