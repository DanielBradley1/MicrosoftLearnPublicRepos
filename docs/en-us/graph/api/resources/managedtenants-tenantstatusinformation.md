<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantstatusinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-03 -->

# tenantStatusInformation resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents onboarding status information for a managed tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| delegatedPrivilegeStatus | delegatedPrivilegeStatus | The status of the delegated admin privilege relationship between the managing entity and the managed tenant. The possible values are: `none`, `delegatedAdminPrivileges`, `unknownFutureValue`, `granularDelegatedAdminPrivileges`, `delegatedAndGranularDelegetedAdminPrivileges`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `granularDelegatedAdminPrivileges` , `delegatedAndGranularDelegetedAdminPrivileges`. Optional. Read-only. |
| lastDelegatedPrivilegeRefreshDateTime | DateTimeOffset | The date and time the delegated admin privileges status was updated. Optional. Read-only. |
| offboardedByUserId | String | The identifier for the account that offboarded the managed tenant. Optional. Read-only. |
| offboardedDateTime | DateTimeOffset | The date and time when the managed tenant was offboarded. Optional. Read-only. |
| onboardedByUserId | String | The identifier for the account that onboarded the managed tenant. Optional. Read-only. |
| onboardedDateTime | DateTimeOffset | The date and time when the managed tenant was onboarded. Optional. Read-only. |
| onboardingStatus | tenantOnboardingStatus | The onboarding status for the managed tenant.. The possible values are: `ineligible`, `inProcess`, `active`, `inactive`, `unknownFutureValue`. Optional. Read-only. |
| tenantOnboardingEligibilityReason | tenantOnboardingEligibilityReason | Organization's onboarding eligibility reason in Microsoft 365 Lighthouse.. The possible values are: `none`, `contractType`, `delegatedAdminPrivileges`,`usersCount`,`license` and `unknownFutureValue`. Optional. Read-only. |
| workloadStatuses | [microsoft.graph.managedTenants.workloadStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadstatus?view=graph-rest-beta) collection | The collection of workload statues for the managed tenant. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantStatusInformation",
  "onboardingStatus": "String",
  "onboardedDateTime": "String (timestamp)",
  "onboardedByUserId": "String",
  "offboardedDateTime": "String (timestamp)",
  "offboardedByUserId": "String",
  "delegatedPrivilegeStatus": "String",
  "lastDelegatedPrivilegeRefreshDateTime": "String (timestamp)",
  "workloadStatuses": [
    {
      "@odata.type": "microsoft.graph.managedTenants.workloadStatus"
    }
  ]
}
```
