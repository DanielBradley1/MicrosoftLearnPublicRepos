<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# allotment resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an independently manageable pool of licenses supported by a subscription.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-list-allotments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) collection | Get a list of the [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-get?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) | Read the properties and relationships of an [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) object. |
| [List assignments for allotment](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-list-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | Get a list of license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) objects within an organization. |
| [Create assignment for allotment](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection of an organization. |
| [List waiting members](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-list-waitingmembers?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) collection | Get a list of over-assigned users who are in the waiting room for this allotment due to license capacity limits. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allottedUnits | Int32 | The number of licenses contained within the allotment. Not nullable. Read-only. |
| assignableTo | [microsoft.graph.cloudLicensing.assigneeTypes](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-service?view=graph-rest-beta#assigneetypes-values) | Identifies the types of directory objects to which the allotment can be assigned. The possible values are: `none`, `user`, `group`, `device`, `unknownFutureValue`. The **assigneeTypes** enum is multivalued and can contain multiple values in a comma‑separated list. Not nullable. Read-only. |
| consumedUnits | Int32 | The number of licenses that are currently consumed by assignments from this allotment. Not nullable. Read-only. |
| id | String | The unique identifier for the **allotment** that should be treated as an opaque identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Not nullable. Read-only. |
| services | [microsoft.graph.cloudLicensing.service](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-service?view=graph-rest-beta) collection | The list of services that might be enabled or disabled for assignments from this allotment. Not nullable. Read-only. |
| skuId | Guid | Unique identifier \(GUID\) for the service SKU that is equal to the **skuId** property on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-beta) object. Read-only. Supports `$filter`. |
| skuPartNumber | String | Unique SKU display name that is equal to the **skuPartNumber** on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-beta) object; for example, `AAD_Premium`. Read-only. |
| subscriptions | [microsoft.graph.cloudLicensing.subscription](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-subscription?view=graph-rest-beta) collection | Basic information about the subscriptions that supports this allotment. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | The list of license assignments that consume licenses from this allotment. Not nullable. |
| waitingMembers | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) collection | List of over-assigned users who are in the waiting room for an allotment due to license capacity limits. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
  "allottedUnits": "Int32",
  "assignableTo": "String",
  "consumedUnits": "Int32",
  "id": "String (identifier)",
  "services": [{"@odata.type": "microsoft.graph.cloudLicensing.service"}],
  "skuId": "Guid",
  "skuPartNumber": "String",
  "subscriptions": [{"@odata.type": "microsoft.graph.cloudLicensing.subscription"}]
}
```
