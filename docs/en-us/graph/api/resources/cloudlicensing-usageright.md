<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# cloudLicensing usageRight resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a principal's right to use a particular set of services, as granted by the combination of their assigned licenses for the same [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List for group](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-groupcloudlicensing-list-usagerights?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) collection | Get a list of the [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects granted to a group. |
| [List for user](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usercloudlicensing-list-usagerights?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) collection | Get a list of the [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects granted to a user. |
| [List for device](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-devicecloudlicensing-list-usagerights?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) collection | Get a list of the [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) objects granted to a device. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usageright-get?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) | Get the properties and relationships of a [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta), or [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta). |
| [List assignments](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usageright-list-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | Get a list of the [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) objects which combine to form this [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **usageRight** that should be treated as an opaque identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Not nullable. Read-only. |
| services | [microsoft.graph.cloudLicensing.service](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-service?view=graph-rest-beta) collection | Information about the services associated with the **usageRight**. Not nullable. Read-only. Supports `$filter` on the **planId** property. |
| skuId | Guid | Unique identifier \(GUID\) for the service SKU that is equal to the **skuId** property on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-beta) object. Read-only. Supports `$filter`. |
| skuPartNumber | String | Unique SKU display name that is equal to the **skuPartNumber** on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-beta) object; for example, `AAD_Premium`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allotments | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) collection | The set of allotments associated with the assignments that combine to form this **usageRight**. |
| assignments | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | The set of assignments that combine to form this **usageRight**, including both direct assignments and assignments inherited through group membership. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.usageRight",
  "id": "String (identifier)",
  "services": [{"@odata.type": "microsoft.graph.cloudLicensing.service"}],
  "skuId": "Guid",
  "skuPartNumber": "String"
}
```
