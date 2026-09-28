<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Use adaptive cards in agents

[Adaptive cards](https://adaptivecards.io/) are platform-neutral JSON documents that render as interactive user interface elements in supported channels. Use them to present structured information, collect input, and provide actions without building a separate web experience.

This article covers the adaptive card APIs in the .NET and JavaScript Agents SDKs. For Teams-specific dialogs that can contain an adaptive card or webpage, see [Task modules](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-task-modules).

Note

Adaptive card routing isn't currently available in the Python Agents SDK.

## Design a card

Use the [Adaptive Card Designer](https://adaptivecards.microsoft.com/designer.html) to create and preview the card JSON. Select a schema version supported by every channel where you plan to use the card.

The following card collects a project name and sends an `Action.Execute` request with the verb `createProject`:

```json
{
  "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.4",
  "body": [
    {
      "type": "TextBlock",
      "text": "Create a project",
      "weight": "Bolder",
      "size": "Medium"
    },
    {
      "type": "Input.Text",
      "id": "projectName",
      "label": "Project name",
      "isRequired": true
    }
  ],
  "actions": [
    {
      "type": "Action.Execute",
      "title": "Create",
      "verb": "createProject"
    }
  ]
}
```

## Send an adaptive card

Create an attachment with the `application/vnd.microsoft.card.adaptive` content type and send it as a message activity:

```csharp
using Microsoft.Agents.Builder;
using Microsoft.Agents.Builder.App;
using Microsoft.Agents.Builder.State;
using Microsoft.Agents.Core.Models;

public class CardAgent(AgentApplicationOptions options) : AgentApplication(options)
{
    public async Task SendProjectCardAsync(
        ITurnContext turnContext,
        ITurnState turnState,
        CancellationToken cancellationToken)
    {
        const string cardJson = """
        {
          "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
          "type": "AdaptiveCard",
          "version": "1.4",
          "body": [
            {
              "type": "Input.Text",
              "id": "projectName",
              "label": "Project name",
              "isRequired": true
            }
          ],
          "actions": [
            {
              "type": "Action.Execute",
              "title": "Create",
              "verb": "createProject"
            }
          ]
        }
        """;

        var attachment = new Attachment
        {
            ContentType = ContentTypes.AdaptiveCard,
            Content = cardJson
        };

        var activity = Activity.CreateMessageActivity()
            .AddAttachment(attachment);

        await turnContext.SendActivityAsync(
            activity,
            cancellationToken);
    }
}
```

You can also create the card with a card model library and assign the resulting object to `Attachment.Content`.

Create an Adaptive Card object, wrap it with `CardFactory.adaptiveCard`, and send the resulting attachment:

```javascript
import {
  AdaptiveCard,
  CardFactory,
  MessageFactory
} from '@microsoft/agents-hosting'

const card: AdaptiveCard = {
  $schema: 'https://adaptivecards.io/schemas/adaptive-card.json',
  type: 'AdaptiveCard',
  version: '1.4',
  body: [
    {
      type: 'Input.Text',
      id: 'projectName',
      label: 'Project name',
      isRequired: true
    }
  ],
  actions: [
    {
      type: 'Action.Execute',
      title: 'Create',
      verb: 'createProject'
    }
  ]
}

const attachment = CardFactory.adaptiveCard(card)
await context.sendActivity(MessageFactory.attachment(attachment))
```

## Handle `Action.Execute`

`AgentApplication` exposes Adaptive Card routing through its Adaptive Cards property.

Register a handler with `AdaptiveCards.OnActionExecute`, or use an `ActionExecuteRoute` attribute.

The following example uses an attribute to match the `createProject` verb:

```csharp
using Microsoft.Agents.Builder;
using Microsoft.Agents.Builder.App;
using Microsoft.Agents.Builder.App.AdaptiveCards;
using Microsoft.Agents.Builder.State;
using System.Text.Json;

public class CardAgent(AgentApplicationOptions options) : AgentApplication(options)
{
    [ActionExecuteRoute("createProject")]
    public Task<AdaptiveCardInvokeResponse> OnCreateProjectAsync(
        ITurnContext turnContext,
        ITurnState turnState,
        object data,
        CancellationToken cancellationToken)
    {
        var values = JsonSerializer.SerializeToElement(data);
        var projectName = values.TryGetProperty("projectName", out var name)
            ? name.GetString()
            : null;

        if (string.IsNullOrWhiteSpace(projectName))
        {
            return Task.FromResult(
                AdaptiveCardInvokeResponseFactory.BadRequest("Project name is required."));
        }

        return Task.FromResult(
            AdaptiveCardInvokeResponseFactory.Message(
                $"Project '{projectName}' was created."));
    }
}
```

An `Action.Execute` handler returns an `AdaptiveCardInvokeResponse`. Use `AdaptiveCardInvokeResponseFactory` to return a message, replacement card, sign-in card, search response, or error response.

To register the same route with the fluent API:

```csharp
AdaptiveCards.OnActionExecute(
    "createProject",
    OnCreateProjectAsync);
```

Register a handler with `app.adaptiveCards.actionExecute`. The handler can return a message string or an Adaptive Card:

```javascript
app.adaptiveCards.actionExecute(
  'createProject',
  async (context, state, data) => {
    const projectName = data.data?.projectName?.trim()

    if (!projectName) {
      return 'Project name is required.'
    }

    return `Project '${projectName}' was created.`
  }
)
```

## Handle `Action.Submit`

For clients that send `Action.Submit` as a message activity, include a route value in the action's `data` object:

```json
{
  "type": "Action.Submit",
  "title": "Save",
  "data": {
    "type": "Action.Submit",
    "id": "savePreferences",
    "verb": "savePreferences",
    "data": {}
  }
}
```

Handle the submission with an `ActionSubmitRoute`:

```csharp
[ActionSubmitRoute("savePreferences")]
public async Task OnSavePreferencesAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    object data,
    CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(
        "Your preferences were saved.",
        cancellationToken: cancellationToken);
}
```

The default route field is `verb`. You can change it with the `AgentApplication:AdaptiveCards:ActionSubmitFilter` configuration setting.

Handle the submission with `app.adaptiveCards.actionSubmit`:

```javascript
app.adaptiveCards.actionSubmit(
  'savePreferences',
  async (context, state, data) => {
    await context.sendActivity('Your preferences were saved.')
  }
)
```

The default route field is `verb`. You can change it with the `adaptiveCardsOptions.actionSubmitFilter` application option.

## Add dynamic search

Adaptive Card inputs can request choices from your agent as the user types. Set the input's `choices.data` dataset, and register a matching search route:

```json
{
  "type": "Input.ChoiceSet",
  "id": "package",
  "label": "Package",
  "choices.data": {
    "type": "Data.Query",
    "dataset": "packages"
  }
}
```

```csharp
[SearchRoute("packages")]
public Task<IList<AdaptiveCardsSearchResult>> SearchPackagesAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    Query<AdaptiveCardsSearchParams> query,
    CancellationToken cancellationToken)
{
    IList<AdaptiveCardsSearchResult> results =
    [
        new("Microsoft.Agents.Builder", "Microsoft.Agents.Builder"),
        new("Microsoft.Agents.Hosting.AspNetCore", "Microsoft.Agents.Hosting.AspNetCore")
    ];

    return Task.FromResult(results);
}
```

Filter results by using `query.Parameters.QueryText` before returning them. Keep the result set small enough for the client to display.

```javascript
app.adaptiveCards.search(
  'packages',
  async (context, state, query) => {
    const queryText = query.parameters.queryText.toLowerCase()
    const packages = [
      {
        title: 'Microsoft Agents hosting',
        value: '@microsoft/agents-hosting'
      },
      {
        title: 'Microsoft Agents hosting for Express',
        value: '@microsoft/agents-hosting-express'
      }
    ]

    return packages.filter((item) =>
      item.title.toLowerCase().includes(queryText) ||
      item.value.toLowerCase().includes(queryText)
    )
  }
)
```

Keep the result set small enough for the client to display.

## Require OAuth for a card route

Adaptive card route attributes and fluent methods accept OAuth handler names. Use this capability when an action needs a user token:

```csharp
[ActionExecuteRoute(
    "showProfile",
    autoSignInHandlers: "graph")]
public Task<AdaptiveCardInvokeResponse> OnShowProfileAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    object data,
    CancellationToken cancellationToken)
{
    // Retrieve the turn token and call the downstream service.
    return Task.FromResult(
        AdaptiveCardInvokeResponseFactory.Message("Profile loaded."));
}
```

For handler and Azure Bot OAuth connection configuration, see [Configure your agent to use OAuth](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-oauth-configuration).

The JavaScript adaptive card helper methods don't currently accept per-route authorization handlers. Use the application authorization APIs to acquire a user token when the handler calls a protected service.

For handler and Azure Bot OAuth connection configuration, see [Configure your agent to use OAuth](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-oauth-configuration).

## Channel-specific considerations

Adaptive card schema support, actions, and rendering can vary by channel and client. Test each card in every target channel and device form factor.

For Microsoft Teams:

- See [Introduction to cards and dialogs](https://learn.microsoft.com/en-us/microsoftteams/platform/task-modules-and-cards/cards-and-task-modules) for supported card types and Teams-specific behavior.
- Use the [Teams extension](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension) for task modules, message extensions, and other Teams-specific card experiences.
