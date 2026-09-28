<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-dotnet -->
<!-- Sitemap-Last-Modified: 2025-09-04 -->

# Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for .NET

This article describes required changes to migrate from the Bot Framework SDK for .NET to the Microsoft 365 Agents SDK for .NET.

Tip

Treat this work as a modernization effort, not only a package swap. The Agents SDK favors simpler, unopinionated patterns \(minimal APIs, DI, standard logging\) and deprecates legacy features like LUIS/QnA and Composer artifacts. Keep only what your bot actually needs and avoid carrying forward old template complexity.

## Azure resources

Your existing Azure resources remain unchanged during this migration. Continue using your current Azure Bot registration \(App ID and secret\); you reference those values in the new TokenValidation and Connections configuration sections described later. Many solutions also include legacy app settings such as `MicrosoftAppType`, `MicrosoftAppId`, `MicrosoftAppPassword`, and `MicrosoftAppTenantId`. These entries are harmless during migration but no longer used by the Microsoft 365 Agents SDK, so you can remove them after you validate the new configuration.

## First steps

Start by updating package dependencies. The following changes don't cover every namespace you might need to touch, but they handle most package substitutions.

| Bot Framework SDK | Agents SDK |
| --- | --- |
| [Microsoft.Bot.Builder.Integration.AspNet.Core](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.integration.aspnet.core) | [Microsoft.Agents.Hosting.AspNetCore](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.hosting.aspnetcore) and [Microsoft.Agents.Authentication.Msal](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.authentication.msal) |
| [Microsoft.Bot.Builder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder) | [Microsoft.Agents.Builder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder) |
| [Microsoft.Bot.Builder.Dialogs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.dialogs) | [Microsoft.Agents.Builder.Dialogs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.dialogs) |
| [Microsoft.Bot.Builder.Azure.Blobs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.azure.blobs) | [Microsoft.Agents.Storage.Blobs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.storage.blobs) |
| [Microsoft.Bot.Builder.Azure](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.azure) | [Microsoft.Agents.Storage.CosmosDb](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.storage.cosmosdb) |
| [Microsoft.Bot.Schema](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.schema) | [Microsoft.Agents.Core](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.core) |

