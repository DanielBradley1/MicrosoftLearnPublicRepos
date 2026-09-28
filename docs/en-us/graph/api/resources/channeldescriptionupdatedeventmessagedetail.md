<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channeldescriptionupdatedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# channelDescriptionUpdatedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an updated [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) description. This message is generated when a **channel's** description is updated.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| channelDescription | String | The updated description of the **channel**. |
| channelId | String | Unique identifier of the **channel**. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.channelDescriptionUpdatedEventMessageDetail",
  "channelDescription": "String",
  "channelId": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an updated **channel** description](https://learn.microsoft.com/en-us/graph/system-messages/#channel-description-updated)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
