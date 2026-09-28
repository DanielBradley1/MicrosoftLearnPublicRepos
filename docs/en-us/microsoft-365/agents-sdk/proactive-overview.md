<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/proactive-overview -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Proactive messaging in the Agents SDK

## What is proactive messaging?

Most agent interactions are *reactive*—a user sends a message, and the agent responds. *Proactive* messaging inverts this pattern. The *agent* initiates contact with a user or resumes a conversation without waiting for an incoming message.

This pattern unlocks a fundamental category of agent behaviors that request/response alone can't achieve.

## Two core operations

Proactive messaging relies on two core operations:

- Continue an existing conversation
- Create \(initiate\) a new conversation

### Continue

**Continue** resumes an existing conversation. The agent must know where to send the message, including the user, the channel, and the service. The agent needs a conversation object that it previously captured during a reactive turn. That conversation must persist beyond the turn that created it. The agent needs to store the conversation object somewhere before it can use it later.

### Create

**Create** starts a brand-new conversation with a user who never spoke to the agent. The agent doesn't need a prior conversation. The agent constructs the destination from known information \(tenant ID, user ID, channel\). If the agent wants to continue that conversation proactively in the future, it needs to keep the conversation returned when it's created.

## Storing conversations

Because continuing a conversation requires information that only exists during a live turn, you must preserve that information beyond the turn that captured it. Two approaches exist for preserving this information:

- **Use the SDK's built-in conversation store**: The SDK can persist the conversation during a reactive turn and return an identifier your code can use later to continue the conversation or send activities.
- **Manage storage yourself**: Capture the conversation from the current turn and serialize it to any store you control. Pass it back to the SDK to continue or send operations directly when needed.

Either way, persistent storage \(Azure Cosmos DB, Blob Storage\) is required in production. In-memory storage works for development only.

## Two trigger patterns

### Internal trigger

The agent queues a background task inside the same process. When the work finishes, the background task uses the captured conversation to resume contact with the user. No external service is involved.

Typical flow:

1. The user sends a request. The agent captures the conversation and queues a background task.
2. A background task completes.
3. The task uses the conversation to send a message or continue the conversation.

### External trigger

The agent delegates work to an external service. When that service finishes, it calls back to the agent by some mechanism \(HTTP, Service Bus, and so on\). The Agents SDK can optionally expose HTTP endpoints that map directly to specific continuation handlers, making it straightforward for external services to trigger the right logic.

Typical flow:

1. The user sends a request. The agent sends the conversation and task details to an external service.
2. An external service completes its work.
3. An external service calls the agent's proactive HTTP endpoint with the result.
4. The agent runs the appropriate continuation handler and responds to the user.

## What the proactive module provides

| Capability | Description |
| --- | --- |
| **Send activity** | Sends a single message to an existing conversation without invoking the full routing pipeline. |
| **Continue conversation** | Runs a handler inside the conversation context, with access to turn state, middleware, and OAuth tokens. |
| **Create conversation** | Creates a brand-new conversation and optionally continues it immediately. |
| **Conversation storage** | Persist and retrieve conversations by ID using the SDK's built-in store. |
| **HTTP endpoints** \(optional\) | Expose proactive endpoints so external services can trigger send, continue, or create operations over HTTP. |

## Examples

Proactive messaging lets your agent send messages or run logic in an existing conversation without waiting for the user to speak first. Common uses include notifications, reminders, background job results, and any scenario where an external event needs to reach a user.

`AgentApplication.Proactive` provides this surface. It's available only to agents built on `AgentApplication` \(not `ActivityHandler`\).

## Concepts

### Conversation

Before you can send a proactive message, you need to know *which conversation* to target. A `Conversation` object holds a `ConversationReference` \(including channel, service URL, and user ID\) plus the JSON Web Token \(JWT\) claims needed to authenticate the outbound call.

You acquire a `Conversation` in one of two ways:

| Approach | When to use |
| --- | --- |
| Store it during a normal turn with `Proactive.StoreConversationAsync` | The user speaks to your agent and you want to reach them later |
| Build one with `ConversationBuilder`, or receive one via HTTP | An external system supplies the reference, or you're creating a new conversation |

### Three proactive operations

| Operation | What it does |
| --- | --- |
| SendActivity | Sends a single `IActivity` to a conversation. No `TurnState`, no route handlers, just a fire-and-forget message. |
| ContinueConversation | Runs a `RouteHandler` delegate inside the conversation context, giving full `ITurnContext`, `ITurnState`, middleware, and optional OAuth tokens. |
| CreateConversation | Asks the channel to create a brand-new conversation, then optionally continues it immediately. |

## Setup

### 1. Verify storage is registered

Proactive messaging requires persistent storage so that conversation references survive agent restarts. Use `MemoryStorage` in development and a durable store like Azure Cosmos DB or blob storage in production.

Here's an example of how it works in `Program.cs`:

```csharp
builder.AddAgentApplicationOptions();   // reads AgentApplicationOptions from config
builder.AddAgent<MyAgent>();

// IStorage is used by both TurnState and Proactive
builder.Services.AddSingleton<IStorage, MemoryStorage>();

builder.Services.AddAgentAspNetAuthentication(builder.Configuration);
```

`AgentApplicationOptions` automatically wires `ProactiveOptions` from the `Proactive` config section when `IStorage` is registered in DI.

### 2. \(Optional\) Map HTTP endpoints

If external systems need to trigger proactive actions over HTTP, add `MapAgentProactiveEndpoints` after `MapAgentApplicationEndpoints`:

