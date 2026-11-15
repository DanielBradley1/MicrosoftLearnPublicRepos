<!-- Source: https://learn.microsoft.com/en-us/graph/api/message-reportmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# message: reportMessage

Namespace: microsoft.graph

Report a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) as junk, phishing, or not junk, which improves mail filtering.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite | Not available. |
| Application | Mail.ReadWrite | Not available. |

## HTTP request

```http
POST /me/messages/{messageId}/reportMessage
POST /users/{userId}/messages/{messageId}/reportMessage
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| IsMessageMoveRequested | Boolean | Indicates whether the message should be moved out of the current folder. Optional. |
| ReportAction | reportAction | Indicates the type of action to be reported on the message that can be junk, not junk, or phishing. The possible values are: `unknown`, `junk`, `notJunk`, `phish`, `unknownFutureValue`. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/messages/AAMkADhAAATs28OAAA=/reportMessage
Content-Type: application/json

{
  "IsMessageMoveRequested": true,
  "ReportAction": "junk"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#message",
  "@odata.type": "#microsoft.graph.message",
  "@odata.etag": "W/\"FwAAABYAAAC4ofQHEIqCSbQPot83AFcbAAAW/0tB\"",
  "id": "AAMkADhAAAW-VPeAAA=",
  "createdDateTime": "2018-08-12T08:43:22Z",
  "lastModifiedDateTime": "2018-08-15T19:47:54Z",
  "changeKey": "FwAAABYAAAC4ofQHEIqCSbQPot83AFcbAAAW/0tB",
  "categories": [],
  "receivedDateTime": "2018-08-12T08:43:22Z",
  "sentDateTime": "2018-08-12T08:43:20Z",
  "hasAttachments": false,
  "internetMessageId": "<00535324-5988-4b6a-b9af-d44cf2d0b691@MWHPR2201MB1022.namprd22.prod.outlook.com>",
  "subject": "Undeliverable: Meet for lunch?",
  "bodyPreview": "Delivery has failed to these recipients or groups:\r\n\r\nfannyd@contoso.com (fannyd@contoso.com)\r\nYour message couldn't be delivered. Despite repeated attempts to deliver your message, querying the Domain Name System (DNS) for the rec",
  "importance": "normal",
  "parentFolderId": "AAMkADhAAAAAAEKAAA=",
  "conversationId": "AAQkADhJzfbkARFhe5kKhjihSA=",
  "isDeliveryReceiptRequested": null,
  "isReadReceiptRequested": false,
  "isRead": false,
  "isDraft": false,
  "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkADhAAAW%2FVPeAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "inferenceClassification": "focused",
  "body": {
    "contentType": "html",
    "content": "<html></html>"
  },
  "sender": {
    "emailAddress": {
      "name": "Microsoft Outlook",
      "address": "MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e@contoso.com"
    }
  },
  "from": {
    "emailAddress": {
      "name": "Microsoft Outlook",
      "address": "MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e@contoso.com"
    }
  },
  "toRecipients": [
    {
      "emailAddress": {
        "name": "fannyd@contoso.com",
        "address": "fannyd@contoso.com"
      }
    },
    {
      "emailAddress": {
        "name": "danas@contoso.com",
        "address": "danas@contoso.com"
      }
    }
  ],
  "ccRecipients": [],
  "bccRecipients": [],
  "replyTo": [],
  "flag": {
    "flagStatus": "notFlagged"
  }
}
```
