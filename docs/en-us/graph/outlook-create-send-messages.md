<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-create-send-messages -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Automate creating, sending, and processing messages

Emails are represented by the [message](https://learn.microsoft.com/en-us/graph/api/resources/message) resource in Microsoft Graph.

By default, messages are identified by a unique entry ID in the **id** property. When a message is initially created and saved as a draft or sent, the store provider assigns the message an entry ID. By default, that ID changes when the message is copied or moved to another folder, store, or .PST file. You reference the message by its current ID for further processing.

## Create and send mail

In Outlook, you can create and send an email in the same [sendMail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) action, or you can [create](https://learn.microsoft.com/en-us/graph/api/user-post-messages) a draft, subsequently [add content](https://learn.microsoft.com/en-us/graph/api/message-update) and [send](https://learn.microsoft.com/en-us/graph/api/message-send) the draft.

Similarly, when responding to an email, you can create and send the response in the same action \([reply](https://learn.microsoft.com/en-us/graph/api/message-reply), [reply-all](https://learn.microsoft.com/en-us/graph/api/message-replyall), or [forward](https://learn.microsoft.com/en-us/graph/api/message-forward)\). Or, you can create a draft for the response \([reply](https://learn.microsoft.com/en-us/graph/api/message-createreply), [reply-all](https://learn.microsoft.com/en-us/graph/api/message-createreplyall), or [forward](https://learn.microsoft.com/en-us/graph/api/message-createforward)\), [add content](https://learn.microsoft.com/en-us/graph/api/message-update), and then [send](https://learn.microsoft.com/en-us/graph/api/message-send) the draft at a later time.

To distinguish between a draft and a sent message programmatically, check the **isDraft** property.

By default, draft messages are saved in the `Drafts` folder, sent messages are saved in the `Sent Items` folder. For convenience, you can identify the Drafts folder and SentItems folder by their corresponding [well-known folder names](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder).

### Set the from and sender properties

When a message is being composed, in most cases, Outlook sets the **from** and **sender** properties to the same signed-in user. You can update these properties in the following scenarios:

- The **from** property can be changed if the Exchange administrator has assigned **sendAs** rights of the mailbox to some other users. The administrator can do this by selecting **Mailbox Permissions** of the mailbox owner in the Azure portal, or by using the Exchange Admin Center or a Windows PowerShell Add-ADPermission cmdlet. Then, you can programmatically set the **from** property to one of these users who have **sendAs** rights for that mailbox.
- The **sender** property can be changed if the mailbox owner has delegated one or more users to be able to send messages from that mailbox. The mailbox owner can delegate in Outlook. When a delegate sends a message on behalf of the mailbox owner, Outlook sets the **sender** property to the delegate’s account, and the **from** property remains as the mailbox owner. Programmatically, you can set the **sender** property to a user who has got delegate permissions for that mailbox.

## Use MailTips to check recipient status and save time \(preview\)

Use [MailTips](https://learn.microsoft.com/en-us/graph/api/resources/mailtips) to make smart decisions before sending an email. MailTips can tell you information such as the recipient's mailbox is restricted to specific senders, or approval is required for emailing the recipient.

## Read messages with control over the body format returned

You can [read a message](https://learn.microsoft.com/en-us/graph/api/message-get) in a mailbox by referencing its ID:

```http
GET /me/messages/AAMkADhMGAAA=
```

Or, you can [get the messages](https://learn.microsoft.com/en-us/graph/api/user-list-messages) in a specific folder. For example, to read messages in the signed-in user's Drafts folder:

```http
GET /me/mailfolders('Drafts')
```

The body of an Outlook message can be either HTML or text, with HTML as the default message body type returned in a GET response.

When getting a message, you can specify the following request header to return the **body** and **uniqueBody** properties in text format:

```http
Prefer: outlook.body-content-type="text"
```

You can specify the following header, or, just skip the header, to get the message body in HTML format:

```http
Prefer: outlook.body-content-type="html"
```

When you specify either header, a successful response would include the corresponding `Preference-Applied` header:

- For text format requests: `Preference-Applied: outlook.body-content-type="text"`
- For HTML format requests: `Preference-Applied: outlook.body-content-type="html"`

If the body is HTML, by default, Outlook removes any potentially unsafe HTML \(for example, JavaScript\) embedded in the **body** property before returning the body content in a REST response.

To get the entire, original HTML content, include the following HTTP request header:

```http
Prefer: outlook.allow-unsafe-html
```

## Integrate with '@' social gesture \(preview\)

@-mentions are notifications to alert users if they are mentioned in messages. The [mention](https://learn.microsoft.com/en-us/graph/api/resources/mention) resource enables apps to set and get the common online social gesture, the '@' prefix, in emails. You can:

- Create @-mentions when [creating a message](https://learn.microsoft.com/en-us/graph/api/user-post-messages#request-2)
- [Get all the messages in a user's mailbox that contain an @-mention of the user](https://learn.microsoft.com/en-us/graph/api/user-list-messages#request-2)
- [Get all the @-mention is a message](https://learn.microsoft.com/en-us/graph/api/message-get#request-2)

## Other shared capabilities

Take advantage of the following common capabilities that are shared among Microsoft Graph entities:

- Subscribe to [change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview) on messages when one or more types of changes occur, such as message creation or update.
- [Track incremental changes to messages in a folder](https://learn.microsoft.com/en-us/graph/delta-query-messages).
- Create [open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#open-extensions) or [schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#schema-extensions) to add custom data to a message instance.
- Create [extended properties](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview) in a message instance to store custom data for Outlook MAPI properties, when these properties are not already exposed in the Microsoft Graph API metadata.

## Next steps

- [Why integrate with Outlook mail](https://learn.microsoft.com/en-us/graph/outlook-mail-concept-overview)
- [Get MIME content \(preview\)](https://learn.microsoft.com/en-us/graph/outlook-get-mime-message)
- [Get shared messages](https://learn.microsoft.com/en-us/graph/outlook-share-messages-folders)
- [Send Outlook messages from another user](https://learn.microsoft.com/en-us/graph/outlook-send-mail-from-other-user)
- [Get immutable identifiers for Outlook resources](https://learn.microsoft.com/en-us/graph/outlook-immutable-id)
- [Using the mail API](https://learn.microsoft.com/en-us/graph/api/resources/mail-api-overview) and its [use cases](https://learn.microsoft.com/en-us/graph/api/resources/mail-api-overview#common-use-cases) in Microsoft Graph v1.0.
