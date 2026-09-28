<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channelsetasfavoritebydefaulteventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# channelSetAsFavoriteByDefaultEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) that the flag `isFavoriteByDefault` is set.

A **channel** is visible to all team members in the list of **channels** under a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) if the flag `isFavoriteByDefault` is `true`.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| channelId | String | Unique identifier of the **channel**. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.channelSetAsFavoriteByDefaultEventMessageDetail",
  "channelId": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about a **channel** set as favorite by default](https://learn.microsoft.com/en-us/graph/system-messages/#channel-set-as-favorite-by-default)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
