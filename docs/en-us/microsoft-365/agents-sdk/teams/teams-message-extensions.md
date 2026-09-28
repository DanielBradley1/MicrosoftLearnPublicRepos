<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-message-extensions -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Use message extensions in Microsoft Teams

Message extensions surface as commands in the Teams compose box, the action menu on messages, or link previews. In the Teams app manifest, each command is identified by the `id` property in the `composeExtensions[].commands[]` array. Pass that value to the SDK route's `commandId` parameter, such as the constructor argument in `[TeamsQueryRoute("searchQuery")]`.

The examples build card payloads as JSON. For guidance on card structure and other C# construction options, see [Building Adaptive Cards](https://microsoft.github.io/teams-sdk/csharp/in-depth-guides/adaptive-cards/building-adaptive-cards).

## Query and SelectItem

Users can query your service and pick results to insert into a message.

Add this command to the Teams manifest:

```json
"composeExtensions": [
  {
    "commands": [
      {
        "id": "searchQuery",
        "type": "query",
        "title": "searchQuery",
        "description": "searchQuery",
        "initialRun": true,
        "fetchTask": false,
        "context": ["commandBox", "compose"],
        "parameters": [
          {
            "name": "searchQuery",
            "title": "Search Query",
            "description": "Search Query",
            "inputType": "text"
          }
        ]
      }
    ]
  }
]
```

```csharp
using Microsoft.Teams.Apps.MessageExtensions;
using Microsoft.Teams.Apps.Schema;
using System.Text.Json;

[TeamsExtension]
public partial class SearchAgent(AgentApplicationOptions options) : AgentApplication(options)
{
    [TeamsQueryRoute("searchQuery")]
    public Task<MessageExtensionResponse> OnSearchAsync(
        ITeamsTurnContext turnContext,
        ITurnState turnState,
        MessageExtensionQuery query,
        CancellationToken cancellationToken)
    {
        bool initialRun = query.Parameters?
            .FirstOrDefault(p => p.Name == "initialRun")?
            .Value?.ToString() == "true";

        if (initialRun)
        {
            return Task.FromResult(CreateMessageResponse("Enter search query"));
        }

        string searchText = query.Parameters?
            .FirstOrDefault(p => p.Name == "searchQuery")?.Value?.ToString() ?? "";

        var attachments = new List<TeamsAttachment>();
        for (int i = 1; i <= 5; i++)
        {
            var cardJson = $$"""
            {
              "type": "AdaptiveCard",
              "version": "1.4",
              "body": [
                {
                  "type": "TextBlock",
                  "text": {{$"Search Result {i}"}},
                  "size": "Large",
                  "weight": "Bolder"
                },
                {
                  "type": "TextBlock",
                  "text": {{$"Query: '{searchQuery}' - Result description for item {i}"}},
                  "wrap": true,
                  "isSubtle": true
                }
              ]
            }
            """;

            var previewJson = $$"""
            {
              "title": {{$"Result {i}"}},
              "text": {{$"This is a preview of result {i} for query '{searchQuery}'."}},
              "tap": {
                "type": "invoke",
                "value": {
                  "index": {{$"{i}"}},
                  "query": {{$"{searchQuery}"}}
                }
              }
            }
            """;

            attachments.Add(CreateAdaptiveCardAttachment(cardJson, previewJson));
        }

        return Task.FromResult(CreateResultResponse([.. attachments]));
    }

    [TeamsSelectItemRoute]
    public Task<MessageExtensionResponse> OnSelectItemAsync(
        ITeamsTurnContext turnContext,
        ITurnState turnState,
        Dictionary<string, string> items,
        CancellationToken cancellationToken)
    {
        var index = items.TryGetValue("index", out string? value) ? value : "No Index";
        var query = items.TryGetValue("query", out string? queryValue) ? queryValue : "No Query";

        var cardJson = $$"""
        {
          "type": "AdaptiveCard",
          "version": "1.4",
          "body": [
            {
              "type": "TextBlock",
              "text": "Item Selected",
              "size": "Large",
              "weight": "Bolder",
              "color": "Good"
            },
            {
              "type": "TextBlock",
              "text": {{$"You selected item: {index} for query: '{query}'"}},
              "wrap": true,
              "separator": true,
              "fontType": "Monospace"
            }
          ]
        }
        """;

        return Task.FromResult(
            CreateResultResponse(CreateAdaptiveCardAttachment(cardJson)));
    }

    private static MessageExtensionResponse CreateMessageResponse(string text)
    {
        return MessageExtensionResponse.CreateBuilder()
            .WithType(MessageExtensionResponseTypes.Message)
            .WithText(text)
            .Build()
            .Body
            ?? throw new InvalidOperationException("The message extension response builder returned no body.");
    }

    private static MessageExtensionResponse CreateResultResponse(params TeamsAttachment[] attachments)
    {
        return MessageExtensionResponse.CreateBuilder()
            .WithType(MessageExtensionResponseTypes.Result)
            .WithAttachmentLayout(AttachmentLayoutType.List)
            .WithAttachments(attachments)
            .Build()
            .Body
            ?? throw new InvalidOperationException("The message extension response builder returned no body.");
    }

    private static TeamsAttachment CreateAdaptiveCardAttachment(
        string cardJson,
        string? previewJson = null)
    {
        var attachment = new TeamsAttachment
        {
            ContentType = AttachmentContentTypes.AdaptiveCard,
            Content = JsonSerializer.Deserialize<JsonElement>(cardJson)
        };

        if (previewJson is not null)
        {
            attachment.Properties = new()
            {
                ["preview"] = new TeamsAttachment
                {
                    ContentType = AttachmentContentTypes.ThumbnailCard,
                    Content = JsonSerializer.Deserialize<JsonElement>(previewJson)
                }
            };
        }

        return attachment;
    }
}
```

