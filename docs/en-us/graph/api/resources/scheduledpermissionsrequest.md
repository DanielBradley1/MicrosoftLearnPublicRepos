<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# scheduledPermissionsRequest resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a request for permissions on resources in a target authorization system that an identity makes through Microsoft Entra Permissions Management, either directly or indirectly. An authorized administrator can grant, reject, or cancel the request.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/permissionsmanagement-post-scheduledpermissionsrequests?view=graph-rest-beta) | [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta) | Create a new [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta) object. |
| [Cancel all](https://learn.microsoft.com/en-us/graph/api/scheduledpermissionsrequest-cancelall?view=graph-rest-beta) | None | Cancels a [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the identity created the request. |
| id | String | Unique identifier for the permissions request within Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| justification | String | The identity's justification for the request. |
| notes | String | Additional context for the permissions request. |
| requestedPermissions | [permissionsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinition?view=graph-rest-beta) | The permissions requested. |
| scheduleInfo | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-beta) | When to assign the requested permissions. |
| statusDetail | statusDetail | The current status of the request. The possible values are: `submitted`, `approved`, `completed`, `canceled`, `rejected`, `unknownFutureValue`. |
| ticketInfo | [ticketInfo](https://learn.microsoft.com/en-us/graph/api/resources/ticketinfo?view=graph-rest-beta) | Ticketing-related metadata that you can use to correlate to the request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.scheduledPermissionsRequest",
  "id": "String (identifier)",
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.permissionsDefinition"
  },
  "notes": "String",
  "justification": "String",
  "createdDateTime": "String (timestamp)",
  "scheduleInfo": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "ticketInfo": {
    "@odata.type": "microsoft.graph.ticketInfo"
  },
  "statusDetail": "String"
}
```