```csharp
app.MapAgentApplicationEndpoints();

// Exposes /proactive/sendactivity, /proactive/continue, /proactive/create
app.MapAgentProactiveEndpoints<MyAgent>();
```

See [Triggering proactive actions over HTTP](#triggering-proactive-actions-over-http) for the full endpoint reference.

## Scenario 1: Send a simple proactive message

### Step 1: Store the conversation

During any normal turn, call `StoreConversationAsync` to persist the conversation for later:

```csharp
public class MyAgent : AgentApplication
{
    public MyAgent(AgentApplicationOptions options) : base(options)
    {
        OnMessage("/subscribe", async (ctx, state, ct) =>
        {
            string conversationId = await Proactive.StoreConversationAsync(ctx, ct);
            await ctx.SendActivityAsync(
                $"You're subscribed! Conversation ID: {conversationId}",
                cancellationToken: ct);
        });
    }
}
```

Note

`StoreConversationAsync` returns the conversation's ID string. Use this ID later to continue the conversation.

### Step 2: Send the message later

When the external event arrives \(a webhook, a background job, a timer\), use the stored ID:

```csharp
// adapter and agent.Proactive resolved via DI / the host
await agent.Proactive.SendActivityAsync(
    adapter,
    conversationId,
    MessageFactory.Text("Your report is ready!"),
    cancellationToken);
```

## Scenario 2: Continue a conversation with full agent logic

`ContinueConversationAsync` runs a handler inside the full `AgentApplication` pipeline, giving the handler access to `ITurnState`, middleware, streaming responses, and cached OAuth tokens.

### Define continuation handlers with `[ContinueConversation]`

Decorate a method with `[ContinueConversationAttribute]` to mark it as a proactive handler. The optional `key` distinguishes multiple handlers on the same agent, and `autoSignInHandlers` names the OAuth connections that must be signed in before the handler runs:

```csharp
public class MyAgent : AgentApplication
{
    public MyAgent(AgentApplicationOptions options) : base(options) { }

    // Default handler, no key, reachable via code or POST /proactive/continue/{conversationId}
    [ContinueConversation(autoSignInHandlers: "graph")]
    public async Task OnDailyReminderAsync(
        ITurnContext turnContext,
        ITurnState turnState,
        CancellationToken cancellationToken)
    {
        // TurnState is fully available
        var lastSeen = turnState.User.Get<DateTime>("lastSeen");

        // OAuth token available because "graph" is listed in autoSignInHandlers
        var token = await turnContext.GetTurnTokenAsync(cancellationToken: cancellationToken);

        await turnContext.SendActivityAsync(
            $"Daily reminder, you last visited on {lastSeen:d}.",
            cancellationToken: cancellationToken);

        turnState.User.Set("lastReminderSent", DateTime.UtcNow);
    }

    // Named handler, POST /proactive/continue/report/{conversationId}
    [ContinueConversation("report")]
    public async Task OnReportReadyAsync(
        ITurnContext turnContext,
        ITurnState turnState,
        CancellationToken cancellationToken)
    {
        await turnContext.SendActivityAsync(
            "Your scheduled report is ready. Check your email.",
            cancellationToken: cancellationToken);
    }
}
```

### Invoke from code

Pass the decorated method to `ContinueConversationAsync`. The OAuth handler names are read automatically from the attribute:

```csharp
// Token handlers ("graph") are picked up from the [ContinueConversation] attribute
await Proactive.ContinueConversationAsync(
    adapter,
    conversationId,
    OnDailyReminderAsync,
    cancellationToken: ct);
```

You can also override them at the call site:

```csharp
await Proactive.ContinueConversationAsync(
    adapter,
    conversationId,
    OnDailyReminderAsync,
    autoSignInHandlers: ["graph", "sharepoint"],
    cancellationToken: ct);
```

### Pass custom data to the handler

Use a custom `continuationActivity` to carry a payload in via `turnContext.Activity.Value`:

```csharp
var continuation = conversation.Reference.GetContinuationActivity();
continuation.Value = new { ReportId = 42, Title = "Q1 Summary" };

await Proactive.ContinueConversationAsync(
    adapter,
    conversation,
    async (ctx, state, ct) =>
    {
        dynamic data = ctx.Activity.Value;
        await ctx.SendActivityAsync(
            $"Report #{data.ReportId} '{data.Title}' is ready.",
            cancellationToken: ct);
    },
    continuationActivity: continuation,
    cancellationToken: ct);
```

## Scenario 3: Create a new conversation

Use `CreateConversationAsync` when the user never spoke to your agent and you need to reach them directly, for example, to send an onboarding message or open a Teams chat.

### Build the options

```csharp
var createOptions = CreateConversationOptionsBuilder
    .Create("your-agent-clientId", channelId: Channels.Msteams)
    .WithTenantId("your-tenant-id")
    .WithUser(userId: "aad-user-object-id")
    .WithTopicName("Welcome to Contoso Agent")
    .WithActivity(MessageFactory.Text("Hi! I'm here to help you get started."))
    .Build();
```

### Create only

Create a new conversation and persist the returned ID for future proactive messages:

```csharp
Conversation newConversation = await Proactive.CreateConversationAsync(
    adapter, createOptions, cancellationToken: ct);

// Persist the new ID for future proactive messages
string newConversationId = newConversation.Reference.Conversation.Id;
```

### Create and immediately continue

To run agent logic right after the conversation is created, supply a handler. The handler is called with a "CreateConversation" event activity:

```csharp
[ContinueConversation]
public async Task OnNewConversationAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(
        "Welcome! Here is what I can do for you...",
        cancellationToken: cancellationToken);
}

// Create then immediately run OnNewConversationAsync
var newConversation = await Proactive.CreateConversationAsync(
    adapter,
    createOptions,
    continuationHandler: OnNewConversationAsync,
    cancellationToken: ct);
```

Note

If `WithActivity(...)` and a `continuationHandler` are both specified, the channel receives the initial activity first, then the handler is invoked.

### Autostore the new conversation

Call `WithStoreConversation(true)` to automatically persist the reference:

```csharp
var createOptions = CreateConversationOptionsBuilder
    .Create("your-bot-app-id", Channels.Msteams)
    .WithTenantId("your-tenant-id")
    .WithUser("user-id")
    .WithStoreConversation(true)
    .Build();

var conv = await Proactive.CreateConversationAsync(adapter, createOptions, ct);
// conv.Reference.Conversation.Id can now be used directly with SendActivityAsync using the conversationId
```

## Scenario 4: Long-running external task

Use this pattern when the user requests an operation that takes an extended amount of time, with an external service performing the work.

Here's the basic flow:

1. User asks the agent to start a long-running job.
2. Agent captures the conversation and sends it, along with task details, to the external service.
3. The external service does the work, then calls back to the agent over HTTP with the result and the original `Conversation`.
4. Agent runs its `[ContinueConversation]` handler and delivers the result.

```csharp
public class MyAgent : AgentApplication
{
    public MyAgent(AgentApplicationOptions options) : base(options)
    {
        OnMessage("analyze", async (turnContext, turnState, cancellationToken) =>
        {
            var conversation = new Conversation(turnContext);

            // Send task + conversation to the external service
            await _externalService.SubmitJobAsync(new
            {
                DocumentId = turnContext.Activity.Text,
                Conversation = conversation.ToJson(),
                CallbackUrl = "https://myagent.example.com/proactive/continue/analysis"
            }, cancellationToken);

            await turnContext.SendActivityAsync(
                "Analysis started. I'll notify you when it's done.",
                cancellationToken: cancellationToken);
        });
    }

    // External service calls POST /proactive/continue/analysis
    // with the result in the request body, which arrives as turnContext.Activity.Value.
    [ContinueConversation("analysis")]
    public async Task OnAnalysisCompleteAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        dynamic result = turnContext.Activity.Value;
        await turnContext.SendActivityAsync(
            $"Analysis complete: {result.Summary}",
            cancellationToken: cancellationToken);
    }
}
```

Note

For the external callback to work, you must call `MapAgentProactiveEndpoints<MyAgent>()` in `Program.cs`. See [Triggering proactive actions over HTTP](#triggering-proactive-actions-over-http).

## Scenario 5: Background task

Use `IBackgroundTaskQueue` when the work happens inside the same process as the agent. This is a hosted service provided by `Microsoft.Agents.Hosting.AspNetCore`.

Inject `IBackgroundTaskQueue` into the agent and capture the `Conversation` before the turn ends. The turn context isn't valid after the turn completes:

```csharp
public class MyAgent : AgentApplication
{
    private readonly IBackgroundTaskQueue _backgroundTaskQueue;

    public MyAgent(AgentApplicationOptions options, IBackgroundTaskQueue backgroundTaskQueue)
        : base(options)
    {
        _backgroundTaskQueue = backgroundTaskQueue;

        OnMessage("process", OnProcessRequestAsync);
    }

    private Task OnProcessRequestAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        // Capture conversation before the turn ends. Do not close over turnContext.
        var conversation = new Conversation(turnContext);
        var adapter = turnContext.Adapter;

        _backgroundTaskQueue.QueueBackgroundWorkItem(async ct =>
        {
            // Perform the long-running work
            await Task.Delay(TimeSpan.FromSeconds(5), ct);

            // Send a simple message back to the user
            await Proactive.SendActivityAsync(
                adapter,
                conversation,
                MessageFactory.Text("Processing complete!"),
                ct);
        });

        return turnContext.SendActivityAsync(
            "Working on it. I'll let you know when it's done.",
            cancellationToken: cancellationToken);
    }
}
```

Note

Capture `turnContext.Adapter` and `new Conversation(turnContext)` *before* the lambda, not inside it. The `ITurnContext` is disposed after the turn completes and isn't safe to use in a background thread.

## Context inside ContinueConversation handlers

A `ContinueConversation` handler receives a fully initialized turn context scoped to the original conversation. This context means:

- **`TurnState`** loads relative to the original conversation and user, the same state the user's reactive turns see.
- **OAuth tokens** obtained during prior reactive turns are available if their connection names are listed in `autoSignInHandlers`. If any listed connection isn't signed in, `ContinueConversationAsync` throws `UserNotSignedIn` by default \(configurable via `ProactiveOptions.FailOnUnsignedInConnections`\).
- The handler **automatically saves** state after it completes, as in a reactive turn.

```csharp
[ContinueConversation(autoSignInHandlers: "graph")]
public async Task OnProactiveAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
{
    // User-scoped state from prior turns is available
    var name = turnState.User.Get<string>("preferredName");

    // Token for "graph" was previously acquired during a reactive sign-in turn
    var token = await turnContext.GetTurnTokenAsync(cancellationToken: cancellationToken);

    await turnContext.SendActivityAsync(
        $"Hi {name}, here is your update...",
        cancellationToken: cancellationToken);

    // State changes are persisted after the handler returns
    turnState.User.Set("lastNotified", DateTime.UtcNow);
}
```

## Multiple ContinueConversation handlers

An agent can define multiple `[ContinueConversation]` handlers, each identified by an optional key. Each handler has its own HTTP endpoint when `MapAgentProactiveEndpoints` is enabled.

```csharp
// Default handler, POST /proactive/continue OR /proactive/continue/{conversationId}
[ContinueConversation(autoSignInHandlers: "graph")]
public async Task OnContinueConversationAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    var graphToken = await turnContext.GetTurnTokenAsync("graph");
    // ...
}

// Named handler, POST /proactive/continue/notify OR /proactive/continue/notify/{conversationId}
[ContinueConversation("notify")]
public async Task OnNotifyAsync(
    ITurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    // ...
}
```

Invoke a specific handler from code by passing its method reference. The `autoSignInHandlers` from the attribute are picked up automatically:

```csharp
// Invokes the default handler; picks up autoSignInHandlers: "graph"
await Proactive.ContinueConversationAsync(
    adapter, conversationId, OnContinueConversationAsync, cancellationToken: ct);

// Invokes the named handler
await Proactive.ContinueConversationAsync(
    adapter, conversationId, OnNotifyAsync, cancellationToken: ct);
```

## Triggering proactive actions over HTTP

After you call `MapAgentProactiveEndpoints<MyAgent>()`, the following endpoints are available. They require the same authentication as `/api/messages` unless you pass `requireAuth: false` to `MapAgentProactiveEndpoints`.

Each operation comes in **two variants** depending on whether the conversation was previously stored in the SDK's built-in store:

| Variant | How the conversation is identified |
| --- | --- |
| **By stored ID** | The conversation was saved with `StoreConversationAsync`. Supply the returned ID in the URL path. |
| **By inline `Conversation`** | The full `Conversation` object is supplied in the request body. No prior storage required. |

### Send an activity by stored ID

Request:

```http
POST /proactive/sendactivity/{conversationId}
```

Request body, an `IActivity`:

```json
{
  "type": "message",
  "text": "Your job finished successfully."
}
```

Response `200`:

```json
{ "id": "activity-id" }
```

### Send an activity by inline conversation

Request:

```http
POST /proactive/sendactivity
```

Request body, a `Conversation` object plus the activity to send:

```json
{
  "conversation": {
    "reference": {
      "channelId": "msteams",
      "serviceUrl": "https://smba.trafficmanager.net/amer/",
      "bot":          { "id": "your-bot-app-id" },
      "user":         { "id": "29:user-aad-object-id" },
      "conversation": { "id": "a:conv-id", "isGroup": false }
    },
    "claims": {
      "aud": "your-bot-app-id",
      "tid": "your-tenant-id"
    }
  },
  "activity": {
    "type": "message",
    "text": "Your job finished successfully."
  }
}
```

Response `200`:

```json
{ "id": "activity-id" }
```

### Continue a conversation by stored ID

For each `[ContinueConversation]` handler, register two endpoints - one for each variant. If query string parameters are present, forward them to the handler as `turnContext.Activity.Value` \(a key/value dictionary\) with `turnContext.Activity.ValueType` set to `Proactive.ContinueConversationValueType`.

Default handler \(`[ContinueConversation]`\):

```http
POST /proactive/continue/{conversationId}
POST /proactive/continue/{conversationId}?result=success&jobId=42
```

Named handler \(`[ContinueConversation("report")]`\):

```http
POST /proactive/continue/report/{conversationId}
```

No request body is required or read. Response `200` has no body.

### Continue a conversation by inline `Conversation`

Default handler:

```http
POST /proactive/continue
```

Named handler:

```http
POST /proactive/continue/report
```

Body, the `Conversation` object:

```json
{
  "reference": {
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "bot":          { "id": "your-bot-app-id" },
    "user":         { "id": "29:user-aad-object-id" },
    "conversation": { "id": "a:conv-id", "isGroup": false }
  },
  "claims": {
    "aud": "your-bot-app-id",
    "tid": "your-tenant-id"
  }
}
```

Forward query string parameters in the same way as the by-ID variant. Response `200` has no body.

### Create a new conversation

Create doesn't have a by-ID variant. The conversation doesn't exist yet.

Default handler:

```http
POST /proactive/create
```

Named handler:

```http
POST /proactive/create/onboarding
```

Request body:

```json
{
  "agentClientId":    "your-bot-app-id",
  "channelId":        "msteams",
  "tenantId":         "your-tenant-id",
  "user":             { "id": "aad-user-object-id" },
  "topicName":        "Proactive Chat",
  "activity":         { "type": "message", "text": "Hello from the server!" },
  "teamsChannelId":   null,
  "channelData":      null,
  "isGroup":          null,
  "storeConversation":    false,
  "continueConversation": false
}
```

Request body parameter descriptions:

| Field | Required | Description |
| --- | --- | --- |
| `channelId` | Yes | Target channel \(for example, `"msteams"`, `"webchat"`\). |
| `user` | Yes | The target user. For Teams, use the Microsoft Entra ID object ID. |
| `agentClientId` | No | The agent's app \(client\) ID. If omitted, the authenticated caller's identity is used. |
| `tenantId` | No | Required for Teams. |
| `topicName` | No | Conversation topic/display name. |
| `activity` | No | Initial activity sent at conversation creation time. |
| `teamsChannelId` | No | Teams channel ID \(`19:...@thread.tacv2`\) to post into a specific channel. |
| `channelData` | No | Channel-specific data passed to the channel. |
| `isGroup` | No | Overrides the group conversation flag. Inferred automatically when `teamsChannelId` is set. |
| `storeConversation` | No | `true` to persist the new conversation in the SDK store. Defaults to `false`. |
| `continueConversation` | No | `true` to invoke the matching `[ContinueConversation]` handler immediately after creation. Defaults to `false`. |

Query string parameters, if present, are forwarded to the continuation handler the same way as the `continue` endpoints.

Response `200` returns the newly created `Conversation` object:

```json
{
  "reference": {
    "channelId": "msteams",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "bot":          { "id": "your-bot-app-id" },
    "user":         { "id": "29:user-aad-object-id" },
    "conversation": { "id": "a:new-conv-id", "isGroup": false }
  },
  "claims": {
    "aud": "your-bot-app-id",
    "tid": "your-tenant-id"
  }
}
```

## OAuth and sign-in in proactive contexts

When you specify `autoSignInHandlers`, `ContinueConversationAsync` checks whether each listed OAuth connection is already signed in before it invokes the handler. `ProactiveOptions.FailOnUnsignedInConnections` controls the behavior when a token is missing:

| Setting | Effect |
| --- | --- |
| `true` \(default\) | Throws `UserNotSignedIn` if any token is missing |
| `false` | Calls the handler anyway; missing tokens resolve to `null` |

Handle the sign-in gap gracefully:

```csharp
try
{
    await Proactive.ContinueConversationAsync(
        adapter, conversationId, OnDailyReminderAsync, cancellationToken: ct);
}
catch (UserNotSignedIn)
{
    // The user hasn't signed in yet. Send a nudge, or queue for later.
    await Proactive.SendActivityAsync(
        adapter,
        conversationId,
        MessageFactory.Text("Sign in so I can send you daily summaries."),
        ct);
}
```

## Error handling

| Exception | Cause |
| --- | --- |
| `KeyNotFoundException` | The `conversationId` wasn't found in storage. The conversation was never stored, or was deleted with `DeleteConversationAsync`. |
| `UserNotSignedIn` | `autoSignInHandlers` was specified but one or more tokens aren't cached and `FailOnUnsignedInConnections` is `true`. |
| `ArgumentNullException` | A required argument \(`adapter`, `activity`, `conversation`\) was `null`. |
| `ArgumentException` | Builder validation failed, typically a missing `agentClientId`, `channelId`, or user ID. |

## Microsoft Teams specifics

Teams requires a tenant ID and, for conversation creation, a service URL. If you don't have the service URL from an inbound activity, use the regional constants:

```csharp
// Public cloud
string serviceUrl = TeamsProactiveServiceEndpoints.publicGlobal;

// Government clouds
string serviceUrl = TeamsProactiveServiceEndpoints.gcc;
string serviceUrl = TeamsProactiveServiceEndpoints.gccHigh;
string serviceUrl = TeamsProactiveServiceEndpoints.dod;
```

### Personal \(1:1\) chat

```csharp
var createOptions = CreateConversationOptionsBuilder
    .Create(
        agentClientId: "your-bot-app-id",
        channelId: Channels.Msteams,
        serviceUrl: TeamsProactiveServiceEndpoints.publicGlobal)
    .WithTenantId("your-tenant-id")
    .WithUser(userId: "aad-user-object-id")
    .WithTopicName("Contoso Notification")
    .WithActivity(MessageFactory.Text("You have a new approval request."))
    .Build();

var conv = await Proactive.CreateConversationAsync(adapter, createOptions, ct);
```

### Channel post

To post into a specific Teams channel, supply the internal Teams channel ID by using `WithTeamsChannelId`. This action automatically sets `isGroup = true`:

```csharp
// teamsChannelId is the "19:...@thread.tacv2" identifier of the Teams channel,
// not the Channels.Msteams string.
var createOptions = CreateConversationOptionsBuilder
    .Create("your-bot-app-id", Channels.Msteams)
    .WithTenantId("your-tenant-id")
    .WithUser("aad-user-object-id")
    .WithTeamsChannelId("19:abc123@thread.tacv2")
    .WithTopicName("Daily Digest")
    .WithActivity(MessageFactory.Text("Here is today's digest."))
    .Build();

await Proactive.CreateConversationAsync(adapter, createOptions, ct);
```

`app.proactive` provides this surface. It's available only to agents built on `AgentApplication` \(not `ActivityHandler`\).

## Concepts

### Conversation

Before you can send a proactive message, you need to know *which conversation* to target. A `Conversation` object holds a `ConversationReference` \(channel, service URL, user IDs\) plus the JWT claims needed to authenticate the outbound call.

You acquire a `Conversation` in one of two ways:

| Approach | When to use |
| --- | --- |
| Store it during a normal turn with `app.proactive.storeConversation(ctx)` | The user already spoke to your agent and you want to reach them later |
| Build one with `ConversationBuilder`, or receive one via HTTP | An external system supplies the reference, or you're creating a new conversation |

### Three proactive operations

| Operation | What it does |
| --- | --- |
| sendActivity | Sends a single `Activity` to a conversation. No `TurnState`, no route handlers, just a fire-and-forget message. |
| continueConversation | Runs a handler inside the conversation context, giving full `TurnContext`, `TurnState`, middleware, and optional OAuth tokens. |
| createConversation | Asks the channel to create a brand-new conversation, then optionally continues it immediately. |

## Setup

### 1. Configure storage

Proactive messaging requires persistent storage so that conversation references survive agent restarts. Use `MemoryStorage` in development and a durable store \(Azure Cosmos DB, Blob Storage\) in production.

```typescript
import { AgentApplication, MemoryStorage, TurnState } from '@microsoft/agents-hosting'

const app = new AgentApplication<TurnState>({
  storage: new MemoryStorage()  // swap for BlobsStorage or CosmosDbPartitionedStorage in production
})
```

`app.proactive` is automatically available once you configure `storage`. Proactive operations use the same storage instance. You can also pass a separate storage backend via the `proactive` option:

```typescript
const app = new AgentApplication<TurnState>({
  storage: new MemoryStorage(),
  proactive: {
    storage: new BlobsStorage(connectionString, containerName)
  }
})
```

## Scenario 1: Send a simple proactive message

### Step 1: Store the conversation

During any normal turn, call `storeConversation` to persist the conversation for later:

```typescript
import { AgentApplication, TurnContext, TurnState } from '@microsoft/agents-hosting'

class MyAgent extends AgentApplication<TurnState> {
  constructor() {
    super({ storage: new MemoryStorage() })

    this.onMessage('/subscribe', async (ctx: TurnContext, state: TurnState) => {
      const conversationId = await this.proactive.storeConversation(ctx)
      await ctx.sendActivity(`You're subscribed! Conversation ID: ${conversationId}`)
    })
  }
}
```

Note

`storeConversation` returns the conversation's ID string. Use this ID later to send activities or continue the conversation.

### Step 2: Send the message later

When the external event arrives \(a webhook, a background job, a timer\), use the stored ID:

```typescript
// adapter resolved via startServer() or your manual Express setup
await app.proactive.sendActivity(
  adapter,
  conversationId,
  { type: 'message', text: 'Your report is ready!' }
)
```

## Scenario 2: Continue a conversation with full agent logic

`continueConversation` runs a handler inside the full `AgentApplication` pipeline, giving the handler access to `TurnState`, middleware, streaming responses, and cached OAuth tokens.

```typescript
await app.proactive.continueConversation(
  adapter,
  conversationId,
  async (ctx: TurnContext, state: TurnState) => {
    // TurnState is fully available, reads the same state as the user's reactive turns
    const lastSeen = state.getValue('user.lastSeen') as string | undefined

    await ctx.sendActivity(`Daily reminder, you last visited on ${lastSeen ?? 'never'}.`)

    state.setValue('user.lastReminderSent', new Date().toISOString())
    // TurnState is saved automatically after the handler returns
  }
)
```

### Pass custom data to the handler

Supply a `continuationActivity` to carry a payload via `ctx.activity.value`:

```typescript
await app.proactive.continueConversation(
  adapter,
  conversationId,
  async (ctx: TurnContext, state: TurnState) => {
    const data = ctx.activity.value as { reportId: number; title: string }
    await ctx.sendActivity(`Report #${data.reportId} '${data.title}' is ready.`)
  },
  undefined,  // no autoSignInHandlers
  {
    value: { reportId: 42, title: 'Q1 Summary' },
    valueType: Proactive.ContinueConversationValueType
  }
)
```

## Scenario 3: Create a new conversation

Use `createConversation` when the user never spoke to your agent and you need to reach them directly, for example, to send an onboarding message or open a Teams chat.

### Build the options

```typescript
import { CreateConversationOptionsBuilder } from '@microsoft/agents-hosting'

