<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamrenamedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamRenamedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about a renamed [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). This message is generated when a **team's** name is updated.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| teamDisplayName | String | The updated name of the **team**. |
| teamId | String | Unique identifier of the **team**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamRenamedEventMessageDetail",
  "teamId": "String",
  "teamDisplayName": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about a renamed **team**](https://learn.microsoft.com/en-us/graph/system-messages/#team-renamed)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
