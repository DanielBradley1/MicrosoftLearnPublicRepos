<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisionedplan?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# provisionedPlan resource type

Namespace: microsoft.graph

Used by the **provisionedPlans** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) entity and the [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilityStatus | String | Condition of the capability assignment. The possible values are `Enabled`, `Warning`, `Suspended`, `Deleted`, `LockedOut`. See [a detailed description of each value](https://learn.microsoft.com/en-us/graph/api/resources/assignedplan?view=graph-rest-1.0#capabilitystatus-values). |
| provisioningStatus | String | The possible values are:  <br>`Success` - Service is fully provisioned.  <br>`Disabled` - Service is disabled.  <br>`Error` - The service plan isn't provisioned and is in an error state.  <br>`PendingInput` - The service isn't provisioned and is awaiting service confirmation.  <br>`PendingActivation` - The service is provisioned but requires explicit activation by an administrator \(for example, Intune\_O365 service plan\)  <br>`PendingProvisioning` - Microsoft has added a new service to the product SKU and it isn't activated in the tenant. |
| service | String | The name of the service; for example, "AccessControlS2S". |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "capabilityStatus": "string",
  "provisioningStatus": "string",
  "service": "string"
}
```
