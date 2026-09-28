<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/licensedetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# licenseDetails resource type

Namespace: microsoft.graph

Contains information about a license assigned to a user.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List license details](https://learn.microsoft.com/en-us/graph/api/user-list-licensedetails?view=graph-rest-1.0) | [licenseDetails](https://learn.microsoft.com/en-us/graph/api/resources/licensedetails?view=graph-rest-1.0) collection | Retrieve a list of [licenseDetails](https://learn.microsoft.com/en-us/graph/api/resources/licensedetails?view=graph-rest-1.0) objects for a user. |
| [Get](https://learn.microsoft.com/en-us/graph/api/licensedetails-getteamslicensingdetails?view=graph-rest-1.0) | [teamsLicensingDetails](https://learn.microsoft.com/en-us/graph/api/resources/teamslicensingdetails?view=graph-rest-1.0) object | Get the Microsoft Teams license details for the specified user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the license detail object. Read-only. Key. Not nullable. |
| servicePlans | [servicePlanInfo](https://learn.microsoft.com/en-us/graph/api/resources/serviceplaninfo?view=graph-rest-1.0) collection | Information about the service plans assigned with the license. Read-only. Not nullable. |
| skuId | Guid | Unique identifier \(GUID\) for the service SKU. Equal to the **skuId** property on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) object. Read-only. |
| skuPartNumber | String | Unique SKU display name. Equal to the **skuPartNumber** on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) object; for example, `AAD_Premium`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "servicePlans": [{"@odata.type": "microsoft.graph.servicePlanInfo"}],
  "skuId": "Guid",
  "skuPartNumber": "String"
}
```
