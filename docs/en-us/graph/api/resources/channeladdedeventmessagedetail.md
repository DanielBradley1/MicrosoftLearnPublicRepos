<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channeladdedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# channelAddedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) added to a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). This message is generated when a standard **channel** is added to a **team**.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| channelDisplayName | String | Display name of the **channel**. |
| channelId | String | Unique identifier of the **channel**. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.channelAddedEventMessageDetail",
  "channelDisplayName": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "channelId": "String"
}
```

## Related content

- [Example response for an event message about a **channel** added to a **team**](https://learn.microsoft.com/en-us/graph/system-messages/#channel-added)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
