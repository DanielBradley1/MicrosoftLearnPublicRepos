<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# distributionList resource type

Namespace: microsoft.graph

Represents a personal distribution list in the user's mailbox. A distribution list enables users to group email recipients together so they can send a message to all members at once, without entering each address individually.

Inherits from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/user-list-distributionlists?view=graph-rest-1.0) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) collection | Get a list of the [personal distribution lists](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) in the user's mailbox. |
| [Create](https://learn.microsoft.com/en-us/graph/api/user-post-distributionlists?view=graph-rest-1.0) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) | Create a new [personal distribution list](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) in the user's mailbox. |
| [Get](https://learn.microsoft.com/en-us/graph/api/distributionlist-get?view=graph-rest-1.0) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) | Read the properties and relationships of a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/distributionlist-update?view=graph-rest-1.0) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) | Update the properties of a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/distributionlist-delete?view=graph-rest-1.0) | None | Delete a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) object. |
| [Add members](https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-1.0) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) | Add members to a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0). |
| [Delete members](https://learn.microsoft.com/en-us/graph/api/distributionlist-deletemembers?view=graph-rest-1.0) | [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0) | Remove members from a [distributionList](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| categories | String collection | The categories associated with the distribution list. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| changeKey | String | Version identifier used for optimistic concurrency control via the `If-Match` header. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the distribution list was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| displayName | String | The display name of the distribution list. |
| id | String | The unique identifier for the distribution list. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the distribution list was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| notes | String | Notes about the distribution list. |
| personId | String | The unique identifier of the distribution list in the mailbox. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [distributionListMember](https://learn.microsoft.com/en-us/graph/api/resources/distributionlistmember?view=graph-rest-1.0) collection | The members of the distribution list. Not returned by default; use `$expand=members` to include. Read-only. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the distribution list. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.distributionList",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "changeKey": "String",
  "categories": [
    "String"
  ],
  "displayName": "String",
  "notes": "String",
  "personId": "String"
}
```
