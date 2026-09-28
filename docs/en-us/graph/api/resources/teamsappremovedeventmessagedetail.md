<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappremovedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamsAppRemovedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) removed. This message is generated when a **teamsApp** is removed from a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0), or a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| teamsAppDisplayName | String | Display name of the **teamsApp**. |
| teamsAppId | String | Unique identifier of the **teamsApp**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppRemovedEventMessageDetail",
  "teamsAppId": "String",
  "teamsAppDisplayName": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about **teamsApp** removed](https://learn.microsoft.com/en-us/graph/system-messages/#teams-app-removed)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