```javascript
teams.messageExtensions
  .onQuery('searchQuery', async (context, state, query) => {
    const initialRun = query.parameters
      ?.find((parameter) => parameter.name === 'initialRun')
      ?.value?.toString() === 'true'

    if (initialRun) {
      return {
        composeExtension: {
          type: 'message',
          text: 'Enter search query'
        }
      }
    }

    const searchText = query.parameters
      ?.find((parameter) => parameter.name === 'searchQuery')
      ?.value?.toString() ?? ''

    const attachments = []
    for (let i = 1; i <= 5; i++) {
      attachments.push({
        contentType: 'application/vnd.microsoft.card.adaptive',
        content: {
          $schema: 'https://adaptivecards.io/schemas/adaptive-card.json',
          type: 'AdaptiveCard',
          version: '1.4',
          body: [
            {
              type: 'TextBlock',
              text: `Search Result ${i}`,
              size: 'Large',
              weight: 'Bolder'
            },
            {
              type: 'TextBlock',
              text: `Query: '${searchText}' - Result description for item ${i}`,
              wrap: true,
              isSubtle: true
            }
          ]
        },
        preview: {
          contentType: 'application/vnd.microsoft.card.thumbnail',
          content: {
            title: `Result ${i}`,
            text: `This is a preview of result ${i} for query '${searchText}'.`,
            tap: {
              type: 'invoke',
              value: { index: i.toString(), query: searchText }
            }
          }
        }
      })
    }

    return {
      composeExtension: {
        attachmentLayout: 'list',
        type: 'result',
        attachments
      }
    }
  })
  .onSelectItem(async (context, state, item) => {
    const index = item?.index ?? 'No Index'
    const query = item?.query ?? 'No Query'

    return {
      composeExtension: {
        attachmentLayout: 'list',
        type: 'result',
        attachments: [{
          contentType: 'application/vnd.microsoft.card.adaptive',
          content: {
            $schema: 'https://adaptivecards.io/schemas/adaptive-card.json',
            type: 'AdaptiveCard',
            version: '1.4',
            body: [
              {
                type: 'TextBlock',
                text: 'Item Selected',
                size: 'Large',
                weight: 'Bolder',
                color: 'Good'
              },
              {
                type: 'TextBlock',
                text: `You selected item: ${index} for query: '${query}'`,
                wrap: true,
                separator: true,
                fontType: 'Monospace'
              }
            ]
          }
        }]
      }
    }
  })
```

