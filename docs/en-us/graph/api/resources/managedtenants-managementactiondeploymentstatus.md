<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactiondeploymentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# managementActionDeploymentStatus resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the deployment status for a given managed tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| managementActionId | String | The identifier for the management action. Required. Read-only. |
| managementTemplateId | String | The management template identifier that was used to generate the management action. Required. Read-only. |
| status | managementActionStatus | The status of the management action. The possible values are: `toAddress`, `completed`, `error`, `timeOut`, `inProgress`, `planned`, `resolvedBy3rdParty`, `resolvedThroughAlternateMitigation`, `riskAccepted`, `unknownFutureValue`. Required. |
| workloadActionDeploymentStatuses | [microsoft.graph.managedTenants.workloadActionDeploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadactiondeploymentstatus?view=graph-rest-beta) collection | The collection of workload action deployment statues for the given management action. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementActionDeploymentStatus",
  "managementTemplateId": "String",
  "managementActionId": "String",
  "status": "String",
  "workloadActionDeploymentStatuses": [
    {
      "@odata.type": "microsoft.graph.managedTenants.workloadActionDeploymentStatus"
    }
  ]
}
```