const createOptions = CreateConversationOptionsBuilder
  .create(process.env.CLIENT_ID!, 'msteams')
  .withTenantId('your-tenant-id')
  .withUser('aad-user-object-id')
  .withTopicName('Welcome to Contoso Agent')
  .withActivity({ type: 'message', text: 'Hi! I\'m here to help you get started.' })
  .build()
```

### Create only

Create a new conversation and persist the returned ID for future proactive messages:

```typescript
const newConversation = await app.proactive.createConversation(adapter, createOptions)

// Persist the new ID for future proactive messages
const newConversationId = newConversation.reference.conversation.id
```

### Create and immediately continue

Supply a handler as the third argument to run agent logic right after the conversation is created:

```typescript
const newConversation = await app.proactive.createConversation(
  adapter,
  createOptions,
  async (ctx: TurnContext, state: TurnState) => {
    await ctx.sendActivity('Welcome! Here is what I can do for you...')
  }
)
```

Note

If you specify both `withActivity(...)` and a continuation handler, the channel receives the initial activity first, then the handler is invoked.

### Autostore the new conversation

Call `storeConversation(true)` on the builder to automatically persist the reference:

```typescript
const createOptions = CreateConversationOptionsBuilder
  .create(process.env.CLIENT_ID!, 'msteams')
  .withTenantId('your-tenant-id')
  .withUser('user-id')
  .storeConversation(true)
  .build()

