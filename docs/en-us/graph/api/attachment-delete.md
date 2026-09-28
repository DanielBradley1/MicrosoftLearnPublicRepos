<!-- Source: https://learn.microsoft.com/en-us/graph/api/attachment-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Delete attachment

Namespace: microsoft.graph

Delete an attachment from a user calendar event, mail message, note, or group post.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Depending on the resource \(**event**, **message**, **note**, or **post**\) that the attachment is attached to and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) before choosing more privileged permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.ReadWrite | Calendars.ReadWrite | Calendars.ReadWrite |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadWrite | Mail.ReadWrite | Mail.ReadWrite |
| [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) | ShortNotes.ReadWrite | ShortNotes.ReadWrite | ShortNotes.ReadWrite.All |
| [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Not supported |

## HTTP request

Attachments for an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in the user's default [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0).

```http
DELETE /me/events/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/events/{id}/attachments/{id}

DELETE /me/calendar/events/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/calendar/events/{id}/attachments/{id}
```

Attachments for an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in the specified [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) that belongs to the user.

```http
DELETE /me/calendars/{id}/events/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/calendars/{id}/events/{id}/attachments/{id}
```

Attachments for an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in a [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) that belongs to the user's default [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0).

```http
DELETE /me/calendars/{id}/events/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/calendars/{id}/events/{id}/attachments/{id}
```

Attachments for an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in a [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) that belongs to a user's [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0).

```http
DELETE /me/calendarGroups/{id}/calendars/{id}/events/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/calendarGroups/{id}/calendars/{id}/events/{id}/attachments/{id}
```

Attachments for a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) in a user's mailbox.

```http
DELETE /me/messages/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/messages/{id}/attachments/{id}
```

Attachments for a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) contained in a top level [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0) in a user's mailbox.

```http
DELETE /me/mailFolders/{id}/messages/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/mailFolders/{id}/messages/{id}/attachments/{id}
```

Attachments for a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) contained in a child folder of a [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0) in a user's mailbox. The following example shows one level of nesting, but a message can be located in a child of a child and so on.

```http
DELETE /me/mailFolders/{id}/childFolders/{id}/.../messages/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/mailFolders/{id}/childFolders/{id}/messages/{id}/attachments/{id}
```

Attachments for a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) in a user's mailbox.

```http
DELETE /me/notes/{id}/attachments/{id}
DELETE /users/{id | userPrincipalName}/notes/{id}/attachments/{id}
```

Attachments for a [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) in a [thread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) thta belongs to a [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) of a group.

```http
DELETE /groups/{id}/threads/{id}/posts/{id}/attachments/{id}
DELETE /groups/{id}/conversations/{id}/threads/{id}/posts/{id}/attachments/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Example 1: Delete an event attachment

The following example shows how to delete an attachment on an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
DELETE https://graph.microsoft.com/v1.0/me/events/{id}/attachments/{id}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Events["{event-id}"].Attachments["{attachment-id}"].DeleteAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Events().ByEventId("event-id").Attachments().ByAttachmentId("attachment-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.me().events().byEventId("{event-id}").attachments().byAttachmentId("{attachment-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/me/events/{id}/attachments/{id}')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->me()->events()->byEventId('event-id')->attachments()->byAttachmentId('attachment-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Remove-MgUserEventAttachment -UserId $userId -EventId $eventId -AttachmentId $attachmentId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.me.events.by_event_id('event-id').attachments.by_attachment_id('attachment-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Delete a note attachment

The following example shows how to delete an attachment on a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0).

#### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/me/notes/AAMkAGI2THVSAAA=/attachments/AAMkAGI2attach2
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
