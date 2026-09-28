<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# assignedLicense resource type

Namespace: microsoft.graph

Represents a license assigned to a user or group. The **assignedLicenses** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) or [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) entitity is a collection of **assignedLicense** objects.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledPlans | Guid collection | A collection of the unique identifiers for plans that have been disabled. IDs are available in **servicePlans** > **servicePlanId** in the tenant's [subscribedSkus](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) or **serviceStatus** > **servicePlanId** in the tenant's [companySubscription](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0). |
| skuId | Guid | The unique identifier for the SKU. Corresponds to the **skuId** from [subscribedSkus](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) or [companySubscription](https://learn.microsoft.com/en-us/graph/api/resources/companysubscription?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "disabledPlans": ["Guid"],
  "skuId": "Guid"
}
```
