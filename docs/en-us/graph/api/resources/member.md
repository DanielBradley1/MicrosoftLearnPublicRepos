<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/member?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# member complex type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a member of a personal distribution list. Use this type when adding or removing members through the [addMembers](https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-beta) and [deleteMembers](https://learn.microsoft.com/en-us/graph/api/distributionlist-deletemembers?view=graph-rest-beta) actions.

Note

To identify a member, a client may supply `key`, `memberId`, or both.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the member. Optional. |
| key | String | The email address or routing key of the member. Optional. |
| memberId | String | A unique identifier system-generated for contact, privateDL, and mailbox members. Optional. |
| type | [recipientType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#recipienttype-values) | The type of the recipient. The possible values are: `contact`, `oneOff`, `mailbox`, `privateDL`, `unknownFutureValue`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.member",
  "displayName": "string",
  "key": "string",
  "type": "string",
  "memberId": "string"
}
```
