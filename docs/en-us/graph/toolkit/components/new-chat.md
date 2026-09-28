<!-- Source: https://learn.microsoft.com/en-us/graph/toolkit/components/new-chat -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# New chat component in Microsoft Graph Toolkit

Caution

The Microsoft Graph Toolkit is deprecated. The retirement period begins September 1, 2025, with full retirement planned for August 28, 2026. Developers should migrate to using the Microsoft Graph SDKs or other supported Microsoft Graph tools for building web experiences. For more information, see the [deprecation announcement](https://devblogs.microsoft.com/microsoft365dev/microsoft-graph-toolkit-retirement/)

Note

This component is in Preview and is subject to change. The use of these components in production applications is not supported. This component is currently only available as a React component and doesn't have a web component equivalent.

The new chat component allows users to create new 1:1 or group conversations in Microsoft Teams.

## Example

The following example displays a new chat form using the `mgt-new-chat` component.

![A screenshot of a new chat component](https://learn.microsoft.com/en-us/graph/toolkit/components/images/mgt-new-chat.png)

## Properties

| Attribute | Property | Description |
| --- | --- | --- |
| mode | mode | Set to `oneOnOne`, `group` or `auto`. Default is `auto`. |

```typescript
<NewChat mode="group" />
```

## CSS custom properties

The `mgt-new-chat` component doesn't define CSS custom properties.

## Events

The following events are fired from the component.

| Event | When is it emitted | Custom data | Cancelable | Bubbles | Works with custom template |
| --- | --- | --- | :---: | :---: | :---: |
| `onChatCreated` | Fired when a new chat thread is created. | The `chat` object that was created as a Microsoft Graph [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat#json-representation). | No | No | No |
| `onCancelClicked` | Fired when user cancels the chat thread creation. | None | No | No | No |

For more information about handling events, see [events](https://learn.microsoft.com/en-us/graph/toolkit/customize-components/events).

## Templates

The `mgt-new-chat` component doesn't offer any template to override.

## Microsoft Graph permissions

This control uses the following Microsoft Graph APIs and permissions.

| Configuration | Permission | API |
| --- | --- | --- |
| Default | Chat.Create, ChatMessage.Send | [/chats](https://learn.microsoft.com/en-us/graph/api/chat-post), [/chats/{id}/messages](https://learn.microsoft.com/en-us/graph/api/chat-post-messages) |

### Subcomponents

The `mgt-new-chat` component consists of one or more subcomponents that might require other permissions than the ones listed previously. For more information, see the documentation for each subcomponent: [mgt-people-picker](https://learn.microsoft.com/en-us/graph/toolkit/components/people-picker).

## Authentication

The tasks component uses the global authentication provider described in the [authentication documentation](https://learn.microsoft.com/en-us/graph/toolkit/providers/providers).

## Cache

The `mgt-new-chat` component doesn't cache any data.

## Localization

The `mgt-new-chat` component doesn't expose any localization variables.

## Known issues

- The `mgt-new-chat` component doesn't support theming and won't respect browsers preferences.
