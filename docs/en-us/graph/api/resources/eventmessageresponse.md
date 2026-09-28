<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/eventmessageresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# eventMessageResponse resource type

Namespace: microsoft.graph

A message that represents a response to a meeting request in the meeting organizer's mailbox.

Derived from [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage?view=graph-rest-1.0).

An organizer who receives an **eventMessageResponse** with the **responseType** set to `tentativelyAccepted` or `declined`, and that includes a **proposedNewTime** property, can choose to accept the proposal. To do so, first, use the **event** navigation property of the **eventMessageResponse** to access the corresponding event, as shown in this [example](https://learn.microsoft.com/en-us/graph/api/eventmessage-get?view=graph-rest-1.0#example-2). Then [update](https://learn.microsoft.com/en-us/graph/api/event-update?view=graph-rest-1.0) the associated event to the proposed time.

For more information on how to propose a time, and how to receive and accept a new time proposal, see [Propose new meeting times](https://learn.microsoft.com/en-us/graph/outlook-calendar-meeting-proposals).

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
| conversationIndex | Edm.Binary | The Index of the conversation the email belongs to. |
| createdDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| endDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The end time of the requested meeting. |
| flag | [followupFlag](https://learn.microsoft.com/en-us/graph/api/resources/followupflag?view=graph-rest-1.0) | The flag value that indicates the status, start date, due date, or completion date for the message. |
| from | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | The owner of the mailbox from which the message is sent. In most cases, this value is the same as the **sender** property, except for sharing or delegation scenarios. The value must correspond to the actual mailbox used. Find out more about [setting the from and sender properties](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages#setting-the-from-and-sender-properties) of a message. |
| hasAttachments | Boolean | Indicates whether the message has attachments. |
| id | String | Unique identifier for the message. By default, this value changes when the item is moved from one container \(such as a folder or calendar\) to another. To change this behavior, use the `Prefer: IdType="ImmutableId"` header. See [Get immutable identifiers for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-immutable-id) for more information. Read-only. |
| importance | String | The importance of the message: `low`, `normal`, `high`. |
| inferenceClassification | String | The possible values are: `focused`, `other`. |
| internetMessageHeaders | [internetMessageHeader](https://learn.microsoft.com/en-us/graph/api/resources/internetmessageheader?view=graph-rest-1.0) collection | The collection of message headers, defined by [RFC5322](https://www.ietf.org/rfc/rfc5322.txt), that provide details of the network path taken by a message from the sender to the recipient. Read-only. |
| internetMessageId | String | The message ID in the format specified by [RFC5322](https://www.ietf.org/rfc/rfc5322.txt). |
| isAllDay | Boolean | Indicates whether the event lasts the entire day. Adjusting this property requires adjusting the **startDateTime** and **endDateTime** properties of the event as well. |
| isDelegated | Boolean | True if this meeting request response is accessible to a delegate, false otherwise. Default is false. |
| isDeliveryReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| isDraft | Boolean | Indicates whether the message is a draft. A message is a draft if it hasn't been sent yet. |
| isOutOfDate | Boolean | Indicates whether this meeting request has been made out-of-date by a more recent request. |
| isRead | Boolean | Indicates whether the message has been read. |
| isReadReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| lastModifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| location | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The location of the requested meeting. |
| meetingMessageType | String | The type of event message: `none`, `meetingRequest`, `meetingCancelled`, `meetingAccepted`, `meetingTentativelyAccepted`, `meetingDeclined`. |
| parentFolderId | String | The unique identifier for the message's parent mailFolder. |
| proposedNewTime | [timeSlot](https://learn.microsoft.com/en-us/graph/api/resources/timeslot?view=graph-rest-1.0) | An alternate date/time proposed by an invitee for a meeting request to start and end. Read-only. Not filterable. |
| receivedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurrence pattern of the requested meeting. |
| replyTo | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The email addresses to use when replying. |
| responseType | string | Specifies the type of response to a meeting request. The possible values are: `tentativelyAccepted`, `accepted`, `declined`. For the eventMessageResponse type, `none`, `organizer`, and `notResponded` are not supported. Read-only. Not filterable. |
| sender | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) | The account that is actually used to generate the message. In most cases, this value is the same as the **from** property. You can set this property to a different value when sending a message from a [shared mailbox](https://learn.microsoft.com/en-us/exchange/collaboration/shared-mailboxes/shared-mailboxes), [for a shared calendar, or as a delegate](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar). In any case, the value must correspond to the actual mailbox used. Find out more about [setting the from and sender properties](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages#setting-the-from-and-sender-properties) of a message. |
| sentDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The start time of the requested meeting. |
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

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "bccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "bodyPreview": "String",
  "categories": ["String"],
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "changeKey": "String",
  "conversationId": "String",
  "conversationIndex": "String (binary)",
  "createdDateTime": "String (timestamp)",
  "endDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "flag": {"@odata.type": "microsoft.graph.followupFlag"},
  "from": {"@odata.type": "microsoft.graph.recipient"},
  "hasAttachments": true,
  "id": "String (identifier)",
  "importance": "string",
  "inferenceClassification": "string",
  "internetMessageHeaders": [{"@odata.type": "microsoft.graph.internetMessageHeader"}],
  "internetMessageId": "String",
  "isAllDay": true,
  "isDelegated": true,
  "isDeliveryReceiptRequested": true,
  "isDraft": true,
  "isOutOfDate": true,
  "isRead": true,
  "isReadReceiptRequested": true,
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.location"},
  "meetingMessageType": "string",
  "parentFolderId": "String",
  "proposedNewTime": {"@odata.type": "microsoft.graph.timeSlot"},
  "receivedDateTime": "String (timestamp)",
  "recurrence": {"@odata.type": "microsoft.graph.patternedRecurrence"},
  "replyTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "responseType": "string",
  "sender": {"@odata.type": "microsoft.graph.recipient"},
  "sentDateTime": "String (timestamp)",
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "subject": "String",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "type": "string",
  "uniqueBody": {"@odata.type": "microsoft.graph.itemBody"},
  "webLink": "String"
}
```