```python
from microsoft_teams.api.models import (
    MessagingExtensionQuery,
    MessagingExtensionResponse,
    MessagingExtensionResult,
    MessagingExtensionResultType,
    MessagingExtensionAttachment,
    MessagingExtensionAttachmentLayout,
)

@teams.message_extensions.query("searchQuery")
async def on_search(context, state, query: MessagingExtensionQuery) -> MessagingExtensionResponse:
    params = {p.name: p.value for p in (query.parameters or [])}
    if str(params.get("initialRun", "")).lower() == "true":
        return MessagingExtensionResponse(
            compose_extension=MessagingExtensionResult(
                type=MessagingExtensionResultType.MESSAGE,
                text="Enter search query",
            )
        )

    search_text = str(params.get("searchQuery", "") or "")

    attachments = []
    for i in range(1, 6):
        card = {
            "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
            "type": "AdaptiveCard",
            "version": "1.4",
            "body": [
                {
                    "type": "TextBlock",
                    "text": f"Search Result {i}",
                    "size": "Large",
                    "weight": "Bolder",
                },
                {
                    "type": "TextBlock",
                    "text": f"Query: '{search_text}' - Result description for item {i}",
                    "wrap": True,
                    "isSubtle": True,
                },
            ],
        }
        preview = {
            "title": f"Result {i}",
            "text": f"This is a preview of result {i} for query '{search_text}'.",
            "tap": {"type": "invoke", "value": {"index": str(i), "query": search_text}},
        }
        attachments.append(
            MessagingExtensionAttachment(
                content_type="application/vnd.microsoft.card.adaptive",
                content=card,
                preview=MessagingExtensionAttachment(
                    content_type="application/vnd.microsoft.card.thumbnail",
                    content=preview,
                ),
            )
        )

    return MessagingExtensionResponse(
        compose_extension=MessagingExtensionResult(
            type=MessagingExtensionResultType.RESULT,
            attachment_layout=MessagingExtensionAttachmentLayout.LIST,
            attachments=attachments,
        )
    )

@teams.message_extensions.select_item
async def on_select_item(context, state, item) -> MessagingExtensionResponse:
    item = item or {}
    index = item.get("index", "No Index")
    query = item.get("query", "No Query")
    card = {
        "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.4",
        "body": [
            {
                "type": "TextBlock",
                "text": "Item Selected",
                "size": "Large",
                "weight": "Bolder",
                "color": "Good",
            },
            {
                "type": "TextBlock",
                "text": f"You selected item: {index} for query: '{query}'",
                "wrap": True,
                "separator": True,
                "fontType": "Monospace",
            },
        ],
    }
    return MessagingExtensionResponse(
        compose_extension=MessagingExtensionResult(
            type=MessagingExtensionResultType.RESULT,
            attachment_layout=MessagingExtensionAttachmentLayout.LIST,
            attachments=[
                MessagingExtensionAttachment(
                    content_type="application/vnd.microsoft.card.adaptive",
                    content=card,
                )
            ],
        )
    )
```

## Action commands

A submit action command opens a form, collects input, and returns a card to post into the conversation.

The Teams manifest must contain the following command:

```json
"composeExtensions": [
  {
    "commands": [
      {
        "id": "createCard",
        "type": "action",
        "title": "Create Card",
        "description": "Create Card",
        "initialRun": false,
        "fetchTask": false,
        "context": ["commandBox", "compose", "message"],
        "parameters": [
          { "name": "title", "title": "Title", "inputType": "text" },
          { "name": "description", "title": "Description", "inputType": "text" }
        ]
      }
    ]
  }
]
```

