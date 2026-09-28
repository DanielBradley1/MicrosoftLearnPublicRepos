<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# complianceChange resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a change to enforce policy such as approving content.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-list-compliancechanges?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowsupdates-compliancechange-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/windowsupdates-compliancechange-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) | Update the properties of a [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/windowsupdates-compliancechange-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when a compliance change was created. |
| id | String | The unique identifier for the compliance change. Returned by default. Not nullable. Read-only. |
| isRevoked | Boolean | `True` indicates that a compliance change is revoked, preventing further application. Revoking a compliance change is a final action. |
| revokedDateTime | DateTimeOffset | The date and time when the compliance change was revoked. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| updatePolicy | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) | The policy this compliance change is a member of. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.complianceChange",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isRevoked": "Boolean",
  "revokedDateTime": "String (timestamp)"
}
```