const conv = await app.proactive.createConversation(adapter, createOptions)
// conv.reference.conversation.id can now be used with sendActivity
```

## Scenario 4: Long-running external task

Use this pattern when the user requests an operation that takes an extended amount of time, and an external service performs the work.

Here's the basic flow:

1. User asks the agent to start a long-running job.
2. Agent captures the conversation and sends it, along with task details, to the external service.
3. The external service does the work, then calls back to the agent over HTTP with the result.
4. Agent runs the continuation handler and delivers the result.

```typescript
class MyAgent extends AgentApplication<TurnState> {
  constructor() {
    super({ storage: new MemoryStorage() })

    this.onMessage('analyze', async (ctx: TurnContext, state: TurnState) => {
      const conversation = new Conversation(ctx)

      // Send task + conversation to the external service
      await externalService.submitJob({
        documentId: ctx.activity.text,
        conversation: conversation.toJson(),
        callbackUrl: 'https://myagent.example.com/api/proactive/continue/analysis'
      })

      await ctx.sendActivity('Analysis started. I\'ll notify you when it\'s done.')
    })
  }
}
```

Register the callback endpoint on the Express server:

```typescript
const server = startServer(app)

// External service calls POST /api/proactive/continue/analysis with the result in the body
server.post('/api/proactive/continue/analysis', async (req, res) => {
  const conversationId = req.body.conversationId as string
  try {
    await app.proactive.continueConversation(
      adapter,
      conversationId,
      async (ctx: TurnContext, state: TurnState) => {
        const result = ctx.activity.value as { summary: string }
        await ctx.sendActivity(`Analysis complete: ${result.summary}`)
      },
      undefined,
      { value: req.body, valueType: Proactive.ContinueConversationValueType }
    )
    res.sendStatus(200)
  } catch (err) {
    res.status(500).json({ error: String(err) })
  }
})
```

## Scenario 5: Background task

Use a standard `Promise`-based background task when the work happens inside the same process as the agent. Capture the `Conversation` and `adapter` *before* the turn ends. The `TurnContext` isn't valid after the turn completes.

```typescript
this.onMessage('process', async (ctx: TurnContext, state: TurnState) => {
  // Capture the conversation before the turn ends. Do NOT close over ctx.
  const conversation = new Conversation(ctx)

  // Fire-and-forget the background work
  void (async () => {
    try {
      // Perform the long-running work
      await doLongRunningWork()

      // Send a simple message back to the user
      await this.proactive.sendActivity(
        this.adapter,
        conversation,
        { type: 'message', text: 'Processing complete!' }
      )
    } catch (err) {
      console.error('Background task failed:', err)
    }
  })()

  await ctx.sendActivity('Working on it. I\'ll let you know when it\'s done.')
})
```

> Capture `new Conversation(ctx)` *before* the async lambda, not inside it. The `TurnContext` is disposed after the turn completes and isn't safe to use afterwards. `this.adapter` and `this.proactive` are stable class references and can be accessed anywhere.

## Context inside continueConversation handlers

A `continueConversation` handler receives a fully initialized turn context scoped to the original conversation. This context means:

- **`TurnState`** loads relative to the original conversation and user, the same state the user's reactive turns see.
- **OAuth tokens** obtained during prior reactive turns are available if their handler names are listed in `autoSignInHandlers`. If any listed handler isn't signed in, `continueConversation` throws by default \(configurable via `proactive.failOnUnsignedInConnections`\).
- The handler automatically **saves** state after it completes, as in a reactive turn.

```typescript
await app.proactive.continueConversation(
  adapter,
  conversationId,
  async (ctx: TurnContext, state: TurnState) => {
    // User-scoped state from prior turns is available
    const name = state.getValue('user.preferredName') as string

    await ctx.sendActivity(`Hi ${name}, here is your update...`)

    // State changes are persisted after the handler returns
    state.setValue('user.lastNotified', new Date().toISOString())
  },
  ['graph']  // autoSignInHandlers, token for 'graph' was acquired in a prior reactive turn
)
```

## Multiple continuation handlers

Because TypeScript uses inline functions rather than decorated methods, multiple continuation handlers are distinct functions or closures passed to `continueConversation`. Register separate HTTP endpoints for each:

```typescript
// Handler for daily reminders
const onDailyReminder = async (ctx: TurnContext, state: TurnState) => {
  await ctx.sendActivity('Here is your daily summary...')
}

