<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-caseslapolicyentry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# caseSlaPolicyEntry resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single SLA \(service level agreement\) policy's denormalized status for a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). Returned as an entry in the **slaPolicies** collection on a case. This resource is entirely server-computed; the SLA policy engine assigns and maintains SLA policies independently of the case management API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| breachTargetDateTime | DateTimeOffset | The date and time the SLA policy is targeted to breach, if applicable. `null` when the policy is paused or completed. Computed by the service. |
| policyDisplayName | String | The display name of the SLA policy. Computed by the service. |
| policyId | String | The unique identifier of the SLA policy, assigned by the SLA policy engine. Computed by the service. |
| status | [microsoft.graph.security.caseManagement.caseSlaPolicyStatus](#caseslapolicystatus-values) | The current SLA status for this policy on this case. Computed by the service. |

### caseSlaPolicyStatus values

| Member | Description |
| :--- | :--- |
| active | The SLA policy is actively tracked and within its target. |
| atRisk | The SLA policy is at risk of breaching its target. |
| breached | The SLA policy has breached its target. |
| paused | Tracking for the SLA policy is paused. |
| completedMet | The SLA policy completed within its target. |
| completedBreached | The SLA policy completed after breaching its target. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.caseSlaPolicyEntry",
  "policyId": "String",
  "policyDisplayName": "String",
  "status": "String",
  "breachTargetDateTime": "DateTimeOffset"
}
```
