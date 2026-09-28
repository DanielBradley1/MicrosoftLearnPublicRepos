<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadactiondeploymentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# workloadActionDeploymentStatus resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the deployment status for the workload action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionId | String | The unique identifier for the workload action. Required. Read-only. |
| deployedPolicyId | String | The identifier of any policy that was created by applying the workload action. Optional. Read-only. |
| error | [microsoft.graph.genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-beta) | The detailed information for exceptions that occur when deploying the workload action. Optional. Required. |
| lastDeploymentDateTime | DateTimeOffset | The date and time the workload action was last deployed. Optional. |
| status | workloadActionStatus | The status of the workload action deployment. The possible values are: `toAddress`, `completed`, `error`, `timeOut`, `inProgress`, `unknownFutureValue`. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.workloadActionDeploymentStatus",
  "actionId": "String",
  "status": "String",
  "error": {
    "@odata.type": "microsoft.graph.genericError"
  },
  "deployedPolicyId": "String",
  "lastDeploymentDateTime": "String (timestamp)"
}
```
