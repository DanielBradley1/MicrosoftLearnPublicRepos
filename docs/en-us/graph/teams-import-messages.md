<!-- Source: https://learn.microsoft.com/en-us/graph/teams-import-messages -->
<!-- Sitemap-Last-Modified: 2026-05-16 -->

# Import messages into Microsoft Teams chats and channels using Microsoft Graph

This article describes how to import messages into an existing Microsoft Teams chat or channel during a migration session by using Microsoft Graph. Message import is intended for migration scenarios and requires that the target chat or channel is placed into *migration mode* before you can import content.

## When to use message import

Use message import when you need to:

- Migrate historical messages into an existing Teams chat or channel.
- Preserve the original author attribution \(who the message is from\).
- Optionally preserve \(or set\) a historical timestamp for each message.

## Requirements

To use the Teams messaging API to import messages, the following conditions must be met:

- App-only \(application\) context: The request must be made using application permissions.
- Required permission: The calling app must be granted the `Teamwork.Migrate.All` application permission.
- Migration mode must be enabled on the target:

  - To enable migration mode on a channel, call [channel: startMigration](https://learn.microsoft.com/en-us/graph/api/channel-startmigration).
  - To enable migration mode on a chat, call [chat: startMigration](https://learn.microsoft.com/en-us/graph/api/chat-startmigration).

- Author attribution is required: Set the **from** property to attribute the imported message to a user who belongs to the same tenant as the authenticated application.
- Optional timestamp rules \(if you specify **createdDateTime**\): You can set a custom timestamp for the imported message, but it must meet the following constraints:

  - The value must be *later than* the **createdDateTime** of the target chat or channel.
  - The value must *not* be in the future.
  - The value must be *unique down to the millisecond* within the target chat or channel. If a message with the same **createdDateTime** exists, the request fails with `409 Conflict`; adjust the value and retry.

Note

- Only the application that called [startMigration](https://learn.microsoft.com/en-us/graph/api/channel-startmigration) on the target channel or [startMigration](https://learn.microsoft.com/en-us/graph/api/chat-startmigration) on the target chat can import messages into it. No other application can request this API on the channel or chat until the owning application completes the migration by calling [channel: completeMigration](https://learn.microsoft.com/en-us/graph/api/channel-completemigration) or [chat: completeMigration](https://learn.microsoft.com/en-us/graph/api/chat-completemigration).
- Some imported messages may not be visible in the Teams client until migration is completed by calling [completeMigration](https://learn.microsoft.com/en-us/graph/api/channel-completemigration) on the target channel or [completeMigration](https://learn.microsoft.com/en-us/graph/api/chat-completemigration) on the target chat.

## Troubleshooting

### 409 Conflict when importing a message

The **createdDateTime** must be unique down to the millisecond within the target chat or channel. If a message with the same **createdDateTime** exists, the request fails with `409 Conflict`. Adjust the **createdDateTime** and retry the request.

## Related content

- [Import third-party platform messages to Teams using Microsoft Graph](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams).
- [Send a message in a channel](https://learn.microsoft.com/en-us/graph/api/channel-post-messages)
- [Send a message in a chat](https://learn.microsoft.com/en-us/graph/api/chat-post-messages)
- [Send a message in a channel or a chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-post)
- [Send replies to a message in a channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-post-replies)
