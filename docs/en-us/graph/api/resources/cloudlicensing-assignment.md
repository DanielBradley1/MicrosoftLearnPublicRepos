<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# assignment resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a license assignment that grants a license for the product-SKU contained within an allotment directly to the assigned user or device, or indirectly to each member of the assigned group. Each unique user or device consumes one license from each allotment to which they're directly or indirectly assigned.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-list-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) collection | Get a list of license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) objects within an organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection of an organization. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-get?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Read the properties and relationships of an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-update?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Update an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object to enable or disable services. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-delete?view=graph-rest-beta) | None | Delete an [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) object. |
| [Create for allotment](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection of an [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta). |
| [Create for user](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usercloudlicensing-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta)'s **assignments** collection. |
| [Create for group](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-groupcloudlicensing-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection for a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta). |
| [Create for device](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-devicecloudlicensing-post-assignments?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) | Create a new license [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) by posting to the **assignments** collection for a [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta). |
| [Reprocess assignments](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-reprocessassignments?view=graph-rest-beta) | None | Reprocess existing license [assignments](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) for a user by calling the **reprocessAssignments** action on a user's assignments. |
| [Get assignedTo](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-get-assignedto?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Get a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta), [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta), or [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) object for a given [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) to which licenses are assigned. |
| [Get allotment for assignment](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignment-get-allotment?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) | Get the [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) that is the source of the licenses used in the assignment. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledServicePlanIds | Guid collection | The list of disabled service plans for this **assignment**. Not nullable. |
| id | String | The unique identifier for the **assignment** that should be treated as an opaque identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Not nullable. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allotment | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) | The allotment from which licenses are assigned. Not nullable. |
| assignedTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user, group, or device to which licenses are assigned. Not nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
  "disabledServicePlanIds": ["Guid"],
  "id": "String (identifier)"
}
```