// Handler for report notifications
const onReportReady = async (ctx: TurnContext, state: TurnState) => {
  await ctx.sendActivity('Your scheduled report is ready. Check your email.')
}

// Invoke from code
await app.proactive.continueConversation(adapter, conversationId, onDailyReminder, ['graph'])
await app.proactive.continueConversation(adapter, conversationId, onReportReady)

// Separate HTTP endpoints
server.post('/api/proactive/reminder/:conversationId', async (req, res) => {
  await app.proactive.continueConversation(adapter, req.params.conversationId, onDailyReminder, ['graph'])
  res.sendStatus(200)
})

server.post('/api/proactive/report/:conversationId', async (req, res) => {
  await app.proactive.continueConversation(adapter, req.params.conversationId, onReportReady)
  res.sendStatus(200)
})
```

## Triggering proactive actions over HTTP

The TypeScript SDK doesn't register proactive HTTP endpoints automatically. You register them on the Express server returned by `startServer()`. Apply the same authentication middleware used for `/api/messages` if the endpoints should be protected.

A complete proactive Express setup:

```typescript
import { startServer } from '@microsoft/agents-hosting-express'
import { AgentApplication, CloudAdapter, Conversation, CreateConversationOptionsBuilder, MemoryStorage, Proactive, TurnState } from '@microsoft/agents-hosting'

