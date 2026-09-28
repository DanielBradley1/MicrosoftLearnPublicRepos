<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/channelsharingupdatedeventmessagedetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# channelSharingUpdatedEventMessageDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of an event message about sharing a channel. This message is generated when a channel with a **membershipType** of `shared` is shared.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Initiator of the event. |
| ownerTeamId | String | The ID of the team to which the shared channel belongs. |
| ownerTenantId | String | The ID of the tenant to which the shared channel belongs. |
| sharedChannelId | String | The ID of the shared channel. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.channelSharingUpdatedEventMessageDetail",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "ownerTeamId": "String",
  "ownerTenantId": "String",
  "sharedChannelId": "String"
}
```

## Related content

- [Response example for an event message about a shared channel](https://learn.microsoft.com/en-us/graph/system-messages/#channel-shared)
- [System messages](https://learn.microsoft.com/en-us/graph/system-messages)
