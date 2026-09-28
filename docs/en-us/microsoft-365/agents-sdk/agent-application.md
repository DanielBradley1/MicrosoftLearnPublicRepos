<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-application -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# AgentApplication in Microsoft 365 Agents SDK

`AgentApplication` is the central building block of an agent built with the Agents SDK. `AgentApplication` is the entry point for all incoming activity, including messages from users, conversation lifecycle events, adaptive card interactions, OAuth callbacks.

An agent is, at its core, an `AgentApplication`. You configure it with handlers that describe what your agent does. The SDK takes care of routing, state management, and the infrastructure required to run it.

## How AgentApplication works

Every agent has a lifecycle that starts when a channel \(Microsoft Teams, a bot service, or a custom client\) delivers an activity to your agent's endpoint. `AgentApplication` sits at the center of that lifecycle:

`Channel → Hosting layer → AgentApplication → Your handlers`

The layers of processing in an agent built with the Agents SDK work as follows:

1. The hosting layer receives the HTTP request and authenticates it.
2. The `AgentApplication` processes the incoming activity through its pipeline.
3. Your handlers are called based on matching routes.

Your agent loads turn state before your handlers run. Afterward, the agent saves the turn state.

## Core concepts

### Activities

Everything in the Agents SDK flows as an *activity*. An activity is a structured message representing something that happened. An activity has a type, such as message, event, invoke, conversationUpdate, and so on. It carries a payload relevant to that type. `AgentApplication` receives activities and routes them to the right handler.

### Routes

A route pairs a *selector* with a *handler*. The selector determines whether a route matches the current activity. The handler runs your logic when the route matches.

Register routes when you configure your agent. They can match:

- A message containing specific text or matching a regular expression
- Any activity of a given type
- Conversation lifecycle events \(member added, member removed\)
- Adaptive card actions
- Custom conditions

When an activity arrives, the system evaluates routes in order until it finds a match. By default, only one route runs.

### Turn state

`AgentApplication` manages \_turn state—structured storage partitioned into scopes:

| Scope type | Description |
| --- | --- |
| Conversation | Shared across all users in a conversation, persisted between turns |
| User | Scoped to an individual user across all conversations |
| Temp | Current turn only - never persisted |

The system automatically loads state before your handlers run and saves it automatically afterward.

### Turn context

When a handler runs, it receives a *turn context*. Turn context is a snapshot of the current activity, the adapter connection, and utilities for sending responses. The turn context is your interface to the current interaction.

### Middleware

`AgentApplication` supports a *middleware pipeline*. Middleware is a chain of components that process each turn before and after your handlers run. Middleware can inspect, transform, or short-circuit the activity flow. Common uses include logging, authentication checks, and request normalization.

## Create an agent