const app = new AgentApplication<TurnState>({ storage: new MemoryStorage() })
const server = startServer(app)

// Use the adapter that startServer created, same instance that processes inbound messages
const adapter = app.adapter as CloudAdapter

// --- Send activity to a stored conversation ---
server.post('/api/proactive/send/:conversationId', async (req, res) => {
  try {
    const result = await app.proactive.sendActivity(
      adapter,
      req.params.conversationId,
      req.body
    )
    res.json({ id: result.id })
  } catch (err) {
    res.status(500).json({ error: String(err) })
  }
})

// --- Continue a stored conversation ---
server.post('/api/proactive/continue/:conversationId', async (req, res) => {
  try {
    await app.proactive.continueConversation(
      adapter,
      req.params.conversationId,
      async (ctx, state) => {
        await ctx.sendActivity(`Proactive: ${(req.body as any).message}`)
      },
      undefined,
      { value: req.body, valueType: Proactive.ContinueConversationValueType }
    )
    res.sendStatus(200)
  } catch (err) {
    res.status(500).json({ error: String(err) })
  }
})

// --- Continue using an inline Conversation object (no prior storage) ---
server.post('/api/proactive/continue', async (req, res) => {
  const { reference, claims } = req.body.conversation
  const conversation = new Conversation(claims, reference)
  try {
    await app.proactive.continueConversation(
      adapter,
      conversation,
      async (ctx, state) => {
        await ctx.sendActivity(`Inline proactive: ${(req.body as any).message}`)
      }
    )
    res.sendStatus(200)
  } catch (err) {
    res.status(500).json({ error: String(err) })
  }
})

