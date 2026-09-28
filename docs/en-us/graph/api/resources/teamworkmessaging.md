<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkmessaging?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# teamworkMessaging resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the messaging functionality available in Microsoft Teams teamwork within an organization. This resource provides access to custom emojis that can be used in chat and channel messages.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List customEmojis](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-list-customemojis?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) collection | Get a list of custom emojis available in the organization. |
| [Create teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/teamworkmessaging-post-customemojis?view=graph-rest-beta) | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) | Upload a new custom emoji to the organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customEmojis | [teamworkCustomEmoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) collection | The collection of custom emojis available in organization messaging. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.teamworkMessaging",
    "id": "String (identifier)"
}
```

## Related content

- [teamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-beta)
- [teamworkCustomEmoji resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta)
