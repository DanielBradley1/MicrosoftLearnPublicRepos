<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailtips?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mailTips resource type

Namespace: microsoft.graph

Informative messages about a recipient, that are displayed to users while they're composing a message. For example, an out-of-office message as an automatic reply for a message recipient.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| automaticReplies | [automaticRepliesMailTips](https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliesmailtips?view=graph-rest-1.0) | Mail tips for automatic reply if it has been set up by the recipient. |
| customMailTip | String | A custom mail tip that can be set on the recipient's mailbox. |
| deliveryRestricted | Boolean | Whether the recipient's mailbox is restricted, for example, accepting messages from only a predefined list of senders, rejecting messages from a predefined list of senders, or accepting messages from only authenticated senders. |
| emailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | The email address of the recipient to get mailtips for. |
| error | [mailTipsError](https://learn.microsoft.com/en-us/graph/api/resources/mailtipserror?view=graph-rest-1.0) | Errors that occur during the [getMailTips](https://learn.microsoft.com/en-us/graph/api/user-getmailtips?view=graph-rest-1.0) action. |
| externalMemberCount | Int32 | The number of external members if the recipient is a distribution list. |
| isModerated | Boolean | Whether sending messages to the recipient requires approval. For example, if the recipient is a large distribution list and a moderator has been set up to approve messages sent to that distribution list, or if sending messages to a recipient requires approval of the recipient's manager. |
| mailboxFull | Boolean | The mailbox full status of the recipient. |
| maxMessageSize | Int32 | The maximum message size that has been configured for the recipient's organization or mailbox. |
| recipientScope | recipientScopeType | The scope of the recipient. The possible values are: `none`, `internal`, `external`, `externalPartner`, `externalNonParther`. For example, an administrator can set another organization to be its "partner". The scope is useful if an administrator wants certain mailtips to be accessible to certain scopes. It's also useful to senders to inform them that their message may leave the organization, helping them make the correct decisions about wording, tone and content. |
| recipientSuggestions | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | Recipients suggested based on previous contexts where they appear in the same message. |
| totalMemberCount | Int32 | The number of members if the recipient is a distribution list. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "automaticReplies": {"@odata.type": "microsoft.graph.automaticRepliesMailTips"},
  "customMailTip": "string",
  "deliveryRestricted": "boolean",
  "emailAddress": {"@odata.type": "microsoft.graph.emailAddress"},
  "error": {"@odata.type": "microsoft.graph.mailTipsError"},
  "externalMemberCount": 1024,
  "isModerated": "boolean",
  "mailboxFull": "boolean",
  "maxMessageSize": 1024,
  "recipientScope": "string",
  "recipientSuggestions": [{"@odata.type": "microsoft.graph.recipient"}],
  "totalMemberCount": 1024
}
```
