<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# workloadStatus resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represent the status for a workload.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name for the workload. Required. Read-only. |
| offboardedDateTime | DateTimeOffset | The date and time the workload was offboarded. Optional. Read-only. |
| onboardedDateTime | DateTimeOffset | The date and time the workload was onboarded. Optional. Read-only. |
| onboardingStatus | workloadOnboardingStatus | The onboarding status for the workload. The possible values are: `notOnboarded`, `onboarded`, `unknownFutureValue`. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.workloadStatus",
  "onboardingStatus": "String",
  "onboardedDateTime": "String (timestamp)",
  "displayName": "String",
  "offboardedDateTime": "String (timestamp)"
}
```
