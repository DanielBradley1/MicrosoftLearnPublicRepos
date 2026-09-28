<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamjoiningenabledeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamJoiningEnabledEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) joining enabled. This message is generated when joining is enabled for a **team**.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| teamId | String | Unique identifier of the **team**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamJoiningEnabledEventMessageDetail",
  "teamId": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about **team** joining enabled](https://learn.microsoft.com/en-us/graph/system-messages/#team-joining-enabled)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