```csharp
using Microsoft.Teams.Apps.MessageExtensions;
using Microsoft.Teams.Apps.Schema;
using System.Text.Json;

[TeamsSubmitActionRoute("createCard")]
public Task<MessageExtensionResponse> OnCreateCardAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    MessageExtensionAction action,
    CancellationToken cancellationToken)
{
    var data = action.GetDataAs<JsonElement>();
    var title = data.GetDataString("title", "Default Title");
    var description = data.GetDataString("description", "Default Description");

    var cardJson = $$"""
    {
        "type": "AdaptiveCard",
        "version": "1.4",
        "body": [
            { "type": "TextBlock", "text": "Custom Card Created", "size": "Large", "weight": "Bolder", "color": "Good" },
            { "type": "TextBlock", "text": {{title}}, "size": "Medium", "weight": "Bolder" },
            { "type": "TextBlock", "text": {{description}}, "wrap": true, "isSubtle": true }
        ]
    }
    """;

    var attachment = new TeamsAttachment
    {
        ContentType = AttachmentContentTypes.AdaptiveCard,
        Content = JsonSerializer.Deserialize<JsonElement>(cardJson)
    };

    var response = MessageExtensionResponse.CreateBuilder()
        .WithType(MessageExtensionResponseTypes.Result)
        .WithAttachmentLayout(AttachmentLayoutType.List)
        .WithAttachments([attachment])
        .Build()
        .Body
        ?? throw new InvalidOperationException("The message extension response builder returned no body.");

    return Task.FromResult(response);
}
```

```javascript
teams.messageExtensions
  .onSubmitAction('createCard', async (context, state, action) => {
    const title = action.data?.title ?? 'Default Title'
    const description = action.data?.description ?? 'Default Description'

    return {
      composeExtension: {
        type: 'result',
        attachmentLayout: 'list',
        attachments: [{
          contentType: 'application/vnd.microsoft.card.adaptive',
          content: {
            $schema: 'https://adaptivecards.io/schemas/adaptive-card.json',
            type: 'AdaptiveCard',
            version: '1.4',
            body: [
              { type: 'TextBlock', text: 'Custom Card Created', size: 'Large', weight: 'Bolder', color: 'Good' },
              { type: 'TextBlock', text: title, size: 'Medium', weight: 'Bolder' },
              { type: 'TextBlock', text: description, wrap: true, isSubtle: true }
            ]
          }
        }]
      }
    }
  })
```

The submit action handler receives a `MessagingExtensionAction`. Read the form fields from `action.data`:

```python
from microsoft_teams.api.models import (
    MessagingExtensionAction,
    MessagingExtensionResponse,
    MessagingExtensionResult,
    MessagingExtensionResultType,
    MessagingExtensionAttachment,
    MessagingExtensionAttachmentLayout,
)

@teams.message_extensions.submit_action("createCard")
async def on_create_card(context, state, action: MessagingExtensionAction) -> MessagingExtensionResponse:
    data = action.data if isinstance(action.data, dict) else {}
    title = data.get("title") or "Default Title"
    description = data.get("description") or "Default Description"

    card = {
        "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.4",
        "body": [
            {"type": "TextBlock", "text": "Custom Card Created", "size": "Large", "weight": "Bolder", "color": "Good"},
            {"type": "TextBlock", "text": title, "size": "Medium", "weight": "Bolder"},
            {"type": "TextBlock", "text": description, "wrap": True, "isSubtle": True},
        ],
    }
    return MessagingExtensionResponse(
        compose_extension=MessagingExtensionResult(
            type=MessagingExtensionResultType.RESULT,
            attachment_layout=MessagingExtensionAttachmentLayout.LIST,
            attachments=[
                MessagingExtensionAttachment(
                    content_type="application/vnd.microsoft.card.adaptive",
                    content=card,
                )
            ],
        )
    )
```

## Link unfurling

Link unfurling generates a rich preview card when a user pastes a URL into the compose box. Teams calls your agent when the URL's domain matches a `messageHandlers` entry in your app manifest:

```json
"composeExtensions": [{
  "botId": "...",
  "messageHandlers": [{
    "type": "link",
    "value": { "domains": ["*.contoso.com"] }
  }]
}]
```

