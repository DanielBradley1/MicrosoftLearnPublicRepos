<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/distributionlistmember?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# distributionListMember resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an expanded member of a personal distribution list.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the member. Read-only. |
| id | String | The unique identifier for the distribution list member. It corresponds to the value supplied as 'key' when adding a member via [addMembers](https://learn.microsoft.com/en-us/graph/api/distributionlist-addmembers?view=graph-rest-beta). Read-only. |
| memberId | String | A system generated unique identifier. Non-empty for contact, privateDL and mailbox members. ReadOnly. |
| type | [recipientType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#recipienttype-values) | The type of the recipient. The possible values are: `contact`, `oneOff`, `mailbox`, `privateDL`, `unknownFutureValue`. ReadOnly |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| contact | [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-beta) | The contact associated with the distribution list member. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.distributionListMember",
  "id": "string (identifier)",
  "displayName": "string",
  "type": "string",
  "memberId": "string"
}
```
