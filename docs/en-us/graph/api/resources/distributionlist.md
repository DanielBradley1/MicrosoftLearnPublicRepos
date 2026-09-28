<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# distributionList resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a personal distribution list in the user's mailbox. A distribution list enables users to group email recipients together so they can send a message to all members at once, without entering each address individually.

Inherits from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/user-list-distributionlists?view=graph-rest-beta) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) collection | Get a list of the [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) objects in the user's mailbox. |
| [Create](https://learn.microsoft.com/en-us/graph/api/user-post-distributionlists?view=graph-rest-beta) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) | Create a new [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) in the user's mailbox. |
| [Get](https://learn.microsoft.com/en-us/graph/api/distributionlist-get?view=graph-rest-beta) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) | Read the properties and relationships of a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/distributionlist-update?view=graph-rest-beta) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) | Update the properties of a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/distributionlist-delete?view=graph-rest-beta) | None | Delete a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) object. |
| [Add members](https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-beta) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) | Add members to a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta). |
| [Delete members](https://learn.microsoft.com/en-us/graph/api/distributionlist-deletemembers?view=graph-rest-beta) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta) | Remove members from a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | The categories associated with the distribution list. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-beta). |
| changeKey | String | Version identifier used for optimistic concurrency control via the `If-Match` header. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the distribution list was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-beta). |
| displayName | String | The display name of the distribution list. |
| id | String | The unique identifier for the distribution list. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the distribution list was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-beta). |
| notes | String | Notes about the distribution list. |
| personIdentifier | String | The unique identifier of the distribution list in the mailbox. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [distributionListMember](https://learn.microsoft.com/en-us/graph/api/resources/distributionlistmember?view=graph-rest-beta) collection | The members of the distribution list. Not returned by default; use `$expand=members` to include. Read-only. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-beta) collection | The collection of single-value extended properties defined for the distribution list. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.distributionList",
  "id": "string (identifier)",
  "createdDateTime": "string (timestamp)",
  "lastModifiedDateTime": "string (timestamp)",
  "changeKey": "string",
  "categories": [
    "string"
  ],
  "displayName": "string",
  "notes": "string",
  "personIdentifier": "string"
}
```