- [C#](#tabpanel_1_csharp)
- [JavaScript](#tabpanel_1_javascript)
- [Python](#tabpanel_1_python)

Subclass `AgentApplication` and register your handlers in the constructor. The hosting framework automatically injects `AgentApplicationOptions`.

```csharp
public class MyAgent : AgentApplication
{
    public MyAgent(AgentApplicationOptions options) : base(options)
    {
        OnConversationUpdate(ConversationUpdateEvents.MembersAdded, WelcomeAsync);
        OnActivity(ActivityTypes.Message, OnMessageAsync, rank: RouteRank.Last);
    }

    private async Task WelcomeAsync(ITurnContext context, ITurnState state, CancellationToken ct)
    {
        foreach (var member in context.Activity.MembersAdded)
        {
            if (member.Id != context.Activity.Recipient.Id)
            {
                await context.SendActivityAsync("Hello! How can I help you?", cancellationToken: ct);
            }
        }
    }

    private async Task OnMessageAsync(ITurnContext context, ITurnState state, CancellationToken ct)
    {
        await context.SendActivityAsync($"You said: {context.Activity.Text}", cancellationToken: ct);
    }
}
```

Register your agent in `Program.cs`:

```csharp
WebApplicationBuilder builder = WebApplication.CreateBuilder(args);

builder.Services.AddHttpClient();
builder.Services.AddSingleton<IStorage, MemoryStorage>();
builder.Services.AddAgent<MyAgent>();
builder.Services.AddAgentAspNetAuthentication(builder.Configuration);

WebApplication app = builder.Build();

app.UseAuthentication();
app.UseAuthorization();
app.MapAgentApplicationEndpoints(requireAuth: !app.Environment.IsDevelopment());

app.Run();
```

Instantiate `AgentApplication` and register handlers on the instance by using the fluent API. To start the server, call `startServer` from the Express hosting package.

```typescript
import { AgentApplication, MemoryStorage, TurnContext, TurnState } from '@microsoft/agents-hosting'
import { startServer } from '@microsoft/agents-hosting-express'

const app = new AgentApplication<TurnState>({ storage: new MemoryStorage() })

app.onConversationUpdate('membersAdded', async (context: TurnContext) => {
    await context.sendActivity('Hello! How can I help you?')
})

app.onActivity('message', async (context: TurnContext, state: TurnState) => {
    await context.sendActivity(`You said: ${context.activity.text}`)
})

startServer(app)
```

For manual Express setup without `startServer`:

```typescript
import express from 'express'
import { CloudAdapter, authorizeJWT, AuthConfiguration } from '@microsoft/agents-hosting'

const authConfig: AuthConfiguration = loadAuthConfigFromEnv()
const adapter = new CloudAdapter(authConfig)
const expressApp = express()

expressApp.use(express.json())
expressApp.use(authorizeJWT(authConfig))

expressApp.post('/api/messages', async (req, res) => {
    await adapter.process(req, res, async (context) => {
        await app.run(context)
    })
})
```

Instantiate `AgentApplication` with a type parameter and register handlers by using decorators.

```python
from microsoft_agents.hosting.core import AgentApplication, TurnState, TurnContext, MemoryStorage
from microsoft_agents.hosting.aiohttp import CloudAdapter, start_agent_process
from aiohttp.web import Request, Response, Application, run_app

AGENT_APP = AgentApplication[TurnState](
    storage=MemoryStorage(),
    adapter=CloudAdapter()
)

@AGENT_APP.conversation_update("membersAdded")
async def on_members_added(context: TurnContext, state: TurnState):
    await context.send_activity("Hello! How can I help you?")

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, state: TurnState):
    await context.send_activity(f"You said: {context.activity.text}")

if __name__ == "__main__":
    async def messages(req: Request) -> Response:
        return await start_agent_process(req, AGENT_APP, AGENT_APP.adapter)

    app = Application()
    app.router.add_post("/api/messages", messages)
    app["agent_app"] = AGENT_APP
    app["adapter"] = AGENT_APP.adapter
    run_app(app, host="localhost", port=3978)
```

## Register activity handlers

### Handle messages

Match messages by exact text \(case-insensitive\):

- [C#](#tabpanel_2_csharp)
- [JavaScript](#tabpanel_2_javascript)
- [Python](#tabpanel_2_python)

```csharp
OnMessage("help", async (context, state, ct) =>
{
    await context.SendActivityAsync("Here's what I can do...", cancellationToken: ct);
});
```

Match messages using a regular expression:

```csharp
OnMessage(new Regex(@"^order\s+\d+$", RegexOptions.IgnoreCase), async (context, state, ct) =>
{
    await context.SendActivityAsync("Looking up your order...", cancellationToken: ct);
});
```

```typescript
app.onMessage('help', async (context: TurnContext, state: TurnState) => {
    await context.sendActivity("Here's what I can do...")
})
```

Match messages using a regular expression:

```typescript
app.onMessage(/^order\s+\d+$/i, async (context: TurnContext, state: TurnState) => {
    await context.sendActivity('Looking up your order...')
})
```

```python
@AGENT_APP.message("/help")
async def on_help(context: TurnContext, state: TurnState):
    await context.send_activity("Here's what I can do...")
```

Match messages using a regular expression:

```python
import re

@AGENT_APP.message(re.compile(r"^order\s+\d+$", re.IGNORECASE))
async def on_order(context: TurnContext, state: TurnState):
    await context.send_activity("Looking up your order...")
```

### Handle conversation updates

Register handlers for conversation lifecycle events such as members joining or leaving.

- [C#](#tabpanel_3_csharp)
- [JavaScript](#tabpanel_3_javascript)
- [Python](#tabpanel_3_python)

```csharp
OnConversationUpdate(ConversationUpdateEvents.MembersAdded, async (context, state, ct) =>
{
    foreach (var member in context.Activity.MembersAdded)
    {
        if (member.Id != context.Activity.Recipient.Id)
        {
            await context.SendActivityAsync("Welcome!", cancellationToken: ct);
        }
    }
});

OnConversationUpdate(ConversationUpdateEvents.MembersRemoved, async (context, state, ct) =>
{
    // Called when participants leave the conversation
});
```

```typescript
app.onConversationUpdate('membersAdded', async (context: TurnContext) => {
    for (const member of context.activity.membersAdded ?? []) {
        if (member.id !== context.activity.recipient.id) {
            await context.sendActivity('Welcome!')
        }
    }
})

app.onConversationUpdate('membersRemoved', async (context: TurnContext) => {
    // Called when participants leave the conversation
})
```

```python
@AGENT_APP.conversation_update("membersAdded")
async def on_members_added(context: TurnContext, state: TurnState):
    for member in context.activity.members_added or []:
        if member.id != context.activity.recipient.id:
            await context.send_activity("Welcome!")

@AGENT_APP.conversation_update("membersRemoved")
async def on_members_removed(context: TurnContext, state: TurnState):
    pass  # Called when participants leave the conversation
```

### Handle any activity type

Match any activity by its type string for complete control over routing.

- [C#](#tabpanel_4_csharp)
- [JavaScript](#tabpanel_4_javascript)
- [Python](#tabpanel_4_python)

```csharp
OnActivity(ActivityTypes.Message, async (context, state, ct) =>
{
    // Handles all message activities
});

OnActivity(ActivityTypes.Event, async (context, state, ct) =>
{
    // Handles event activities
});
```

Use `ActivityTypes` constants instead of hard-coded strings.

```typescript
app.onActivity('message', async (context: TurnContext, state: TurnState) => {
    // Handles all message activities
})

app.onActivity('event', async (context: TurnContext, state: TurnState) => {
    // Handles event activities
})
```

```python
@AGENT_APP.activity("message")
async def on_message(context: TurnContext, state: TurnState):
    pass  # Handles all message activities

@AGENT_APP.activity("event")
async def on_event(context: TurnContext, state: TurnState):
    pass  # Handles event activities
```

## Control route evaluation order

The system sorts routes into a fixed evaluation order when you register them, not at runtime. The sort uses two levels:

1. **Route type**: The system groups routes by type, and it always evaluates higher-priority types before lower-priority types, regardless of rank:
   | Priority | Route type |
   | --- | --- |
   | 1 \(highest\) | Agentic invoke routes |
   | 2 | Invoke routes \(adaptive card actions, OAuth callbacks, and other time-sensitive invokes\) |
   | 3 | Agentic routes |
   | 4 \(lowest\) | All other routes |
2. **Rank**: Within each route type group, the system orders routes by their rank value. Lower numeric values are evaluated first.

Use `RouteRank` constants to set rank when registering a handler:

| Constant | Value | Meaning |
| --- | --- | --- |
| `RouteRank.First` | `0` | Evaluated before all other routes in its group |
| `RouteRank.Unspecified` | `32767` | Default when no rank is specified |
| `RouteRank.Last` | `65535` | Evaluated after all other routes in its group |

By default, evaluation stops at the first matching route. Use `RouteRank.Last` for a catch-all fallback that handles anything not matched by a more specific route.

- [C#](#tabpanel_5_csharp)
- [JavaScript](#tabpanel_5_javascript)
- [Python](#tabpanel_5_python)

```csharp
// Specific handlers use the default rank
OnMessage("status", HandleStatusAsync);
OnMessage("help", HandleHelpAsync);

// Catch-all — handles anything not matched above
OnActivity(ActivityTypes.Message, HandleUnknownMessageAsync, rank: RouteRank.Last);
```

```typescript
// Specific handlers use the default rank
app.onMessage('status', handleStatusAsync)
app.onMessage('help', handleHelpAsync)

// Catch-all — handles anything not matched above
app.onActivity('message', handleUnknownMessageAsync, RouteRank.Last)
```

```python
@AGENT_APP.message("/status")
async def on_status(context: TurnContext, state: TurnState):
    await context.send_activity("Status: OK")

@AGENT_APP.message("/help")
async def on_help(context: TurnContext, state: TurnState):
    await context.send_activity("Here's what I can do...")

# Catch-all — handles anything not matched above (registered last)
@AGENT_APP.activity("message")
async def on_unknown(context: TurnContext, state: TurnState):
    await context.send_activity("I didn't understand that. Type /help for options.")
```

## Turn lifecycle hooks

Register logic that runs on every turn, before or after route matching. These hooks are useful for logging, cross-cutting concerns, and error handling.

- [C#](#tabpanel_6_csharp)
- [JavaScript](#tabpanel_6_javascript)
- [Python](#tabpanel_6_python)

```csharp
OnBeforeTurn(async (context, state, ct) =>
{
    logger.LogInformation("Turn started: {Type}", context.Activity.Type);
    return true; // Return false to abort the turn
});

OnAfterTurn(async (context, state, ct) =>
{
    logger.LogInformation("Turn completed");
    return true; // Return false to skip state saving
});

OnTurnError(async (context, state, exception, ct) =>
{
    logger.LogError(exception, "Turn error");
    await context.SendActivityAsync("Something went wrong. Please try again.", cancellationToken: ct);
});
```

When `OnBeforeTurn` returns `false`, the turn is aborted and no routes run. When `OnAfterTurn` returns `false`, turn state isn't saved.

```typescript
app.beforeTurn(async (context: TurnContext, state: TurnState) => {
    console.log(`Turn started: ${context.activity.type}`)
    return true // Return false to abort the turn
})

app.afterTurn(async (context: TurnContext, state: TurnState) => {
    console.log('Turn completed')
    return true // Return false to skip state saving
})

app.onError(async (context: TurnContext, error: Error) => {
    console.error('Turn error:', error)
    await context.sendActivity('Something went wrong. Please try again.')
})
```

```python
@AGENT_APP.before_turn
async def on_before_turn(context: TurnContext, state: TurnState) -> bool:
    print(f"Turn started: {context.activity.type}")
    return True  # Return False to abort the turn

@AGENT_APP.after_turn
async def on_after_turn(context: TurnContext, state: TurnState) -> bool:
    print("Turn completed")
    return True  # Return False to skip state saving

@AGENT_APP.turn_error
async def on_turn_error(context: TurnContext, state: TurnState, error: Exception):
    print(f"Turn error: {error}")
    await context.send_activity("Something went wrong. Please try again.")
```

## Use turn state

The agent automatically loads turn state before your handlers run and saves it afterward. The turn state object passed to your handlers gives you access to the different scopes so you can read and write data that persists across turns or is ephemeral for the current turn:

- **Conversation scope**: For data shared across all turns in a conversation
- **User scope**: For per-user data
- **Temp scope**: For data that only needs to exist during the current turn

- [C#](#tabpanel_7_csharp)
- [JavaScript](#tabpanel_7_javascript)
- [Python](#tabpanel_7_python)

```csharp
OnActivity(ActivityTypes.Message, async (context, state, ct) =>
{
    // Conversation scope — persisted per conversation
    var count = state.Conversation.GetValue<int>("messageCount", () => 0);
    state.Conversation.SetValue("messageCount", count + 1);

    // User scope — persisted per user
    var name = state.User.GetValue<string>("displayName");

    // Temp scope — current turn only
    state.Temp.SetValue("parsedInput", context.Activity.Text?.Trim());

    await context.SendActivityAsync($"Message #{count + 1}: {context.Activity.Text}", cancellationToken: ct);
});
```

```typescript
app.onActivity('message', async (context: TurnContext, state: TurnState) => {
    // Conversation scope — persisted per conversation
    let count: number = state.getValue('conversation.messageCount') ?? 0
    state.setValue('conversation.messageCount', count + 1)

    // User scope — persisted per user
    const name: string = state.getValue('user.displayName')

    await context.sendActivity(`Message #${count + 1}: ${context.activity.text}`)
})
```

```python
@AGENT_APP.activity("message")
async def on_message(context: TurnContext, state: TurnState):
    # Conversation scope — persisted per conversation
    count = state.get_value("conversation.message_count") or 0
    state.set_value("conversation.message_count", count + 1)

    # User scope — persisted per user
    name = state.get_value("user.display_name")

    await context.send_activity(f"Message #{count + 1}: {context.activity.text}")
```

Note

Use `MemoryStorage` for local development and testing. For production deployments, especially deployments running on multiple instances, use a persistent storage provider such as Azure Cosmos DB or Azure Blob Storage. See [Use storage providers in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/storage).

## Next steps

- [Manage state in Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/state-concepts)
- [Use storage providers in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/storage)