// --- Create a new conversation ---
server.post('/api/proactive/create', async (req, res) => {
  const { userId, tenantId } = req.body as { userId: string; tenantId: string }
  const opts = CreateConversationOptionsBuilder
    .create(process.env.CLIENT_ID!, 'msteams')
    .withTenantId(tenantId)
    .withUser(userId)
    .storeConversation(true)
    .build()
  try {
    const conv = await app.proactive.createConversation(adapter, opts)
    res.json({ conversationId: conv.reference.conversation.id })
  } catch (err) {
    res.status(500).json({ error: String(err) })
  }
})
```

## OAuth and sign-in in proactive contexts

When you specify `autoSignInHandlers`, `continueConversation` checks whether each listed OAuth handler is already signed in before invoking the handler. `ProactiveOptions.failOnUnsignedInConnections` controls the behavior when a token is missing:

| Setting | Effect |
| --- | --- |
| `true` \(default\) | Throws if any token is missing |
| `false` | Calls the handler anyway; missing tokens resolve to `null` |

Handle the sign-in gap gracefully:

```typescript
import { AgentApplication, MemoryStorage, TurnState } from '@microsoft/agents-hosting'

const app = new AgentApplication<TurnState>({
  storage: new MemoryStorage(),
  proactive: { failOnUnsignedInConnections: true }  // default, explicit for clarity
})

