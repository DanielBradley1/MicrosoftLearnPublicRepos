<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementunevaluatedservice -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementUnevaluatedService resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A service whose balance couldn't be evaluated for the user, reported instead of an unreliable [costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance) row.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `reason` | [balanceEvaluationFailureReason](#balanceevaluationfailurereason-enumeration) | Why the balance couldn't be evaluated. |
| `serviceId` | String | The service identifier whose balance couldn't be evaluated. |

### balanceEvaluationFailureReason enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `upstreamFailure` | The service couldn't resolve the spending policy, so no authoritative balance could be produced. |
| `noApplicablePolicy` | No spending policy governs this service for this user, so there's no balance to report. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUnevaluatedService",
  "reason": "String",
  "serviceId": "String"
}
```
