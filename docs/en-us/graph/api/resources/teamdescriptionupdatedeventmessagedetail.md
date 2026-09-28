<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamdescriptionupdatedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamDescriptionUpdatedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an updated [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) description. This message is generated when a **team's** description is updated.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| teamDescription | String | The updated description for the **team**. |
| teamId | String | Unique identifier of the **team**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamDescriptionUpdatedEventMessageDetail",
  "teamId": "String",
  "teamDescription": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an updated **team** description](https://learn.microsoft.com/en-us/graph/system-messages/#team-description-updated)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
