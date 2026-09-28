<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagemention?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# chatMessageMention resource type

Namespace: microsoft.graph

Represents a mention in a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) entity. The mention can be to a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0), bot, [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), or [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

In a **chatMessage** object that contains one or more mentions, the message body **content** property represents the chat message in HTML. It encloses the **mentionText** of each mention in an HTML `at` element, with an `id` attribute that corresponds to the **id** property of the mention.

As an example, a chat message contains two mentions, with the mention text "Megan" and "Alex" respectively. Its body **content** property specifies `at` elements for the two mentions as follows:

```json
"body": {
    "contentType": "html",
    "content": "<div><div>Ah, <at id=\"0\">Megan</at>, <at id=\"1\">Alex</at>, I saw them in a separate folder. Thanks!</div>\n</div>"
}
```

In the **content** property, the first mention has an HTML `id` attribute of 0. This corresponds to the **id** property of that first instance of **chatMessageMention**, which is also 0.

The second mention has an `id` attribute of 1, matching the **id** property of the second instance, which is 1.

For a fuller context of the example, see [List channel message replies](https://learn.microsoft.com/en-us/graph/api/chatmessage-list-replies?view=graph-rest-1.0#example).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | Int32 | Index of an entity being mentioned in the specified **chatMessage**. Matches the {index} value in the corresponding `<at id="{index}">` tag in the message body. |
| mentioned | [chatMessageMentionedIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagementionedidentityset?view=graph-rest-1.0) | The entity \(user, application, team, channel, or chat\) that was @mentioned. |
| mentionText | string | String used to represent the mention. For example, a user's display name, a team name. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": 1024,
  "mentioned": {"@odata.type": "microsoft.graph.chatMessageMentionedIdentitySet"},
  "mentionText": "string"
 }
```
