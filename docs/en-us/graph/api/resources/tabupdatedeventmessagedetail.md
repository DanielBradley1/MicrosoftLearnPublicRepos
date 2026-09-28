<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tabupdatedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# tabUpdatedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an updated tab. This message is generated when a tab is updated in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| tabId | String | Unique identifier of the tab. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tabUpdatedEventMessageDetail",
  "tabId": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an updated tab](https://learn.microsoft.com/en-us/graph/system-messages/#tab-updated)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