```csharp
using Microsoft.Teams.Apps.MessageExtensions;
using Microsoft.Teams.Apps.Schema;
using System.Text.Json;

[TeamsQueryLinkRoute]
public Task<MessageExtensionResponse> OnQueryLinkAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    MessageExtensionQueryLink? query,
    CancellationToken cancellationToken)
{
    var url = query?.Url?.ToString();
    if (string.IsNullOrWhiteSpace(url))
    {
        return Task.FromResult(CreateMessageResponse("No URL provided"));
    }

    var cardJson = $$"""
    {
      "type": "AdaptiveCard",
      "version": "1.4",
      "body": [
        {
          "type": "TextBlock",
          "text": "Link Preview",
          "size": "Medium",
          "weight": "Bolder"
        },
        {
          "type": "TextBlock",
          "text": {{$"URL: {url}"}},
          "wrap": true,
          "isSubtle": true
        },
        {
          "type": "TextBlock",
          "text": "This is a preview of the linked content generated by the message extension.",
          "wrap": true,
          "size": "Small"
        }
      ]
    }
    """;

    var previewJson = $$"""
    {
      "title": "Link Preview",
      "text": {{url}}
    }
    """;

    var attachment = new TeamsAttachment
    {
        ContentType = AttachmentContentTypes.AdaptiveCard,
        Content = JsonSerializer.Deserialize<JsonElement>(cardJson),
        Properties = new()
        {
            ["preview"] = new TeamsAttachment
            {
                ContentType = AttachmentContentTypes.ThumbnailCard,
                Content = JsonSerializer.Deserialize<JsonElement>(previewJson)
            }
        }
    };

    var response = MessageExtensionResponse.CreateBuilder()
        .WithType(MessageExtensionResponseTypes.Result)
        .WithAttachmentLayout(AttachmentLayoutType.List)
        .WithAttachments([attachment])
        .Build()
        .Body
        ?? throw new InvalidOperationException("The message extension response builder returned no body.");

    return Task.FromResult(response);
}
```

**Zero-install/anonymous link unfurling** allows Teams to call your agent even before the user installs the app. Use `[TeamsAnonQueryLinkRoute]`. The handler signature is identical. The agent can't send proactive messages or access member details in anonymous context.

```javascript
teams.messageExtensions
  .onQueryLink(async (context, state, query) => {
    const url = query?.url
    if (!url) {
      return {
        composeExtension: {
          type: 'message',
          text: 'No URL provided'
        }
      }
    }

    return {
      composeExtension: {
        attachmentLayout: 'list',
        type: 'result',
        attachments: [{
          contentType: 'application/vnd.microsoft.card.adaptive',
          content: {
            $schema: 'https://adaptivecards.io/schemas/adaptive-card.json',
            type: 'AdaptiveCard',
            version: '1.4',
            body: [
              { type: 'TextBlock', text: 'Link Preview', size: 'Medium', weight: 'Bolder' },
              { type: 'TextBlock', text: `URL: ${url}`, wrap: true, isSubtle: true },
              {
                type: 'TextBlock',
                text: 'This is a preview of the linked content generated by the message extension.',
                wrap: true,
                size: 'Small'
              }
            ]
          },
          preview: {
            contentType: 'application/vnd.microsoft.card.thumbnail',
            content: { title: 'Link Preview', text: url }
          }
        }]
      }
    }
  })
```

**Zero-install/anonymous link unfurling** allows Teams to call your agent before the user installs the app. Use `onAnonymousQueryLink`. The handler signature is identical.

The handler receives an `AppBasedLinkQuery`. Read the pasted URL from `query.url`:

