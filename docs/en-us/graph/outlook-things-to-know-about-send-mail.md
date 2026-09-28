<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-things-to-know-about-send-mail -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Overview of the Microsoft Graph send mail process

In Microsoft Graph, each of the [forward](https://learn.microsoft.com/en-us/graph/api/message-forward), [reply](https://learn.microsoft.com/en-us/graph/api/message-reply), [replyAll](https://learn.microsoft.com/en-us/graph/api/message-replyAll), or [sendMail](https://learn.microsoft.com/en-us/graph/api/user-sendmail) methods creates and sends an email message in the same call. This article summarizes how Outlook and Exchange Online usually process the send mail API calls to send mail. Most of the steps \(steps 2 to 7\) take place after the method response is returned.

## 1. Create a new message in sender's mailbox

Outlook creates a new message in the sender's Drafts folder, copies the message content, recipients, and attachments from the JSON request to the draft message, and saves it. If successful, the method returns an HTTP response `202 Accepted` status code.

If the sender provided MIME content, Exchange Online copies it to a single property in the new draft message. Exchange Online then parses the MIME content and copies relevant content to message properties, and to the recipients and attachments tables. When complete, the method returns a `202 Accepted` status code.

This step might fail for reasons such as the sender's mailbox is full, or the network connection to the sender's server is down. If the method fails, it returns a 4xx or 5xx status code accordingly.

When step 1 is complete, your app's direct interaction with Microsoft Graph is over.

## 2. Notify transport service of new outbound message

Exchange Online notifies its transport service that a new message is available for pickup.

## 3. Copy outbound message to transport pipeline

The transport process reads message content from the sender's mailbox, converts it to MIME format, and stores it into the transport pipeline. If the sender provided MIME content, the transport process copies the MIME content more or less intact. Otherwise, the transport process serializes the message properties to construct MIME content.

If step 3 fails, the transport process constructs a non-delivery report message and places it in the sender's Inbox.

## 4. Move original message to the Sent Items folder

After all of this succeeds, transport calls back to the store to assume responsibility for the message. In response, the Exchange store updates the message and moves it from the Drafts folder to the Sent Items folder. \(Depending on optional message properties, it might move to a different folder or delete the message instead.\)

## 5. Perform policy evaluation and routing

The next steps taken by transport include policy enforcement, routing, and next-hop delivery. Transport examines recipient email addresses and buckets them according to what the initial routing hop has to be. Transport detects invalid recipient addresses at this point, for which transport mails the non-delivery reports back to the sender. Transport then applies policies configured by tenant administrators. Such policies might reject the message based on its content, store copies, and so on. After applying policy, transport fans out a copy of the message to each next-hop destination. For more details about the transport flow, see [mail flow and the transport pipeline](https://learn.microsoft.com/en-us/Exchange/mail-flow/mail-flow).

## 6. Deliver message to recipients

Exchange Online transport might or might not be responsible for final delivery to all recipients. That depends on whether those recipients have Exchange Online mailboxes.

## 7. Deliver report messages to sender

A few services are involved in generating delivery reports and sending them to the sender accordingly:

- When a responsible transport component, which can be a Exchange Online or non-Exchange Online component, determines that one or more recipient email addresses are non-deliverable, the component generates non-delivery reports.
- At the same time, the transport component generates delivery reports if the sender explicitly requested them.
- The recipient's email service or email client might generate read and non-read notifications, or not at all.

For more information about report messages, see [DSNs and NDRs in Exchange Server](https://learn.microsoft.com/en-us/exchange/mail-flow/non-delivery-reports-and-bounce-messages/non-delivery-reports-and-bounce-messages).

## Related content

- [Why integrate with Outlook mail](https://learn.microsoft.com/en-us/graph/outlook-mail-concept-overview).
- [Automate creating, sending, and processing messages](https://learn.microsoft.com/en-us/graph/outlook-create-send-messages).
- [Send messages with MIME content](https://learn.microsoft.com/en-us/graph/outlook-send-mime-message).
- [Send Outlook messages from another user](https://learn.microsoft.com/en-us/graph/outlook-send-mail-from-other-user).
- [Use the mail API](https://learn.microsoft.com/en-us/graph/api/resources/mail-api-overview)

Microsoft Graph APIs that create and send a draft in separate calls:

- [Create draft message](https://learn.microsoft.com/en-us/graph/api/user-post-messages)
- [Create draft to reply](https://learn.microsoft.com/en-us/graph/api/message-createreply)
- [Create draft to reply-all](https://learn.microsoft.com/en-us/graph/api/message-createreplyall)
- [Create draft to forward message](https://learn.microsoft.com/en-us/graph/api/message-createforward)
- [Send draft message](https://learn.microsoft.com/en-us/graph/api/message-send)
