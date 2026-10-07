<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/components/chat -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Chat component in Microsoft Graph Toolkit

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/).

Note

This component is in preview and is subject to change. The use of these components in production applications is not supported. This component is currently only available as a React component and doesn't have a web component equivalent.

The chat component enables the user to have 1:1 or group conversations. This component doesn't support channel conversations. The component allows for rendering conversations and authoring new messages. All data is stored in Microsoft Teams.

## Example

The following example displays a conversation using the `mgt-chat` component.

![A screenshot of a chat component](https://learn.microsoft.com/en-us/graph/toolkit/components/images/mgt-chat.png)

## Properties

| Attribute | Property | Description |
| --- | --- | --- |
| chat-id | chatId | A string ID to set the 1:1 or group [conversation](https://learn.microsoft.com/en-us/graph/api/resources/chat) to render. Required. |

## CSS custom properties

The `mgt-chat` component doesn't define CSS custom properties.

## Events

The `mgt-chat` component doesn't offer any events.

## Templates

The `mgt-chat` component doesn't offer templates to override.

## Microsoft Graph permissions

This control uses the following Microsoft Graph APIs and permissions.

| Configuration | Permission | API |
| --- | --- | --- |
| `chatId` is set | Chat.ReadBasic, Chat.Read, ChatMessage.Read, Chat.ReadWrite, ChatMember.ReadWrite | [/chats/{id}/messages](https://learn.microsoft.com/en-us/graph/api/chat-list-messages), [/chats/{id}/messages](https://learn.microsoft.com/en-us/graph/api/chat-post-messages), [/chats/{id}/messages/{messageId}](https://learn.microsoft.com/en-us/graph/api/chatmessage-update), [/me/chats/{id}/messages/{messageId}/softDelete](https://learn.microsoft.com/en-us/graph/api/chatmessage-softdelete), [/chats/{id}/members/{membershipId}](https://learn.microsoft.com/en-us/graph/api/chat-delete-members), [/chats/{id}/members](https://learn.microsoft.com/en-us/graph/api/chat-post-members), [/chats/{id}/messages/{messageId}/hostedContents/{hostedContentId}](https://learn.microsoft.com/en-us/graph/api/chatmessagehostedcontent-get), [/chats/{id}](https://learn.microsoft.com/en-us/graph/api/chat-patch) |

### Subcomponents

The `mgt-chat` component consists of one or more subcomponents that might require other permissions than the ones listed previously. For more information, see the documentation for each subcomponent:

- [mgt-person](https://learn.microsoft.com/en-us/graph/toolkit/components/person)
- [mgt-people-picker](https://learn.microsoft.com/en-us/graph/toolkit/components/people-picker)

## Authentication

The `mgt-chat` component uses the global authentication provider described in the [authentication documentation](https://learn.microsoft.com/en-us/graph/toolkit/providers/providers).

## Cache

The `mgt-chat` component caches chat messages and related metadata.

## Localization

The `mgt-chat` component doesn't expose any localization variables.

## Known issues

- The `mgt-chat` component doesn't support the same `chatId` being used in multiple instances of the component or across multiple tabs.
- The `mgt-chat` component doesn't support theming and won't respect browsers preferences.
