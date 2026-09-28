<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# waitingMember resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user or device that was added to the waiting room for an allotment due to license capacity limits.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List for allotment](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-allotment-list-waitingmembers?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) collection | Get a list of over-assigned [users](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) who are in the waiting room due to license capacity limits. |
| [List for user](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usercloudlicensing-list-waitingmembers?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) collection | Get a list of the [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) objects granted to a user. |
| [List for device](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-devicecloudlicensing-list-waitingmembers?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) collection | Get a list of the [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) objects for a device. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-waitingmember-get?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) | Read the properties and relationships of [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **waitingMember** that should be treated as an opaque identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Not nullable. Read-only. |
| waitingSinceDateTime | DateTimeOffset | Indicates the moment when the user or device first waited for this license. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allotment | [microsoft.graph.cloudLicensing.allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) | The allotment from which licenses are assigned. Not nullable. |
| assignedTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user or device to which licenses are assigned. Not nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
  "id": "String (identifier)",
  "waitingSinceDateTime": "String (timestamp)"
}
```
