<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/eventmessagerequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-24 -->

# eventMessageRequest resource type

Namespace: microsoft.graph

A message that represents a meeting request in an invitee's mailbox.

The **eventMessageRequest** entity is derived from [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0).

To respond to the meeting request, first, use the **event** navigation property to access the corresponding event, as shown in this [example](https://learn.microsoft.com/en-us/graph/api/eventmessage-get?view=graph-rest-1.0#example-2). Then [accept](https://learn.microsoft.com/en-us/graph/api/event-accept?view=graph-rest-1.0), [tentativelyAccept](https://learn.microsoft.com/en-us/graph/api/event-tentativelyaccept?view=graph-rest-1.0), or [decline](https://learn.microsoft.com/en-us/graph/api/event-decline?view=graph-rest-1.0) that event associated with the **eventMessageRequest**.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowNewTimeProposals": "Boolean",
  "bccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "string",
  "categories": ["string"],
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "changeKey": "string",
  "conversationId": "string",
  "conversationIndex": "String (binary)",
  "createdDateTime": "String (timestamp)",
  "endDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "string (identifier)",
  "importance": "String",
  "inferenceClassification": "String",
  "isDelegated": true,
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isOutOfDate": "Boolean",
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "meetingMessageType": "microsoft.graph.meetingMessageType",
  "parentFolderId": "string",
  "previousEndDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "previousLocation": {"@odata.type": "microsoft.graph.location"},
  "previousStartDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "receivedDateTime": "String (timestamp)",
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "responseRequested": "Boolean",
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "subject": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "type": "string",
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowNewTimeProposals | Boolean | `True` if the meeting organizer allows invitees to propose a new time when responding, `false` otherwise. Optional. Default is `true`. |
| bccRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The Bcc: recipients for the message. |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The body of the message. |
| bodyPreview | String | The first 255 characters of the message body. |
| categories | String collection | The categories associated with the message. |
| ccRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The Cc: recipients for the message. |
| changeKey | String | The version of the message. |
| conversationId | String | The ID of the conversation the email belongs to. |
| conversationIndex | Edm.Binary | The index of the conversation the email belongs to. |
| createdDateTime | DateTimeOffset | The date and time the message was created. |
| endDateTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The end time of the requested meeting. |
| from | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | The owner of the mailbox from which the message is sent. In most cases, this value is the same as the **sender** property, except for sharing or delegation scenarios. The value must correspond to the actual mailbox used. Find out more about [setting the from and sender properties](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages#setting-the-from-and-sender-properties) of a message. |
| hasAttachments | Boolean | Indicates whether the message has attachments. |
| id | String | Read-only. |
| importance | String | The importance of the message: `Low`, `Normal`, `High`. |
| inferenceClassification | String | The possible values are: `Focused`, `Other`. |
| isDelegated | Boolean | True if this meeting request response is accessible to a delegate, false otherwise. Default is false. |
| isDeliveryReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| isDraft | Boolean | Indicates whether the message is a draft. A message is a draft if it hasn't been sent yet. |
| isOutOfDate | Boolean | Indicates whether this meeting request has been made out-of-date by a more recent request. |
| isRead | Boolean | Indicates whether the message has been read. |
| isReadReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| lastModifiedDateTime | DateTimeOffset | The date and time the message was last changed. |
| location | [Location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The location of the requested meeting. |
| meetingMessageType | String | The type of event message: `none`, `meetingRequest`, `meetingCancelled`, `meetingAccepted`, `meetingTentativelyAccepted`, `meetingDeclined`. |
| parentFolderId | String | The unique identifier for the message's parent mailFolder. |
| previousEndDateTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | If the meeting update changes the meeting end time, this property specifies the previous meeting end time. |
| previousLocation | [Location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | If the meeting update changes the meeting location, this property specifies the previous meeting location. |
| previousStartDateTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | If the meeting update changes the meeting start time, this property specifies the previous meeting start time. |
| receivedDateTime | DateTimeOffset | The date and time the message was received. |
| recurrence | [PatternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurrence pattern of the requested meeting. |
| replyTo | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The email addresses to use when replying. |
| responseRequested | Boolean | Set to true if the sender would like the invitee to send a response to the requested meeting. |
| sender | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | The account that is actually used to generate the message. In most cases, this value is the same as the **from** property. You can set this property to a different value when sending a message from a [shared mailbox](https://learn.microsoft.com/en-us/exchange/collaboration/shared-mailboxes/shared-mailboxes), [for a shared calendar, or as a delegate](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar). In any case, the value must correspond to the actual mailbox used. Find out more about [setting the from and sender properties](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages#setting-the-from-and-sender-properties) of a message. |
| sentDateTime | DateTimeOffset | The date and time the message was sent. |
| startDateTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The start time of the requested meeting. |
| subject | String | The subject of the message. |
| toRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The To: recipients for the message. |
| type | String | The type of requested meeting: `singleInstance`, `occurence`, `exception`, `seriesMaster`. |
| uniqueBody | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The part of the body of the message that is unique to the current message. |
| webLink | String | The URL to open the message in Outlook on the web.  <br>  <br>You can append an ispopout argument to the end of the URL to change how the message is displayed. If ispopout is not present or if it is set to 1, then the message is shown in a popout window. If ispopout is set to 0, then the browser will show the message in the Outlook on the web review pane.  <br>  <br>The message will open in the browser if you are logged in to your mailbox via Outlook on the web. You will be prompted to login if you are not already logged in with the browser.  <br>  <br>This URL cannot be accessed from within an iFrame. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | The collection of [fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0), [itemAttachment](https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-1.0), and [referenceAttachment](https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-1.0) attachments for the message. Read-only. Nullable. |
| event | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | The event associated with the event message. The assumption for attendees or room resources is that the Calendar Attendant is set to automatically update the calendar with an event when meeting request event messages arrive. Navigation property. Read-only. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the eventMessage. Read-only. Nullable. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the eventMessage. Read-only. Nullable. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the eventMessage. Read-only. Nullable. |

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get event message](https://learn.microsoft.com/en-us/graph/api/eventmessage-get?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Read properties and relationships of eventMessage object. |
| [Update event message](https://learn.microsoft.com/en-us/graph/api/eventmessage-update?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Update eventMessage object. |
| [Delete event message](https://learn.microsoft.com/en-us/graph/api/eventmessage-delete?view=graph-rest-1.0) | None | Delete eventMessage object. |
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
| [Get open extension](https://learn.microsoft.com/en-us/graph/api/opentypeextension-get?view=graph-rest-1.0) | [openTypeExtension](https://learn.microsoft.com/en-us/graph/api/resources/opentypeextension?view=graph-rest-1.0) collection | Get an open extension identified by name. |
| **Extended properties** |  |  |
| [Create single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Create one or more single-value extended properties in a new or existing eventMessage. |
| [Get single-value property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Get eventMessages that contain a single-value extended property by using `$expand` or `$filter`. |
| [Create multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Create one or more multi-value extended properties in a new or existing eventMessage. |
| [Get multi-value property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0) | [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0) | Get an eventMessage that contains a multi-value extended property by using `$expand`. |
