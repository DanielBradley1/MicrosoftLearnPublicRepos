<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/invitedusermessageinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-17 -->

# invitedUserMessageInfo resource type

Namespace: microsoft.graph

The invitedUserMessageInfo object allows you to configure the [invitation](https://learn.microsoft.com/en-us/graph/api/resources/invitation?view=graph-rest-1.0) message.

For more information about configuring the invitation message, see [B2B invitation email layout and language settings](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ccRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | Additional recipients the invitation message should be sent to. Currently only one additional recipient is supported. |
| customizedMessageBody | String | Customized message body you want to send if you don't want the default message. Only plain text is allowed. |
| messageLanguage | String | The language you want to send the default message in. If the customizedMessageBody is specified, this property is ignored, and the message is sent using the customizedMessageBody. The language format should be in ISO 639. The default is en-US. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "ccRecipients": [ {"@odata.type": "microsoft.graph.recipient"} ],
  "customizedMessageBody": "string",
  "messageLanguage": "string"
}
```
