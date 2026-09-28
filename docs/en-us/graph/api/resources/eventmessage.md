<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-24 -->

# eventMessage resource type

Namespace: microsoft.graph

A message that represents a meeting request, cancellation, or response. The possible values are: `acceptance`, `tentative acceptance`, or `decline`.

The **eventMessage** entity is derived from [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0). **eventMessage** is the base type for [eventMessageRequest](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagerequest?view=graph-rest-1.0) and [eventMessageResponse](https://learn.microsoft.com/en-us/graph/api/resources/eventmessageresponse?view=graph-rest-1.0). The **meetingMessageType** property identifies the type of the event message.

When an organizer or app sends a meeting request, the meeting request arrives in an invitee's mailbox as an **eventMessage** instance with the **meetingMessageType** of **meetingRequest**. In addition, Outlook automatically creates an **event** instance in the invitee's calendar, with the **showAs** property as **tentative**.

To get the properties of the associated event in the invitee's mailbox, the app can use the **event** navigation property of the **eventMessage**, as shown in [get event message example](https://learn.microsoft.com/en-us/graph/api/eventmessage-get?view=graph-rest-1.0#example-2). The app can also respond to the event on behalf of the invitee programmatically, by [accepting](https://learn.microsoft.com/en-us/graph/api/event-accept?view=graph-rest-1.0), [tentatively accepting](https://learn.microsoft.com/en-us/graph/api/event-tentativelyaccept?view=graph-rest-1.0), or [declining](https://learn.microsoft.com/en-us/graph/api/event-decline?view=graph-rest-1.0) the event.

Aside from a meeting request, an **eventMessage** instance can be found in an invitee's mailbox as the result of an event organizer canceling a meeting, or in the organizer's mailbox as a result of an invitee responding to the meeting request. An app can act on event messages in the same way as on messages with minor differences.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/eventmessage-get?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Read properties and relationships of eventMessage object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/eventmessage-update?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Update eventMessage object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/message-delete?view=graph-rest-1.0) | None | Delete eventMessage object. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/eventmessage-permanentdelete?view=graph-rest-1.0) | None | Permanently delete an event message and place it in the purges folder in the recoverable Items folder in the user's mailbox. |
| [Copy message](https://learn.microsoft.com/en-us/graph/api/message-copy?view=graph-rest-1.0) | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Copy a message to a folder. |
| [Create draft to forward message](https://learn.microsoft.com/en-us/graph/api/message-createforward?view=graph-rest-1.0) | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Create a draft of the Forward message. You can then [update](https://learn.microsoft.com/en-us/graph/api/message-update?view=graph-rest-1.0) or [send](https://learn.microsoft.com/en-us/graph/api/message-send?view=graph-rest-1.0) the draft. |
| [Create draft to reply](https://learn.microsoft.com/en-us/graph/api/message-createreply?view=graph-rest-1.0) | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Create a draft of the Reply message. You can then [update](https://learn.microsoft.com/en-us/graph/api/message-update?view=graph-rest-1.0) or [send](https://learn.microsoft.com/en-us/graph/api/message-send?view=graph-rest-1.0) the draft. |
| [Create draft to reply-all](https://learn.microsoft.com/en-us/graph/api/message-createreplyall?view=graph-rest-1.0) | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Create a draft of the Reply All message. You can then [update](https://learn.microsoft.com/en-us/graph/api/message-update?view=graph-rest-1.0) or [send](https://learn.microsoft.com/en-us/graph/api/message-send?view=graph-rest-1.0) the draft. |
| [Forward message](https://learn.microsoft.com/en-us/graph/api/message-forward?view=graph-rest-1.0) | None | Forward a message. The message is then saved in the Sent Items folder. |
| [Move message](https://learn.microsoft.com/en-us/graph/api/message-move?view=graph-rest-1.0) | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Move a message to a folder. This creates a new copy of the message in the destination folder. |
| [Reply to a message](https://learn.microsoft.com/en-us/graph/api/message-reply?view=graph-rest-1.0) | None | Reply to the sender of a message. The message is then saved in the Sent Items folder. |
| [Reply-all to a message](https://learn.microsoft.com/en-us/graph/api/message-replyall?view=graph-rest-1.0) | None | Reply to all recipients of a message. The message is then saved in the Sent Items folder. |
| [Send draft message](https://learn.microsoft.com/en-us/graph/api/message-send?view=graph-rest-1.0) | None | Sends a previously created message draft. The message is then saved in the Sent Items folder. |
| **Attachments** |  |  |
| [List attachments](https://learn.microsoft.com/en-us/graph/api/eventmessage-list-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Get all attachments on an eventMessage. |
| [Add attachment](https://learn.microsoft.com/en-us/graph/api/eventmessage-post-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Add a new attachment to an eventMessage by posting to the attachments collection. |
| **Open extensions** |  |  |
| [Create open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-post-opentypeextension?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) | Create an open extension and add custom properties in a new or existing instance of a resource. |
| [Get open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-get?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) collection | Get an open extension object or objects identified by name or fully qualified name. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing eventMessage. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Get eventMessages that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing eventMessage. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Get an eventMessage that contains a multi-value extended property by using `$expand`. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bccRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The Bcc: recipients for the message. |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The body of the message. It can be in HTML or text format. |
| bodyPreview | String | The first 255 characters of the message body. It is in text format. |
| categories | String collection | The categories associated with the message. |
| ccRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The Cc: recipients for the message. |
| changeKey | String | The version of the message. |
| conversationId | String | The ID of the conversation the email belongs to. |
| conversationIndex | Edm.Binary | Indicates the position of the message within the conversation. |
| createdDateTime | DateTimeOffset | The date and time the message was created. |
| flag | [followupFlag](https://learn.microsoft.com/en-us/graph/api/resources/followupflag?view=graph-rest-1.0) | The flag value that indicates the status, start date, due date, or completion date for the message. |
| from | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | The owner of the mailbox from which the message is sent. In most cases, this value is the same as the **sender** property, except for sharing or delegation scenarios. The value must correspond to the actual mailbox used. Find out more about [setting the from and sender properties](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages#setting-the-from-and-sender-properties) of a message. |
| hasAttachments | Boolean | Indicates whether the message has attachments. |
| id | String | Unique identifier for the event message. By default, this value changes when the item is moved from one container \(such as a folder or calendar\) to another. To change this behavior, use the `Prefer: IdType="ImmutableId"` header. See [Get immutable identifiers for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-immutable-id) for more information. Read-only. |
| importance | String | The importance of the message: `low`, `normal`, `high`. |
| inferenceClassification | String | The possible values are: `focused`, and `other`. |
| internetMessageHeaders | [internetMessageHeader](https://learn.microsoft.com/en-us/graph/api/resources/internetmessageheader?view=graph-rest-1.0) collection | The collection of message headers, defined by [RFC5322](https://www.ietf.org/rfc/rfc5322.txt), that provide details of the network path taken by a message from the sender to the recipient. Read-only. |
| internetMessageId | String | The message ID in the format specified by [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). |
| isDelegated | Boolean | True if this meeting request is accessible to a delegate, false otherwise. The default is false. |
| isDeliveryReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| isDraft | Boolean | Indicates whether the message is a draft. A message is a draft if it isn't yet sent. |
| isRead | Boolean | Indicates whether the message is read. |
| isReadReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| lastModifiedDateTime | DateTimeOffset | The date and time the message was last changed. |
| meetingMessageType | meetingMessageType | The type of event message: `none`, `meetingRequest`, `meetingCancelled`, `meetingAccepted`, `meetingTenativelyAccepted`, `meetingDeclined`. |
| parentFolderId | String | The unique identifier for the message's parent mailFolder. |
| receivedDateTime | DateTimeOffset | The date and time the message was received. |
| replyTo | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The email addresses to use when replying. |
| sender | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | The account that is used to generate the message. In most cases, this value is the same as the **from** property. You can set this property to a different value when sending a message from a [shared mailbox](https://learn.microsoft.com/en-us/exchange/collaboration/shared-mailboxes/shared-mailboxes), [for a shared calendar, or as a delegate](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar). In any case, the value must correspond to the actual mailbox used. Find out more about [setting the from and sender properties](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages#setting-the-from-and-sender-properties) of a message. |
| sentDateTime | DateTimeOffset | The date and time the message was sent. |
| subject | String | The subject of the message. |
| toRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The To: recipients for the message. |
| uniqueBody | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The part of the body of the message that is unique to the current message. |
| webLink | String | The URL to open the message in Outlook on the web.  <br>  <br>You can append an `ispopout` argument to the end of the URL to change how the message is displayed. If `ispopout` isn't present or if it's set to 1, then the message is shown in a popout window. If `ispopout` is set to 0, then the browser shows the message in the Outlook on the web review pane.  <br>  <br>The message opens in the browser if you're logged in to your mailbox via Outlook on the web. You are prompted to sign in if you aren't already signed in with the browser.  <br>  <br>This URL can't be accessed from within an iFrame. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Read-only. Nullable. |
| event | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | The event associated with the event message. The assumption for attendees or room resources is that the Calendar Attendant is set to automatically update the calendar with an event when meeting request event messages arrive. Navigation property. Read-only. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the eventMessage. Read-only. Nullable. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the eventMessage. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the eventMessage. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "bccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "string",
  "categories": ["string"],
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "changeKey": "string",
  "conversationId": "string",
  "conversationIndex": "String (binary)",
  "createdDateTime": "DateTimeOffset",
  "event": { "@odata.type": "microsoft.graph.event" },
  "flag": {"@odata.type": "microsoft.graph.followupFlag"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
  "internetMessageHeaders": [{"@odata.type": "microsoft.graph.internetMessageHeader"}],
  "internetMessageId": "String",
  "isDelegated": true,
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "DateTimeOffset",
  "meetingMessageType": "String",
  "parentFolderId": "string",
  "receivedDateTime": "DateTimeOffset",
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "DateTimeOffset",
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "string"
}
```
