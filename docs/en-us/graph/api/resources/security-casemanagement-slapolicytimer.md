<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicytimer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# slaPolicyTimer resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an embedded warning and breach timer in the **timers** property of an [slaPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicydefinition?view=graph-rest-beta).

Timers are evaluated in **order**, lowest first. The first timer whose **filters** match applies; otherwise, the default timer applies. Each policy supports up to 15 timers and must have exactly one timer with **isDefault** set to `true`.

Timers don't have independent GET, POST, PATCH, or DELETE endpoints. Read them through the parent policy and replace the entire **timers** collection when updating it.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| breachThresholdInMinutes | Int32 | The elapsed time in minutes after which the timer is considered breached. Required when supplying a timer. |
| filters | [microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicycriteriablock?view=graph-rest-beta) | The condition that a case must match for this timer to apply. Required when **isDefault** is `false`. Omit this property for the default timer. |
| isDefault | Boolean | Whether this timer is the fallback when no other timer's **filters** match. Required when supplying a timer. Exactly one timer per policy must have a value of `true`. |
| order | Int32 | The evaluation order among the policy's timers, lowest first. Required when supplying a timer. |
| policyTimerId | String | The server-generated identifier for the timer. Computed on creation and immutable thereafter. Read-only. Omit this property from request bodies. |
| warningThresholdInMinutes | Int32 | The elapsed time in minutes after which an early warning is raised. |

## Relationships

None.

## JSON representation

For request bodies, set `@odata.type` on the **filters** criteria block when you supply it. Service responses can omit `@odata.type` on **slaPolicyTimer** objects and their nested **filters** object.

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyTimer",
  "policyTimerId": "String",
  "order": "Int32",
  "filters": {
    "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock"
  },
  "isDefault": "Boolean",
  "warningThresholdInMinutes": "Int32",
  "breachThresholdInMinutes": "Int32"
}
```
