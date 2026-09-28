<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/unit-testing-agents-dotnet -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Unit test your agents in .NET

Unit tests let you verify your agent's behavior turn by turn without deploying to a channel, connecting to Azure AI Bot Service, or sending real HTTP traffic. This guide builds from simple echo tests up through multurn flows, dependency mocking, and AI-backed semantic validation.

## Prerequisites

Add the `Microsoft.Agents.Builder.Testing` NuGet package to your test project. It includes `AgentTestHost`, `TestAdapter`, and `TestFlow` - the three components you use in every test.

```xml
<PackageReference Include="Microsoft.Agents.Builder.Testing" Version="*" />
```

Tests in this guide use [xUnit](https://xunit.net/) and [Moq](https://github.com/moq/moq), but the testing library has no dependency on a specific test framework.

## Core concepts

### TestAdapter

`TestAdapter` is the in-process stand-in for a real channel adapter. Instead of sending activities over a network, it queues agent replies in an `ActiveQueue` that your assertions read from. It also contains a `MockUserTokenClient` for simulating OAuth flows.

### TestFlow

`TestFlow` is a fluent API for modeling a conversation as a sequence of send/assert operations. The chain is evaluated lazily. Nothing executes until you call `StartTestAsync()`.

```csharp
await new TestFlow(adapter, myBotCallback)
    .Send("hello")
    .AssertReply("Hello back!")
    .StartTestAsync();
```

### AgentTestHost

`AgentTestHost` wraps an `IHost` configured the same way as your production `Program.cs`. It preregisters `TestAdapter` as `IChannelAdapter` and exposes `CreateTestFlow()` to start test conversations.

```csharp
await using var host = AgentTestHost.Create(builder =>
{
    builder.Services.AddSingleton<IStorage, MemoryStorage>();
    builder.Services.AddTransient<IAgent, MyAgent>();
});

await host.CreateTestFlow()
    .Send("hello")
    .AssertReply("Hello back!")
    .StartTestAsync();
```

> **Important:** Don't call `AddAgent<T>()` inside `AgentTestHost.Create()`. That method registers `CloudAdapter`, which conflicts with the preregistered `TestAdapter`. Register `IAgent` directly by using `AddTransient<IAgent, T>()` or a factory delegate.

## Your first test

Given an agent that echoes user messages:

```csharp
public class EchoAgent : AgentApplication
{
    public EchoAgent(AgentApplicationOptions options) : base(options)
    {
        OnActivity(ActivityTypes.Message, OnMessageAsync, rank: RouteRank.Last);
    }

    private async Task OnMessageAsync(ITurnContext tc, ITurnState ts, CancellationToken ct)
    {
        await tc.SendActivityAsync($"You said: {tc.Activity.Text}", cancellationToken: ct);
    }
}
```

The test:

```csharp
[Fact]
public async Task Echo_ReturnsUserText()
{
    await using var host = AgentTestHost.Create(builder =>
    {
        builder.Services.AddSingleton<IStorage, MemoryStorage>();
        builder.Services.AddTransient<IAgent>(sp =>
            new EchoAgent(new AgentApplicationOptions(sp.GetRequiredService<IStorage>())));
    });

    await host.CreateTestFlow()
        .Send("hello")
        .AssertReply("You said: hello")
        .StartTestAsync();
}
```

### What each step does

| Step | Description |
| --- | --- |
| `AgentTestHost.Create(...)` | Builds and starts an in-process host with `TestAdapter` prewired |
| `CreateTestFlow()` | Resolves `IAgent` from DI and wraps it in a `TestFlow` |
| `.Send("hello")` | Creates a `Message` activity and routes it through the agent |
| `.AssertReply("You said: hello")` | Dequeues the next reply and asserts its text \(trimmed, exact match\) |
| `.StartTestAsync()` | Executes the entire chain |

## Assertion variants

`TestFlow` provides several assertion methods depending on how precise your check needs to be.

### Exact text match

```csharp
.AssertReply("You said: hello")
```

### Substring match

```csharp
.AssertReplyContains("hello")
```

### One of several acceptable replies

```csharp
.AssertReplyOneOf(new[] { "Hi!", "Hello!", "Hey!" })
```

### Custom validation with a delegate

```csharp
.AssertReply(activity =>
{
    Assert.Equal(ActivityTypes.Message, activity.Type);
    Assert.Contains("hello", activity.Text);
})
```

### Async validation delegate

```csharp
.AssertReplySatisfies(async activity =>
{
    var data = await LoadExpectedDataAsync();
    Assert.Equal(data.Expected, activity.Text);
})
```

### Verify no further replies

After asserting all expected replies, guard against unexpected extras:

```csharp
.AssertReply("done")
.AssertNoMoreReplies()
```

`AssertNoMoreReplies()` waits 1 second and fails if any activity arrives. Use the description parameter to name the assertion in failure output:

```csharp
.AssertNoMoreReplies("only one reply expected per turn")
```

## Combine send and assert with Test\(\)

For single-turn pairs, `.Test()` combines `.Send()` and `.AssertReply()`:

```csharp
await host.CreateTestFlow()
    .Test("ping", "pong")
    .Test("foo",  "You said: foo")
    .StartTestAsync();
```

## Multi-turn conversations

Chain multiple send/assert pairs to test full conversation flows:

```csharp
await host.CreateTestFlow()
    .Send("start")
    .AssertReply("What is your name?")
    .Send("Alice")
    .AssertReply("Hello, Alice!")
    .Send("what can you do?")
    .AssertReply(activity => Assert.NotEmpty(activity.Text))
    .StartTestAsync();
```

## Test multiple replies per turn

An agent can send several activities in response to one user message. Each `.AssertReply()` call dequeues one activity from the queue:

```csharp
await host.CreateTestFlow()
    .Send("tell me three things")
    .AssertReply("First thing.")
    .AssertReply("Second thing.")
    .AssertReply("Third thing.")
    .AssertNoMoreReplies()
    .StartTestAsync();
```

## Test conversation updates

Channels use `ConversationUpdate` activities to notify agents that members join or leave. Use `SendConversationUpdate()` to simulate the join event that triggers a welcome message.

### Test with the default user

If you don't pass any arguments, the adapter adds its default user \(`user1`\) to `MembersAdded`:

```csharp
await host.CreateTestFlow()
    .SendConversationUpdate()
    .AssertReply("Hello and Welcome!")
    .StartTestAsync();
```

### Test with specific members

```csharp
await host.CreateTestFlow()
    .SendConversationUpdate(new[]
    {
        new ChannelAccount { Id = "alice", Name = "Alice" },
        new ChannelAccount { Id = "bob",   Name = "Bob"   }
    })
    .AssertReply("Hello and Welcome!")
    .StartTestAsync();
```

### Full welcome and message flow

```csharp
await host.CreateTestFlow()
    .SendConversationUpdate()
    .AssertReply("Hello and Welcome!")
    .Send("hello")
    .AssertReply("You said: hello")
    .AssertNoMoreReplies()
    .StartTestAsync();
```

## Inspect the full activity

When you need to check properties beyond `Text`, like `Speak`, `InputHint`, `SuggestedActions`, or attachments, use a delegate assertion:

```csharp
.AssertReply(activity =>
{
    Assert.Equal("Sure, one moment…", activity.Text);
    Assert.Equal("Sure, one moment…", activity.Speak);
    Assert.Equal(InputHints.IgnoringInput, activity.InputHint);
})
```

For Adaptive Card attachments, `TestAdapter` round-trips serialization, so `Attachment.Content` arrives as a `JsonElement`. Use `.ToString()` to extract its string value:

```csharp
.AssertReply(activity =>
{
    var card = activity.Attachments
        .First(a => a.ContentType == ContentTypes.AdaptiveCard);

    // Correct: Content is JsonElement after TestAdapter serialization
    string json = card.Content.ToString()!;
    Assert.Contains("Seattle", json);
})
```

## Typing indicators

If your agent sends a Typing activity before the real reply, assert it explicitly:

```csharp
.Send("hello")
.AssertTypingIndicator()
.AssertReply("Here is your answer…")
```

## Assert activity type

```csharp
.AssertReply(activity =>
{
    Assert.Equal(ActivityTypes.Message, activity.Type);
})
```

## Data-driven tests

Rather than writing a separate test for each input variant, use xUnit `Theory` tests with `[InlineData]` to parameterize:

```csharp
[Theory]
[InlineData("hi",    "You said: hi")]
[InlineData("hello", "You said: hello")]
[InlineData("bye",   "You said: bye")]
public async Task Echo_VariousInputs(string input, string expected)
{
    await using var host = AgentTestHost.Create(builder =>
    {
        builder.Services.AddSingleton<IStorage, MemoryStorage>();
        builder.Services.AddTransient<IAgent>(sp =>
            new EchoAgent(new AgentApplicationOptions(sp.GetRequiredService<IStorage>())));
    });

    await host.CreateTestFlow()
        .Test(input, expected)
        .StartTestAsync();
}
```

For complex test cases, including multiple turns, and different conversation states, use `[MemberData]`:

```csharp
public static IEnumerable<object[]> ConversationFlows()
{
    yield return new object[]
    {
        new string[] { "start", "Alice", "done" },
        new string[] { "What is your name?", "Hello, Alice!", "Goodbye, Alice!" }
    };
    yield return new object[]
    {
        new string[] { "start", "Bob", "done" },
        new string[] { "What is your name?", "Hello, Bob!", "Goodbye, Bob!" }
    };
}

[Theory]
[MemberData(nameof(ConversationFlows))]
public async Task MultiTurn_Flow(string[] inputs, string[] expected)
{
    await using var host = AgentTestHost.Create(builder =>
    {
        builder.Services.AddSingleton<IStorage, MemoryStorage>();
        builder.Services.AddTransient<IAgent, GreetingAgent>();
    });

    var flow = host.CreateTestFlow();
    for (int i = 0; i < inputs.Length; i++)
    {
        flow = flow.Test(inputs[i], expected[i]);
    }
    await flow.StartTestAsync();
}
```

## Use mocks

Unit tests should isolate the component under test. Use Moq to replace external dependencies, such as AI services, databases, and recognizers, so that tests remain deterministic and fast.

### Inject mock dependencies

Design your agent to receive dependencies through its constructor rather than creating them internally:

```csharp
// Harder to test — agent owns the recognizer
public class WeatherAgent : AgentApplication
{
    private readonly WeatherService _weather = new WeatherService();
}

// Easier to test — dependency injected
public class WeatherAgent : AgentApplication
{
    private readonly IWeatherService _weather;

    public WeatherAgent(AgentApplicationOptions options, IWeatherService weather)
        : base(options)
    {
        _weather = weather;
    }
}
```

### Replace a service in tests

```csharp
[Fact]
public async Task Weather_ReturnsFormattedForecast()
{
    var mockWeather = new Mock<IWeatherService>();
    mockWeather
        .Setup(s => s.GetForecastAsync("Seattle", It.IsAny<CancellationToken>()))
        .ReturnsAsync(new Forecast { TemperatureC = 18, Summary = "Partly cloudy" });

    await using var host = AgentTestHost.Create(builder =>
    {
        builder.Services.AddSingleton<IStorage, MemoryStorage>();
        builder.Services.AddSingleton<IWeatherService>(mockWeather.Object);
        builder.Services.AddTransient<IAgent>(sp =>
            new WeatherAgent(
                new AgentApplicationOptions(sp.GetRequiredService<IStorage>()),
                sp.GetRequiredService<IWeatherService>()));
    });

    await host.CreateTestFlow()
        .Send("weather in Seattle")
        .AssertReplyContains("18")
        .StartTestAsync();
}
```

### Verify service calls

```csharp
mockWeather.Verify(
    s => s.GetForecastAsync("Seattle", It.IsAny<CancellationToken>()),
    Times.Once);
```

## Semantic validation using AI

When your agent calls a language model and its output is nondeterministic, exact text assertions are brittle. `SemanticValidator` uses an AI judge to evaluate whether a reply satisfies a yes/no question.

### SemanticValidator

```csharp
var validator = new SemanticValidator(chatClient, "Does this response describe the weather?");

await host.CreateTestFlow()
    .Send("What is the weather in Seattle?")
    .AssertReplySatisfies(validator, timeout: 60_000)
    .StartTestAsync();
```

The validator sends the agent's reply text to the AI judge with the assertion question. If the judge responds with "yes," the assertion passes. If it responds with "no," the test fails with a detailed message showing the prompt and the actual reply.

### Create an IChatClient

```csharp
using Azure.AI.OpenAI;
using Azure.Core;
using Microsoft.Extensions.AI;

IChatClient chatClient = new AzureOpenAIClient(
        new Uri(endpoint),
        new ApiKeyCredential(apiKey))   // ApiKeyCredential is from System.ClientModel
    .GetChatClient(deploymentName)
    .AsIChatClient();
```

### Custom IResponseValidator

Implement `IResponseValidator` when `SemanticValidator` doesn't fit, for example, when the reply is an Adaptive Card rather than plain text:

```csharp
public class WeatherCardValidator : IResponseValidator
{
    private readonly IChatClient _judge;
    private readonly string _location;

    public WeatherCardValidator(IChatClient judge, string location)
    {
        _judge = judge;
        _location = location;
    }

    public async Task ValidateAsync(IActivity reply, CancellationToken ct = default)
    {
        string content;

        if (!string.IsNullOrEmpty(reply?.Text))
        {
            content = reply.Text;
        }
        else
        {
            var card = reply?.Attachments?
                .FirstOrDefault(a => a.ContentType == ContentTypes.AdaptiveCard);

            if (card?.Content == null)
                throw new InvalidOperationException("Reply has neither text nor Adaptive Card.");

            // Content is JsonElement after TestAdapter round-trip — use ToString()
            content = card.Content.ToString()!;
        }

        var messages = new List<ChatMessage>
        {
            new(ChatRole.System, "Answer only 'yes' or 'no'."),
            new(ChatRole.User, $"Does this contain a weather forecast for {_location}?\n\n{content}")
        };

        var response = await _judge.GetResponseAsync(messages, cancellationToken: ct);
        var answer = response?.Text?.Trim().ToLowerInvariant() ?? string.Empty;

        if (answer.StartsWith("yes"))
            return;

        if (answer.StartsWith("no"))
            throw new InvalidOperationException(
                $"Validation failed for '{_location}'. Agent replied:\n{content}");

        throw new InvalidOperationException($"Unexpected judge response: '{answer}'");
    }
}
```

Usage:

```csharp
[Fact(Skip = "Requires Azure OpenAI. Set AZURE_OPENAI_ENDPOINT, AZURE_OPENAI_KEY, AZURE_OPENAI_DEPLOYMENT_NAME.")]
public async Task WeatherAgent_ReturnsSeattleForecast()
{
    string endpoint   = Environment.GetEnvironmentVariable("AZURE_OPENAI_ENDPOINT")!;
    string apiKey     = Environment.GetEnvironmentVariable("AZURE_OPENAI_KEY")!;
    string deployment = Environment.GetEnvironmentVariable("AZURE_OPENAI_DEPLOYMENT_NAME")!;

    IChatClient judge = new AzureOpenAIClient(new Uri(endpoint), new ApiKeyCredential(apiKey))
        .GetChatClient(deployment)
        .AsIChatClient();

    var validator = new WeatherCardValidator(judge, "Seattle");

    await using var host = AgentTestHost.Create(builder =>
    {
        builder.Services.AddSingleton<IStorage, MemoryStorage>();
        // ... register Kernel and agent
    });

    await host.CreateTestFlow()
        .SendConversationUpdate()
        .AssertReplyContains("Welcome")
        .Send("What is the weather forecast for Seattle today?")
        .AssertReplySatisfies(validator, timeout: 60_000)
        .AssertNoMoreReplies()
        .StartTestAsync();
}
```

Note

Tests that call external AI services are slow and have environmental dependencies. Mark them with `[Fact(Skip = "...")]` and a clear message about required environment variables. Run them in a dedicated CI stage rather than with your unit test suite.

## Test middleware

Attach middleware to `host.Adapter` before creating test flows. All flows created from that host process activities through the middleware.

### Transcript logging

```csharp
[Fact]
public async Task Transcript_CapturesAllActivities()
{
    await using var host = AgentTestHost.Create(builder =>
    {
        builder.Services.AddSingleton<IStorage, MemoryStorage>();
        builder.Services.AddTransient<IAgent, EchoAgent>();
    });

    var transcript = new MemoryTranscriptStore();
    host.Adapter.Use(new TranscriptLoggerMiddleware(transcript));

    await host.CreateTestFlow()
        .SendConversationUpdate()
        .AssertReply("Hello and Welcome!")
        .Send("hello")
        .AssertReply("You said: hello")
        .AssertNoMoreReplies()
        .StartTestAsync();

    var activities = await GetTranscriptAsync(
        host.Adapter.Conversation.ChannelId,
        host.Adapter.Conversation.Conversation.Id,
        transcript);

    // ConversationUpdate in, welcome out, message in, echo out = 4
    Assert.Equal(4, activities.Count);
}

private static async Task<IList<IActivity>> GetTranscriptAsync(
    string channelId, string conversationId, ITranscriptStore store)
{
    var result = new List<IActivity>();
    string token = null;
    do
    {
        var page = await store.GetTranscriptActivitiesAsync(channelId, conversationId, token);
        token = page.ContinuationToken;
        result.AddRange(page.Items);
    } while (token != null);
    return result;
}
```

## Use TestAdapter directly

Use `AgentTestHost` for the recommended setup path. However, you can create `TestAdapter` and `TestFlow` directly when you want lower-level control or are testing a standalone callback.

```csharp
[Fact]
public async Task DirectAdapter_Echo()
{
    var adapter = TestAdapter.Create(channelId: Channels.Msteams);

    async Task BotCallback(ITurnContext tc, CancellationToken ct)
    {
        if (tc.Activity.Type == ActivityTypes.Message)
            await tc.SendActivityAsync($"echo:{tc.Activity.Text}", cancellationToken: ct);
    }

    await new TestFlow(adapter, BotCallback)
        .Test("foo", "echo:foo")
        .StartTestAsync();
}
```

### Customize the conversation reference

```csharp
var adapter = TestAdapter.Create(
    channelId:        "msteams",
    userId:           "u42",
    userName:         "Alice",
    botId:            "mybot",
    botName:          "MyBot",
    conversationId:   "conv-42",
    conversationName: "Test Room");
```

Set the conversation reference directly on the host's adapter before creating flows:

```csharp
host.Adapter.Conversation = new ConversationReference
{
    ChannelId    = Channels.Msteams,
    User         = new ChannelAccount("alice", "Alice"),
    Agent        = new ChannelAccount("bot",   "Bot"),
    Conversation = new ConversationAccount(false, "conv-1", "Conversation 1"),
    ServiceUrl   = "https://test.example.com"
};
```

## Testing OAuth and token flows

`TestAdapter` exposes methods to prepopulate user tokens. These methods let you test agents that use [GetUserTokenAsync](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.userauth.tokenservice.usertokenclientwrapper.getusertokenasync) or single sign-on flows without connecting to a real identity provider.

### Prepopulate a token

```csharp
host.Adapter.AddUserToken(
    connectionName: "MyOAuthConnection",
    channelId:      Channels.Test,
    userId:         "user1",
    token:          "fake-access-token");
```

### Prepopulate an exchangeable token for single sign-on

```csharp
host.Adapter.AddExchangeableToken(
    connectionName:  "MyOAuthConnection",
    channelId:       Channels.Test,
    userId:          "user1",
    exchangableItem: "sso-token",
    token:           "fake-access-token");
```

### Simulate an exchange failure

```csharp
host.Adapter.ThrowOnExchangeRequest(
    connectionName:  "MyOAuthConnection",
    channelId:       Channels.Test,
    userId:          "user1",
    exchangableItem: "bad-sso-token");
```

## Insert delays

Use `.Delay()` when your agent has time-dependent behavior.

```csharp
await host.CreateTestFlow()
    .Send("start")
    .Delay(TimeSpan.FromSeconds(2))
    .Send("are you still there?")
    .AssertReply("Yes, I'm here.")
    .StartTestAsync();
```

## Timeout defaults and debugging

All assertion methods have a `timeout` parameter in milliseconds, with a default value of `3000`. When you attach the Visual Studio debugger, the system automatically sets timeouts to `uint.MaxValue` so that breakpoints don't cause spurious failures.

For long-running agent operations, such as calls to a language model, pass an explicit timeout.

```csharp
.AssertReplySatisfies(validator, timeout: 60_000)
```

`AssertNoMoreReplies()` uses a shorter default of `1000` ms since the agent already finished processing.

## Reference

### AgentTestHost

| Member | Description |
| --- | --- |
| `AgentTestHost.Create(configure)` | Creates and starts the host. Preregisters `TestAdapter` as `IChannelAdapter`. |
| `host.Adapter` | The `TestAdapter` instance. Attach middleware here. |
| `host.CreateTestFlow()` | Resolves `IAgent` from DI and returns a `TestFlow`. |
| `host.DisposeAsync()` | Stops the host. Use `await using` to dispose. |

### TestAdapter

| Member | Description |
| --- | --- |
| `TestAdapter.Create(...)` | Factory for a fully configured adapter. |
| `adapter.Conversation` | The `ConversationReference` used for all activities. |
| `adapter.ActiveQueue` | Queue of activities sent by the agent. |
| `adapter.Use(middleware)` | Attaches middleware. Returns `this` for chaining. |
| `adapter.AddUserToken(...)` | Prepopulates a user token for OAuth testing. |
| `adapter.AddExchangeableToken(...)` | Prepopulates an SSO-exchangeable token. |
| `adapter.ThrowOnExchangeRequest(...)` | Configures an exchange request to throw. |

### TestFlow methods

| Method | Description |
| --- | --- |
| `.Send(text)` | Sends a message activity. |
| `.Send(activity)` | Sends any activity type. |
| `.SendConversationUpdate()` | Sends a ConversationUpdate with the default user. |
| `.SendConversationUpdate(members)` | Sends a ConversationUpdate with specific members. |
| `.Test(input, expected)` | `.Send()` + `.AssertReply()` shorthand. |
| `.AssertReply(string)` | Exact text match \(trimmed\). |
| `.AssertReplyContains(string)` | Substring match. |
| `.AssertReplyOneOf(string[])` | Match any one of several strings. |
| `.AssertReply(Activity)` | Match by activity type and text. |
| `.AssertReply(Action<IActivity>)` | Custom sync validation; throw to fail. |
| `.AssertReplySatisfies(Func<IActivity, Task>)` | Custom async validation. |
| `.AssertReplySatisfies(IResponseValidator)` | Delegate to a validator object. |
| `.AssertTypingIndicator()` | Expects a Typing activity. |
| `.AssertNoMoreReplies()` | Fails if any activity arrives within 1 second. |
| `.Delay(ms)` | Inserts a pause in the flow. |
| `.StartTestAsync()` | Executes the chain. |

### SemanticValidator

| Member | Description |
| --- | --- |
| `new SemanticValidator(chatClient, prompt)` | Creates a validator. `prompt` is a yes/no question about the reply. |
| `ValidateAsync(activity, ct)` | Passes if AI responds "yes"; throws if "no" or unexpected. |
