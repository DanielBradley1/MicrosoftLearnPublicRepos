<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# assignmentError resource type

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an error that impacts synchronization of license assignments in the directory. This error can prevent the license assignment from taking effect or from updating.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-admincloudlicensing-list-assignmenterrors?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) collection | Get a list of the [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) objects within an organization or affecting a specific user. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignmenterror-get?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) | Read the properties and relationships of an [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) object. |
| [Get assignedTo](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignmenterror-get-assignedto?view=graph-rest-beta) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | Get a [user](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) or [group](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) object for a given [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) to which licenses are assigned. |
| [Get usageRight](https://learn.microsoft.com/en-us/graph/api/cloudlicensing-assignmenterror-get-usageright?view=graph-rest-beta) | [microsoft.graph.cloudLicensing.usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) | Get a [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) object affected by an [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code associated with the assignment synchronization failure. |
| id | String | The unique identifier for the **assignmentError** that should be treated as an opaque identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Not nullable. Read-only. |
| message | String | The error message associated with the assignment synchronization failure. |
| occurrenceDateTime | DateTimeOffset | The date and time at which the error most recently occurred. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| skuId | Guid | Unique identifier \(GUID\) for the service SKU that is equal to the **skuId** property on the related [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-beta) object. Read-only. Supports `$filter`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignedTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The user to whom licenses are assigned. Not nullable. Read-only. |
| usageRight | [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) | The affected **usageRight**, if one exists. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudLicensing.assignmentError",
  "code": "String",
  "id": "String (identifier)",
  "message": "String",
  "occurrenceDateTime": "String (timestamp)",
  "skuId": "Guid"
}
```