try {
  await app.proactive.continueConversation(
    adapter,
    conversationId,
    onDailyReminder,
    ['graph']
  )
} catch (err) {
  // User hasn't signed in yet. Send a nudge, or queue for later.
  await app.proactive.sendActivity(
    adapter,
    conversationId,
    { type: 'message', text: 'Sign in so I can send you daily summaries.' }
  )
}
```

## Error handling

| Error | Cause |
| --- | --- |
| `Error: Conversation not found` | The `conversationId` wasn't found in storage. The conversation was never stored, or was deleted by using `deleteConversation`. |
| `Error: User not signed in` | You specified `autoSignInHandlers` but one or more tokens aren't cached and `failOnUnsignedInConnections` is `true`. |
| `TypeError` | A required argument \(`adapter`, `activity`, `conversation`\) is `null` or `undefined`. |
| Validation error | `ConversationBuilder.build()` or `CreateConversationOptionsBuilder.build()` failed, typically due to a missing `agentClientId`, `channelId`, or user ID. |

Important

Adapter callbacks swallow exceptions internally. The proactive methods capture and re-throw errors automatically, but if you call `adapter.continueConversation` directly, use the capture-and-rethrow pattern:

```typescript
let capturedError: Error | undefined
await adapter.continueConversation(identity, ref, async (ctx) => {
  try {
    await doWork(ctx)
  } catch (err) {
    capturedError = err as Error
  }
})
if (capturedError) throw capturedError
```

## Microsoft Teams specifics

Teams requires a tenant ID and, for conversation creation, a service URL. If you don't have the service URL from an inbound activity, use the well-known constants exported from `@microsoft/agents-hosting`:

```typescript
import { TeamsServiceEndpoints } from '@microsoft/agents-hosting'

// Public cloud
const serviceUrl = TeamsServiceEndpoints.publicGlobal

// Government clouds
const serviceUrl = TeamsServiceEndpoints.gcc
const serviceUrl = TeamsServiceEndpoints.gccHigh
const serviceUrl = TeamsServiceEndpoints.dod
```

### Personal \(1:1\) chat

```typescript
const createOptions = CreateConversationOptionsBuilder
  .create(
    process.env.CLIENT_ID!,
    'msteams',
    TeamsServiceEndpoints.publicGlobal
  )
  .withTenantId('your-tenant-id')
  .withUser('aad-user-object-id')
  .withTopicName('Contoso Notification')
  .withActivity({ type: 'message', text: 'You have a new approval request.' })
  .build()

const conv = await app.proactive.createConversation(adapter, createOptions)
```

### Channel post

To post into a specific Teams channel, supply the internal Teams channel ID by using `withTeamsChannelId`. This action automatically sets `isGroup = true`:

```typescript
// teamsChannelId is the "19:...@thread.tacv2" identifier of the Teams channel,
// not the string 'msteams'.
const createOptions = CreateConversationOptionsBuilder
  .create(process.env.CLIENT_ID!, 'msteams')
  .withTenantId('your-tenant-id')
  .withUser('aad-user-object-id')
  .withTeamsChannelId('19:abc123@thread.tacv2')
  .withTopicName('Daily Digest')
  .withActivity({ type: 'message', text: 'Here is today\'s digest.' })
  .build()

await app.proactive.createConversation(adapter, createOptions)
```

## Summary

Proactive messaging transforms agents from passive responders into active participants, and decouples the receipt of a request from the delivery of a response. This change lets agents integrate better with real-time events, background processes, and external systems, and reach out to the user. This functionality enables experiences that feel natural and timely rather than limited to the conversational turn model.
