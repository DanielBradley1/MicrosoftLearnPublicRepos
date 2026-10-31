<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseoperationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# cloudPcManagedLicenseOperationResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the outcome of a Cloud PC managed-license operation for an individual user. This complex type is returned in the **results** property of [cloudPcManagedLicenseExtendAccess](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| entraUserId | String | The Microsoft Entra user object identifier to which the result applies that matches one of the values supplied in **entraUserIds** when the operation was submitted. This value isn't a user principal name or an entity key. Results are returned inline as part of the operation and can't be retrieved individually. Read-only. Not nullable. |
| failureCode | [cloudPcManagedLicenseOperationFailureCode](#cloudpcmanagedlicenseoperationfailurecode-values) | The reason the operation failed for this user. Returned only when **operationResultStatus** is `failed`. The possible values are: `internalServiceError`, `noActiveProvisioningPolicyAssignment`, `userLicenseAssignmentNotEnabled`, `maximumAccessDurationExceeded`, `sufficientAccessTimeRemaining`, `noEligibleLicenseAvailable`, `unknownFutureValue`. Read-only. Nullable. |
| operationResultStatus | [cloudPcManagedLicenseOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta#cloudpcmanagedlicenseoperationstatus-values) | The outcome for the individual user. Per-user results are returned only after the operation reaches a terminal status and use `succeeded` or `failed`. The `inProgress` and `partiallySucceeded` values aren't used for per-user results. The `unknownFutureValue` value is reserved for future enum members. Read-only. Not nullable. |

### cloudPcManagedLicenseOperationFailureCode values

| Member | Description |
| :--- | :--- |
| internalServiceError | Default. The operation can't be completed because of an internal service error. Retry the operation later for the affected user. |
| noActiveProvisioningPolicyAssignment | The user doesn't have an active provisioning policy assignment for the specified service plan. |
| userLicenseAssignmentNotEnabled | The user's license assignment isn't enabled. |
| maximumAccessDurationExceeded | Extending the user's access causes their total access duration to exceed the maximum of 30 days. |
| sufficientAccessTimeRemaining | The user's remaining access time already covers the rest of the current license cycle, so no extension is needed. |
| noEligibleLicenseAvailable | No Windows 365 Reserve license is available from subscriptions in the tenant for the user. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcManagedLicenseOperationResult",
  "entraUserId": "String",
  "failureCode": "String",
  "operationResultStatus": "String"
}
```
