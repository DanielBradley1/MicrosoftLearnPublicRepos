<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsrequestchange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsRequestChange resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a change event relating to requests for permissions by identities.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/permissionsmanagement-list-permissionsrequestchanges?view=graph-rest-beta) | [permissionsRequestChange](https://learn.microsoft.com/en-us/graph/api/resources/permissionsrequestchange?view=graph-rest-beta) collection | Get a list of the [permissionsRequestChange](https://learn.microsoft.com/en-us/graph/api/resources/permissionsrequestchange?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/permissionsrequestchange-get?view=graph-rest-beta) | [permissionsRequestChange](https://learn.microsoft.com/en-us/graph/api/resources/permissionsrequestchange?view=graph-rest-beta) | Read the properties and relationships of a [permissionsRequestChange](https://learn.microsoft.com/en-us/graph/api/resources/permissionsrequestchange?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeOccurrenceStatus | permissionsRequestOccurrenceStatus | The status of the active occurence of the schedule if one exists. The possible values are: `grantingFailed`, `granted`, `granting`, `revoked`, `revoking`, `revokingFailed`, `unknownFutureValue`. |
| id | String | Unique ID of the permissions request change event within Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| modificationDateTime | DateTimeOffset | Time when the change occurred. |
| permissionsRequestId | String | The ID of the **scheduledPermissionsRequest** object. |
| statusDetail | statusDetail | The current status of the request. The possible values are: `submitted`, `approved`, `completed`, `canceled`, `rejected`, `unknownFutureValue`. |
| ticketId | String | Represents the ticketing system identifier. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsRequestChange",
  "id": "String (identifier)",
  "modificationDateTime": "String (timestamp)",
  "statusDetail": "String",
  "activeOccurrenceStatus": "String",
  "ticketId": "String",
  "permissionsRequestId": "String"
}
```
