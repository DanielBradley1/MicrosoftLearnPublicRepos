<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# post resource type

Namespace: microsoft.graph Represents an individual Post item within a [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) entity.

Even though you cannot explicitly create a post, doing any of the following would create a post:

- [Reply to an existing post](https://learn.microsoft.com/en-us/graph/api/post-reply?view=graph-rest-1.0)
- [Reply to an existing thread](https://learn.microsoft.com/en-us/graph/api/conversationthread-reply?view=graph-rest-1.0)
- [Create a thread in a new conversation](https://learn.microsoft.com/en-us/graph/api/group-post-threads?view=graph-rest-1.0)
- [Create a new conversation](https://learn.microsoft.com/en-us/graph/api/group-post-conversations?view=graph-rest-1.0)

This resource lets you add your own data to custom properties using [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List posts](https://learn.microsoft.com/en-us/graph/api/conversationthread-list-posts?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Get the posts of the specified thread. |
| [Get post](https://learn.microsoft.com/en-us/graph/api/post-get?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Get the properties and relationships of a post in a specified thread. |
| [Reply post](https://learn.microsoft.com/en-us/graph/api/post-reply?view=graph-rest-1.0) | None | Reply to a post and add a new post to the specified thread in a group conversation. |
| [Forward post](https://learn.microsoft.com/en-us/graph/api/post-forward?view=graph-rest-1.0) | None | Forward a post to a recipient. |
| **Attachments** |  |  |
| [List attachments](https://learn.microsoft.com/en-us/graph/api/post-list-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Get all attachments on a post. |
| [Add attachment](https://learn.microsoft.com/en-us/graph/api/post-post-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Add an attachment to a post. |
| **Open extensions** |  |  |
| [Create open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) | Create an open extension and add custom properties in a new or existing instance of a resource. |
| [Get open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-get?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) collection | Get an open extension object or objects identified by name or fully qualified name. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing post. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Get posts that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing post. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Get a post that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The contents of the post. This is a default property. This property can be null. |
| categories | String collection | The categories associated with the post. |
| changeKey | String | Identifies the version of the post. Every time the post is changed, ChangeKey changes as well. This allows Exchange to apply changes to the correct version of the object. |
| conversationId | String | Unique ID of the conversation. Read-only. |
| conversationThreadId | String | Unique ID of the conversation thread. Read-only. |
| createdDateTime | DateTimeOffset | Specifies when the post was created. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| from | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | Used in delegate access scenarios. Indicates who posted the message on behalf of another user. This is a default property. |
| hasAttachments | Boolean | Indicates whether the post has at least one attachment. This is a default property. |
| id | String | Read-only. |
| lastModifiedDateTime | DateTimeOffset | Specifies when the post was last modified. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| newParticipants | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | Conversation participants that were added to the thread as part of this post. |
| receivedDateTime | DateTimeOffset | Specifies when the post was received. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| sender | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | Contains the address of the sender. The value of Sender is assumed to be the address of the authenticated user in the case when Sender is not specified. This is a default property. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | [Attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Read-only. Nullable. Supports `$expand`. |
| extensions | [Extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the post. Read-only. Nullable. Supports `$expand`. |
| inReplyTo | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Read-only. Supports `$expand`. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the post. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the post. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "categories": ["string"],
  "changeKey": "string",
  "conversationId": "string",
  "conversationThreadId": "string",
  "createdDateTime": "String (timestamp)",
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "newParticipants": [{"@odata.type": "microsoft.graph.recipient"}],
  "receivedDateTime": "String (timestamp)",
  "sender": {"@odata.type": "microsoft.graph.recipient"}
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
