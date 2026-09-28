<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmembertransitiondetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-25 -->

# multiTenantOrganizationMemberTransitionDetails resource type

Namespace: microsoft.graph

Details of the processing status for a tenant in a multitenant organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| desiredRole | multiTenantOrganizationMemberRole | Role of the tenant in the multitenant organization. The possible values are: `owner`, `member`, `unknownFutureValue`. |
| desiredState | multiTenantOrganizationMemberState | State of the tenant in the multitenant organization currently being processed. The possible values are: `pending`, `active`, `removed`, `unknownFutureValue`. Read-only. |
| details | String | Details that explain the processing status if any. Read-only. |
| status | multiTenantOrganizationMemberProcessingStatus | Processing state of the asynchronous job. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantOrganizationMemberTransitionDetails",
  "desiredState": "String",
  "desiredRole": "String",
  "status": "String",
  "details": "String"
}
```
