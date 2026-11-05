<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# teamworkCustomEmoji resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom emoji that was uploaded to the teamwork messaging of the organization. Custom emojis can be used in chat messages and channel messages.

Inherits from [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-list-customemojis?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) collection | Get a list of [custom emojis](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) available in the teamwork messaging of the organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-post-customemojis?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) | Create a new [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) in the teamwork messaging of the organization, which adds the custom emoji to Teams for the tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-get?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) | Get a single [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) or the raw image content of a custom emoji by display name from the teamwork messaging of the organization. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/teamworkcustomemoji-delete?view=graph-rest-beta) | None | Delete a [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) by display name from the teamwork messaging of the organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Binary | The base64-encoded image content of the emoji. Supported formats include PNG and GIF. Inherited from [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-beta). |
| contentType | String | The media type of the custom emoji content, such as `image/png` or `image/gif`. Inherited from [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-beta). |
| createdBy | [customEmojiFromIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/customemojifromidentityset?view=graph-rest-beta) | Identity of the user who created the emoji. |
| createdDateTime | DateTimeOffset | The date and time when the emoji was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| displayName | String | The unique display name of the custom emoji. This property is an alternate key and must not conflict with existing emoji names. |
| id | String | The service-generated identifier of the custom emoji. Inherited from [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.teamworkCustomEmoji",
    "id": "String (identifier)",
    "contentBytes": "Binary",
    "contentType": "String",
    "displayName": "String",
    "createdDateTime": "String (timestamp)",
    "createdBy": {
        "@odata.type": "microsoft.graph.customEmojiFromIdentitySet"
    }
}
```

## Related content

- [teamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-beta)