If your bot integrates with Microsoft Teams, include the Teams Extension package [Microsoft.Agents.Extensions.Teams](https://www.nuget.org/packages/Microsoft.Agents.Extensions.Teams) for core Teams features.

Remove your dependency on [NewtonSoft.Json](https://www.nuget.org/packages/Newtonsoft.Json). The Agents SDK uses [System.Text.Json](https://learn.microsoft.com/en-us/dotnet/api/system.text.json) for serialization.

Take a moment to clean up NuGet sources and pin package versions. Remove any deprecated Bot Framework preview feeds—such as former MyGet sources—from NuGet.config to avoid restore failures. Prefer the latest stable `Microsoft.Agents.*` packages and consider central version pinning \(for example, via Directory.Packages.props\) so you can upgrade intentionally.

Next, update namespaces. The easiest approach is a solution-wide find-and-replace of the exact text.

| Bot Framework Namespace | Agents SDK Namespace |
| --- | --- |
| `using Microsoft.Bot.Builder.Integration.AspNet.Core;` | `using Microsoft.Agents.Hosting.AspNetCore;` |
| `using Microsoft.Bot.Builder;` | `using Microsoft.Agents.Builder;` |
| `Microsoft.Bot.Builder.Dialogs` | `Microsoft.Agents.Builder.Dialogs` |
| `using Microsoft.Bot.Schema;` | `using Microsoft.Agents.Core.Models;` |
| `Microsoft.Bot.Connector.Authentication` | `Microsoft.Agents.Connector` |
| `using Microsoft.Bot.Builder.Teams;` | `using Microsoft.Agents.Extensions.Teams.Compat;` |
| `using Microsoft.Bot.Schema.Teams;` | `using Microsoft.Agents.Extensions.Teams.Models;` |
| `using Newtonsoft.Json;` | `using System.Text.Json;` |
| `using Newtonsoft.Json.Linq;` | Remove entirely |

| Bot Framework Teams Namespace | Agents SDK Namespace |
| --- | --- |
| [Microsoft.Bot.Builder.Teams](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.teams) | [Microsoft.Agents.Extensions.Teams.Compat](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.extensions.teams.compat) |
| [Microsoft.Bot.Schema.Teams](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.schema.teams) | [Microsoft.Agents.Extensions.Teams.Models](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.extensions.teams.models) |

Some types and properties were renamed in the Agents SDK. Use the following mappings to guide changes.

| Bot Framework | Agents SDK |
| --- | --- |
| [BotState](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.botstate) | [AgentState](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.agentstate) |
| [OAuthPromptSettings.ConnectionName](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.dialogs.oauthpromptsettings.connectionname) | [OAuthPromptSettings.AzureBotOAuthConnectionName](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.userauth.tokenservice.oauthsettings.azurebotoauthconnectionname) |
| [IAttachments.GetAttachmentInfoWithHttpMessagesAsync](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.connector.iattachments.getattachmentinfowithhttpmessagesasync) | [IAttachments.GetAttachmentInfoAsync](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.connector.iattachments.getattachmentinfoasync) |
| [IBotFrameworkHttpAdapter](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.integration.aspnet.core.ibotframeworkhttpadapter) | [IAgentHttpAdapter](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.hosting.aspnetcore.iagenthttpadapter) |
| [BotAdapter](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.botadapter) | [ChannelAdapter](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.channeladapter) |
| [CloudAdapterBase](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.cloudadapterbase) | [ChannelServiceAdapterBase](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.channelserviceadapterbase) |

Update common `TurnState` references. Replace the following usages accordingly.

| Bot Framework Namespace | Agents SDK Namespace |
| --- | --- |
| `TurnState.Get<ConnectorClient>` | `.Services.Get<IConnectorClient>` |
| `.TurnState.Get<IUserTokenClient>` | `.Services.Get<IUserTokenClient>` |
| `.TurnState.` | `.Services.` |

Initialization differs slightly in the Agents SDK. Many Bot Framework samples register dependency injection in `Startup.cs` and reference it from `Program.cs`. With the Agents SDK, consolidate this setup in `Program.cs` for a simpler minimal-API style configuration.

Authentication also changes. The Bot Framework SDK included incoming JSON Web Token \(JWT\) authentication in its hosting stack, but the Agents SDK leaves HTTP authentication to ASP.NET. Copy [AspNetExtensions](https://github.com/microsoft/Agents/blob/main/samples/dotnet/quickstart/AspNetExtensions.cs) into your project to enable ASP.NET authentication for incoming requests.

### Architectural notes and compatibility

Remove deprecated services and artifacts as part of the migration. LUIS and QnA Maker are retired, so replace any remaining usage with supported approaches such as Azure OpenAI with retrieval. The Agents SDK doesn't support Composer/Adaptive Dialogs and LG/Adaptive Expressions, so you should remove the related assets.

Dialogs remain available under `Microsoft.Agents.Builder.Dialogs` for compatibility. They continue to work and are a practical bridge during migration, but plan refactors toward more modern orchestration patterns where it makes sense.

Middleware is still supported; however, the SDK also exposes turn lifecycle hooks. Prefer small before/after turn logic when possible. If you're not ready to refactor, you can continue to register existing `IMiddleware` implementations via dependency injection.

Paste the following code into your `Program.cs`, replacing the current contents.

```csharp
using Microsoft.Agents.Builder;
using Microsoft.Agents.Builder.State;
using Microsoft.Agents.Hosting.AspNetCore;
using Microsoft.Agents.Storage;
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.DependencyInjection;
using System.Threading;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddHttpClient();

// Register your bot. 
// A Dialog based bot would look something like:
// builder.AddAgent<MyBot<MainDialog>>();
// 
// If you used custom (CloudAdapter subclass):
// builder.AddAgent<MyBot, MyAdapter>();
builder.AddAgent<MyBot>();

// This is the same as in BF SDK and can be replaced with what you had in Startup.cs
builder.Services.AddSingleton<IStorage, MemoryStorage>();

builder.Services.AddSingleton<ConversationState>();
builder.Services.AddSingleton<UserState>();

// If you are using dialogs, copy your equivalent from Startup.cs
builder.Services.AddSingleton<MainDialog>();

// Perform any other DI included in your Startup.cs
// Do not include:
//    services.AddSingleton<BotFrameworkAuthentication, ConfigurationBotFrameworkAuthentication>();
//    services.AddSingleton<IBotFrameworkHttpAdapter, ???>();
//    services.AddTransient<IBot, ???>();
//    services.AddSingleton<ServiceClientCredentialsFactory>(...)
//    services.AddHttpClient().AddControllers().AddNewtonsoftJson

// Configure the HTTP request pipeline.

// Add AspNet token validation for Azure Bot Service and Entra. Authentication is
// configured in the appsettings.json "TokenValidation" section.
builder.Services.AddControllers();
builder.Services.AddAgentAspNetAuthentication(builder.Configuration);

var app = builder.Build();

// Enable AspNet authentication and authorization
app.UseAuthentication();
app.UseAuthorization();

app.MapPost("/api/messages", 
async (HttpRequest request, 
       HttpResponse response, 
       IAgentHttpAdapter adapter, 
       IAgent agent, 
       CancellationToken cancellationToken) =>
{
    await adapter.ProcessAsync(request, response, agent, cancellationToken);
}).RequireAuthorization(); ;

app.Run();
```

### appsettings

Reference your existing appsettings and add the following sections. First, configure TokenValidation so ASP.NET can validate incoming requests.

```json
"TokenValidation": {
  "Enabled": true,
  "Audiences": [
    "{{MicrosoftAppId-value}}"
  ],
  "TenantId": "{{MicrosoftTenantId-value}}"
},
```

> See the comments in [AspNetExtensions](https://github.com/microsoft/Agents/blob/main/samples/dotnet/quickstart/AspNetExtensions.cs) for details on all available settings.

Next, define Connections. The following sample shows a single-tenant configuration using client secrets.

```json
"Connections": {
  "ServiceConnection": {
    "Settings": {
      "AuthType": "ClientSecret",
      "AuthorityEndpoint": "https://login.microsoftonline.com/{{MicrosoftTenantId-value}}",
      "ClientId": "{{MicrosoftAppId-value}}",
      "ClientSecret": "{{MicrosoftAppPassword-value}}",
      "Scopes": [
        "https://api.botframework.com/.default"
      ]
    }
  }
},
"ConnectionsMap": [
  {
    "ServiceUrl": "*",
    "Connection": "ServiceConnection"
  }
],
```

> See [Configure authentication in a .NET agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/microsoft-authentication-library-configuration-options) for details on different authentication settings.

## Serialization changes

Some [`TeamsActivityHandler`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.bot.builder.teams.teamsactivityhandler) methods that previously required `JObject` now expect [`JsonElement`](https://learn.microsoft.com/en-us/dotnet/api/system.text.json.jsonelement). Also remove `builder.Services.AddControllers().AddNewtonsoftJson();` from Program.cs unless you explicitly need it for unrelated code paths; the Agents SDK doesn't require it.

Attachment and Teams schemas moved to `Microsoft.Agents.Core.Models` and `Microsoft.Agents.Extensions.Teams.Models`. If you parsed raw JSON with Newtonsoft in the past, update that logic to use `System.Text.Json` equivalents.

## State

[`ConversationState`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.conversationstate), [`UserState`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.userstate), and [`PrivateConversationState`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.privateconversationstate) are compatible with a few differences. [`IStatePropertyAccessor`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.istatepropertyaccessor-1) is deprecated—though still functional—so prefer the [`IAgentState`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.iagentstate) methods going forward.

[`Dialog.RunAsync`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.dialogs.dialogextensions.runasync) continues to accept an `IStatePropertyAccessor` but also supports passing [`AgentState`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.state.agentstate) or derived types such as `ConversationState`, `UserState`, and `PrivateConversationState`. Passing one of these state objects directly is recommended.

[`AutoSaveStateMiddleware`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.compat.autosavestatemiddleware) are enhanced to automatically load and save state. Don't use it with [`AgentApplication`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.agentapplication)-based agents. For [`ActivityHandler`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.compat.activityhandler)-based agents, you can add it to your adapter to auto load/save all state:

```csharp
adapter.Use(new AutoSaveStateMiddleware(true, conversationState, userState));
```

## Troubleshooting and tips

The following tips might help you be more successful.

### NuGet restore failures

If NuGet restore fails, remove deprecated Bot Framework preview feeds from NuGet.config and ensure only nuget.org \(or your approved artifact feed\) is configured.

### Ambiguous interfaces

If you encounter ambiguous interfaces—such as `IMiddleware` or `IStorage`—fully qualify the Agents SDK types \(for example, use `Microsoft.Agents.Storage.IStorage`\).

### Accessing turn-scoped services

When accessing turn-scoped services, replace `TurnContext.TurnState` usages with `TurnContext.Services`. For example, retrieve `IConnectorClient` or `IUserTokenClient` through `.Services.Get<T>()`.

### JSON migration \(System.Text.Json\)

For JSON migration, replace any `JObject`/`JToken` logic with `JsonDocument`/`JsonElement` from `System.Text.Json`.

### Local 401s during debugging

If you see 401s during local debugging, either supply your App ID and secret in the Emulator, or temporarily remove `.RequireAuthorization()` while you diagnose authentication.

## Migration checklist

✓ **Analyze and plan**: Identify unsupported features \(Composer, LUIS/QnA\) and decide to migrate vs. rebuild scope.  
✓ **Upgrade .NET target**: Move to net6.0 or net8.0 across projects.  
✓ **Replace packages**: Remove `Microsoft.Bot.*`; add `Microsoft.Agents.*` \(Builder, Core, Hosting.AspNetCore, Authentication.Msal, Storage providers, Teams/Teams.Compat\).  
✓ **Update namespaces and types**: Apply find/replace per the tables above; fix renamed APIs.  
✓ **`Program.cs`**: Register your agent via `builder.AddAgent<T>()`, state/storage, and call `AddAgentAspNetAuthentication`; map `/api/messages` with authorization.  
✓ **Middleware**: Prefer turn events; if needed, register existing `IMiddleware` via DI.  
✓ **Build and test locally**: Use the Emulator with credentials; validate core scenarios and Teams behaviors.  
✓ **Deploy and monitor**: Update app settings in Azure to match the new configuration and watch logs after rollout.

## Related Content

- [Azure Bot Framework SDK to Agents SDK migration guidance](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-guidance)
- [Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for nodejs](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-nodejs)
- [Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for Python](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-python)
