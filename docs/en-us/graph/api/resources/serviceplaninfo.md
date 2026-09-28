<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceplaninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# servicePlanInfo resource type

Namespace: microsoft.graph

Contains information about a service plan associated with a subscribed SKU. The **servicePlans** property of the [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) entity is a collection of **servicePlanInfo**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesTo | String | The object the service plan can be assigned to. The possible values are:  <br>`User` - service plan can be assigned to individual users.  <br>`Company` - service plan can be assigned to the entire tenant. |
| provisioningStatus | String | The provisioning status of the service plan. The possible values are:  <br>`Success` - Service is fully provisioned.  <br>`Disabled` - Service is disabled.  <br>`Error` - The service plan isn't provisioned and is in an error state.  <br>`PendingInput` - The service isn't provisioned and is awaiting service confirmation.  <br>`PendingActivation` - The service is provisioned but requires explicit activation by an administrator \(for example, Intune\_O365 service plan\)  <br>`PendingProvisioning` - Microsoft has added a new service to the product SKU and it isn't activated in the tenant. |
| servicePlanId | Guid | The unique identifier of the service plan. |
| servicePlanName | String | The name of the service plan. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appliesTo": "String",
  "provisioningStatus": "String",
  "servicePlanId": "Guid",
  "servicePlanName": "String"
}
```
