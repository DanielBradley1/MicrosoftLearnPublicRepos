<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/distributionlistmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# distributionListMember resource type

Namespace: microsoft.graph

Represents an expanded member of a [personal distribution list](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0), with resolved contact information.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the member. Read-only. |
| id | String | The unique identifier for the distribution list member. It corresponds to the value supplied as **key** when you add a member via [addMembers](https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-1.0). Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| memberId | String | A system-generated unique identifier. Nonempty for `contact`, `privateDL`, and `mailbox` members. Read-only. |
| type | recipientType | The type of the recipient. The possible values are: `contact`, `oneOff`, `mailbox`, `privateDL`, `unknownFutureValue`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| contact | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | The contact associated with the distribution list member. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.distributionListMember",
  "id": "String (identifier)",
  "displayName": "String",
  "type": "String",
  "memberId": "String"
}
```