```python
from microsoft_teams.api.models import (
    AppBasedLinkQuery,
    MessagingExtensionResponse,
    MessagingExtensionResult,
    MessagingExtensionResultType,
    MessagingExtensionAttachment,
    MessagingExtensionAttachmentLayout,
)

@teams.message_extensions.query_link
async def on_query_link(context, state, query: AppBasedLinkQuery) -> MessagingExtensionResponse:
    url = query.url or ""
    if not url:
        return MessagingExtensionResponse(
            compose_extension=MessagingExtensionResult(
                type=MessagingExtensionResultType.MESSAGE,
                text="No URL provided",
            )
        )

    card = {
        "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
        "type": "AdaptiveCard",
        "version": "1.4",
        "body": [
            {"type": "TextBlock", "text": "Link Preview", "size": "Medium", "weight": "Bolder"},
            {"type": "TextBlock", "text": f"URL: {url}", "isSubtle": True, "wrap": True},
            {
                "type": "TextBlock",
                "text": "This is a preview of the linked content generated by the message extension.",
                "wrap": True,
                "size": "Small",
            },
        ],
    }
    return MessagingExtensionResponse(
        compose_extension=MessagingExtensionResult(
            type=MessagingExtensionResultType.RESULT,
            attachment_layout=MessagingExtensionAttachmentLayout.LIST,
            attachments=[
                MessagingExtensionAttachment(
                    content_type="application/vnd.microsoft.card.adaptive",
                    content=card,
                    preview=MessagingExtensionAttachment(
                        content_type="application/vnd.microsoft.card.thumbnail",
                        content={"title": "Link Preview", "text": url},
                    ),
                )
            ],
        )
    )
```

**Zero-install/anonymous link unfurling** allows Teams to call your agent before the user installs the app. Use `@teams.message_extensions.anonymous_query_link` - the handler signature is identical.

## Message preview

When you configure a compose extension with `botMessagePreviewAction`, Teams shows the user a preview of the card before sending it.

```csharp
using Microsoft.Teams.Apps.MessageExtensions;
using Microsoft.Teams.Apps.Schema;
using System.Text.Json;

[TeamsMessagePreviewEditRoute("myCommand")]
public Task<MessageExtensionResponse> OnPreviewEditAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    MessageExtensionActivityPreview previewActivity,
    CancellationToken cancellationToken)
{
    const string editCardJson = """
    {
      "type": "AdaptiveCard",
      "version": "1.4",
      "body": [
        {
          "type": "TextBlock",
          "text": "Edit card",
          "size": "Large",
          "weight": "Bolder"
        }
      ]
    }
    """;

    var attachment = new TeamsAttachment
    {
        ContentType = AttachmentContentTypes.AdaptiveCard,
        Content = JsonSerializer.Deserialize<JsonElement>(editCardJson)
    };

    var response = MessageExtensionResponse.CreateBuilder()
        .WithType(MessageExtensionResponseTypes.Result)
        .WithAttachmentLayout(AttachmentLayoutType.List)
        .WithAttachments([attachment])
        .Build()
        .Body
        ?? throw new InvalidOperationException("The message extension response builder returned no body.");

    return Task.FromResult(response);
}

[TeamsMessagePreviewSendRoute("myCommand")]
public async Task OnPreviewSendAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    MessageExtensionActivityPreview previewActivity,
    CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync("Card sent!", cancellationToken: cancellationToken);
}
```

```javascript
import { Activity } from '@microsoft/agents-activity'
import { MessagingExtensionActionResponse } from '@microsoft/teams.api'

teams.messageExtensions
  .onMessagePreviewEdit('myCommand', async (context, state, activity) => {
    return {
      composeExtension: {
        type: 'result',
        attachmentLayout: 'list',
        attachments: [{
          contentType: 'application/vnd.microsoft.card.adaptive',
          content: {
            $schema: 'https://adaptivecards.io/schemas/adaptive-card.json',
            type: 'AdaptiveCard',
            version: '1.4',
            body: [
              {
                type: 'TextBlock',
                text: 'Edit card',
                size: 'Large',
                weight: 'Bolder'
              }
            ]
          }
        }]
      }
    }
  })
  .onMessagePreviewSend('myCommand', async (context, state, activity) => {
    await context.sendActivity('Card sent!')
  })
```

The preview handlers receive the parsed preview `Activity`. Use `message_preview_edit` to return an editable card and `message_preview_send` to send it:

