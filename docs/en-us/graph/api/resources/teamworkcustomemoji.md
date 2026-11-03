<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# teamworkCustomEmoji resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom emoji that was uploaded to the teamwork messaging of the organization. Custom emojis can be used in chat messages and channel messages.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-list-customemojis?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) collection | Get a list of [custom emojis](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) available in the teamwork messaging of the organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-post-customemojis?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) | Create a new [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) in the teamwork messaging of the organization, which adds the custom emoji to Teams for the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | String | The base64-encoded image content of the emoji. Supported formats include PNG and GIF. |
| createdBy | [customEmojiFromIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/customemojifromidentityset?view=graph-rest-beta) | Identity of the user who created the emoji. |
| createdDateTime | DateTimeOffset | The date and time when the emoji was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| displayName | String | The unique display name of the custom emoji. Key. Must be unique and must not conflict with existing emoji names. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.teamworkCustomEmoji",
    "displayName": "String (identifier)",
    "contentBytes": "String",
    "createdDateTime": "String (timestamp)",
    "createdBy": {
        "@odata.type": "microsoft.graph.customEmojiFromIdentitySet"
    }
}
```

## Related content

- [teamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-beta)
