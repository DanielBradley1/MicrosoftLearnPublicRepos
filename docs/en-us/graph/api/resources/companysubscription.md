<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/companysubscription?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-24 -->

# companySubscription resource type

Namespace: microsoft.graph

Represents a commercial subscription for a tenant. Use the values of **skuId** and **serviceStatus** > **servicePlanId** to assign licenses to unassigned users and groups through the [user: assignLicense](https://learn.microsoft.com/en-us/graph/api/user-assignlicense?view=graph-rest-1.0) and [group: assignLicense](https://learn.microsoft.com/en-us/graph/api/group-assignlicense?view=graph-rest-1.0) APIs respectively.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/companysubscription-get?view=graph-rest-1.0) | [companySubscription](https://learn.microsoft.com/en-us/graph/api/resources/companysubscription?view=graph-rest-1.0) | Get a specific commercial subscription that an organization acquired. |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-subscriptions?view=graph-rest-1.0) | [companySubscription](https://learn.microsoft.com/en-us/graph/api/resources/companysubscription?view=graph-rest-1.0) collection | Get the list of commercial subscriptions that an organization acquired. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| commerceSubscriptionId | String | The ID of this subscription in the commerce system. Alternate key. |
| createdDateTime | DateTimeOffset | The date and time when this subscription was created. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique ID for this subscription. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isTrial | Boolean | Whether the subscription is a free trial or purchased. |
| nextLifecycleDateTime | DateTimeOffset | The date and time when the subscription will move to the next state \(as defined by the **status** property\) if not renewed by the tenant. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| ownerId | String | The object ID of the account admin. |
| ownerTenantId | String | The unique identifier for the Microsoft partner tenant that created the subscription on a customer tenant. |
| ownerType | String | Indicates the entity that **ownerId** belongs to, for example, "User". |
| serviceStatus | [servicePlanInfo](https://learn.microsoft.com/en-us/graph/api/resources/serviceplaninfo?view=graph-rest-1.0) collection | The provisioning status of each service included in this subscription. |
| skuId | String | The object ID of the SKU associated with this subscription. |
| skuPartNumber | String | The SKU associated with this subscription. |
| status | String | The status of this subscription. The possible values are: `Enabled`, `Deleted`, `Suspended`, `Warning`, `LockedOut`. |
| totalLicenses | Int32 | The number of licenses included in this subscription. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "commerceSubscriptionId": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isTrial": "Boolean",
  "nextLifecycleDateTime": "String (timestamp)",
  "ownerId": "String",
  "ownerTenantId": "String",
  "ownerType": "String",
  "serviceStatus": [{ "@odata.type": "microsoft.graph.servicePlanInfo" }],
  "skuId": "String",
  "skuPartNumber": "String",
  "status": "String",
  "totalLicenses": "Int32"
}
```