```python
from microsoft_agents.activity import Activity
from microsoft_teams.api.models import (
    MessagingExtensionResponse,
    MessagingExtensionResult,
    MessagingExtensionResultType,
    MessagingExtensionAttachment,
    MessagingExtensionAttachmentLayout,
)

@teams.message_extensions.message_preview_edit("myCommand")
async def on_preview_edit(context, state, activity_preview: Activity) -> MessagingExtensionResponse:
    return MessagingExtensionResponse(
        compose_extension=MessagingExtensionResult(
            type=MessagingExtensionResultType.RESULT,
            attachment_layout=MessagingExtensionAttachmentLayout.LIST,
            attachments=[
                MessagingExtensionAttachment(
                    content_type="application/vnd.microsoft.card.adaptive",
                    content={
                        "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
                        "type": "AdaptiveCard",
                        "version": "1.4",
                        "body": [
                            {
                                "type": "TextBlock",
                                "text": "Edit card",
                                "size": "Large",
                                "weight": "Bolder",
                            }
                        ],
                    },
                )
            ],
        )
    )

@teams.message_extensions.message_preview_send("myCommand")
async def on_preview_send(context, state, activity_preview: Activity):
    await context.send_activity("Card sent!")
```

## Settings

Create a settings page that users can access through the gear icon in the message extension flyout.

```csharp
using Microsoft.Teams.Apps.MessageExtensions;
using Microsoft.Teams.Apps.Schema;

[TeamsQuerySettingUrlRoute]
public Task<MessageExtensionResponse> OnQuerySettingsUrlAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    var response = MessageExtensionResponse.CreateBuilder()
        .WithType(MessageExtensionResponseTypes.Config)
        .WithSuggestedActions(new Microsoft.Teams.Apps.Schema.SuggestedActions
        {
            Actions =
            [
                new SuggestedAction(
                    ActionType.OpenUrl,
                    "Configure",
                    "https://your-agent-host/settings")
            ]
        })
        .Build()
        .Body
        ?? throw new InvalidOperationException("The message extension response builder returned no body.");

    return Task.FromResult(response);
}

[TeamsSettingRoute]
public Task<MessageExtensionResponse> OnConfigureSettingsAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    MessageExtensionQuery settings,
    CancellationToken cancellationToken)
{
    // Persist settings.State or settings.Parameters as needed
    return Task.FromResult(new MessageExtensionResponse());
}
```

```javascript
import { MessagingExtensionResponse } from '@microsoft/teams.api'

teams.messageExtensions
  .onQuerySettingUrl(async (context, state) => {
    return {
      composeExtension: {
        type: 'config',
        suggestedActions: {
          actions: [{
            type: 'openUrl',
            value: 'https://your-agent-host/settings',
            title: 'Configure'
          }]
        }
      }
    }
  })
  .onSetting(async (context, state, settings) => {
    // Persist the user's settings
    console.log('Settings saved:', settings)
  })
```

Use `query_setting_url` to return the settings page URL and `setting` to apply the submitted settings:

```python
from microsoft_teams.api.models import (
    MessagingExtensionQuery,
    MessagingExtensionResponse,
    MessagingExtensionResult,
    MessagingExtensionResultType,
)

@teams.message_extensions.query_setting_url
async def on_query_settings_url(context, state, query: MessagingExtensionQuery) -> MessagingExtensionResponse:
    return MessagingExtensionResponse(
        compose_extension=MessagingExtensionResult(
            type=MessagingExtensionResultType.CONFIG,
            suggested_actions={
                "actions": [
                    {"type": "openUrl", "title": "Configure", "value": "https://your-agent-host/settings"}
                ]
            },
        )
    )

@teams.message_extensions.setting
async def on_configure_settings(context, state, query: MessagingExtensionQuery):
    # Persist query.state or query.parameters as needed
    return MessagingExtensionResponse()
```

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Use task modules](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-task-modules)
- [Collect feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback)
- [Handle files and file consent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-files)
- [Use Adaptive Cards in agents](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards)
