<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/member?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# member complex type

Namespace: microsoft.graph

Represents a member of a [personal distribution list](https://learn.microsoft.com/en-us/graph/api/resources/distributionlist?view=graph-rest-1.0), identified by routing key and recipient type. Use this type when you add or remove members through the [addMembers](https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-1.0) and [deleteMembers](https://learn.microsoft.com/en-us/graph/api/distributionlist-deletemembers?view=graph-rest-1.0) actions.

Note

To identify a member, a client can supply **key**, **memberId**, or both.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the member. Optional. |
| key | String | The email address or routing key of the member. Optional. |
| memberId | String | A system-generated unique identifier for `contact`, `privateDL`, and `mailbox` members. Optional. |
| type | recipientType | The type of the recipient. The possible values are: `contact`, `oneOff`, `mailbox`, `privateDL`, `unknownFutureValue`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.member",
  "displayName": "String",
  "key": "String",
  "type": "String",
  "memberId": "String"
}
```
