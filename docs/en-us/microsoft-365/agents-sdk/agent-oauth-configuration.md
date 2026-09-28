<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-oauth-configuration -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Configure your agent to use OAuth

An agent uses OAuth to sign users in and get tokens for downstream resources \(such as Microsoft Graph\) without handling credentials itself. Azure Bot Service manages the token exchange, and the agent retrieves the resulting user token during a turn.

## Overview

Using OAuth in an agent involves three activities:

1. **Configure OAuth on the Azure Bot and app registration**: Create one or more OAuth connections on your Azure Bot resource, each backed by a Microsoft Entra ID app registration. [Add user authorization using federated identity credential](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/azure-bot-user-authorization-federated-credentials) covers the most common approach. Other credential types, such as client secrets or certificates, are also supported. For the full set of options, see [Bot Service authentication basics](https://learn.microsoft.com/en-us/azure/bot-service/bot-builder-concept-authentication?view=azure-bot-service-4.0&preserve-view=true).
2. **Configure the matching settings in the agent**: Each OAuth connection on the Azure Bot maps to one OAuth handler in the agent's configuration. See [Settings](#settings). For general agent setup, see [What is the Microsoft 365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview).
3. **Use the tokens in code**: During a turn, retrieve the user token—or perform an On-Behalf-Of \(OBO\) exchange—through the agent's user authorization API. See [Use the token in code \(non-OBO\)](#use-the-token-in-code-non-obo) and [Use the token in code \(OBO\)](#use-the-token-in-code-obo).

Keep the following concepts in mind as you read the rest of this article:

- **An Azure Bot can contain multiple OAuth connections.** For example, one connection for Microsoft Graph and another for GitHub. Each connection is configured independently on the Azure Bot.
- **There's a 1:1 relationship between an OAuth connection on the Azure Bot and an OAuth handler in the agent.** A handler's `AzureBotOAuthConnectionName` setting names the Azure Bot connection it uses. To use two connections, define two handlers.
- **The agent's user authorization API is the surface you call in code.** In .NET this is `AgentApplication.UserAuthorization`—for example, `GetTurnTokenAsync` to read a token and `ExchangeTurnTokenAsync` to perform an OBO exchange. The equivalent surfaces are `authorization` in JavaScript and `auth` in Python.

For working samples, see the auto sign-in and OBO samples for:

- [.NET](https://github.com/microsoft/Agents/tree/main/samples/dotnet/auto-signin)
- [JavaScript](https://github.com/microsoft/Agents/tree/main/samples/nodejs/auto-signin)
- [Python](https://github.com/microsoft/Agents/tree/main/samples/python/auto-signin).

## Language support for OAuth

The Agents SDK supports OAuth for .NET, JavaScript, and Python. The core concepts are the same in every language: OAuth handlers, attaching handlers to routes, and OBO exchange. Only the configuration format and the handler API names differ:

| Language | Where you configure | API surface |
| --- | --- | --- |
| .NET | `appsettings.json` \(or code in `Program.cs`\) | `AgentApplication.UserAuthorization` |
| JavaScript | `.env` environment variables | `AgentApplication.authorization` |
| Python | `.env` environment variables | `AgentApplication.auth` |

For JavaScript and Python, the `.env` keys use the same hierarchical names as the .NET `appsettings.json` structure, with each level separated by a double underscore \(`__`\). JavaScript keys keep the camel‑cased leaf names shown in the tables \(for example, `azureBotOAuthConnectionName`\). Python keys are upper‑cased \(for example, `AZUREBOTOAUTHCONNECTIONNAME`\).

Important

Global auto sign-in \(`AutoSignIn`\) and `DefaultHandlerName` are supported only in .NET. In JavaScript and Python, you attach OAuth handlers to specific routes, as shown in [Per-route configuration](#per-route-configuration).

## Settings

A user authorization object inside `AgentApplication` controls how the agent acquires user tokens. At minimum, each handler names the Azure Bot OAuth connection it uses. The following examples show the minimal structure in each language. The [tables that follow](#userauthorization-properties) describe the rest of the available properties, and the [OBO sections](#use-the-token-in-code-obo) cover the `OBOConnectionName` and `OBOScopes` settings.

In .NET, configure user authorization under `AgentApplication` in `appsettings.json`:

```json
  "AgentApplication": {
    "UserAuthorization": {
      "DefaultHandlerName": "{{handler-name}}",
      "AutoSignIn": true | false,
      "Handlers": {
        "{{handler-name}}": {
          "Settings": {
            "AzureBotOAuthConnectionName": "{{azure-bot-connection-name}}"
          }
        }
      }
    }
  }
```

In JavaScript, configure user authorization with environment variables in the `.env` file:

```ini
# Connection used to authenticate the agent itself
connections__serviceConnection__settings__clientId=
connections__serviceConnection__settings__clientSecret=
connections__serviceConnection__settings__tenantId=
connectionsMap__0__connection=serviceConnection
connectionsMap__0__serviceUrl=*

# OAuth handler named "{{handler-name}}"
AgentApplication__UserAuthorization__Handlers__{{handler-name}}__Settings__azureBotOAuthConnectionName={{azure-bot-connection-name}}
```

In Python, configure user authorization with environment variables in the `.env` file:

```ini
# Connection used to authenticate the agent itself
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID=
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET=
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID=

# OAuth handler named "{{handler-name}}"
AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__{{handler-name}}__SETTINGS__AZUREBOTOAUTHCONNECTIONNAME={{azure-bot-connection-name}}
```

### UserAuthorization properties

The following table lists the top-level `UserAuthorization` properties that determine how handlers are selected and how tokens are acquired for each incoming activity.

| Property | Required | Type | Description |
| --- | --- | --- | --- |
| `DefaultHandlerName` | No \(recommended\) | string | .NET only. Name of the handler used when `AutoSignIn` evaluates to true and no per‑route override is specified. |
| `AutoSignIn` | No | bool or delegate | .NET only. When true \(default\), the agent attempts to acquire a token for every incoming activity. Override at runtime with `Options.AutoSignIn` to filter activity types. |
| `Handlers` | Yes \(at least one\) | object \(dictionary\) | Mapping of handler name to its configuration. Each key must be unique. |

In .NET, to restrict which activities auto sign-in applies to, set a predicate similar to: `Options.AutoSignIn = (context, ct) => Task.FromResult(context.Activity.IsType(ActivityTypes.Message));`. JavaScript and Python don't support global auto sign-in. Instead, scope sign-in by attaching specific handler names to individual routes, as shown in the [per-route](#per-route-configuration) examples.

### Settings properties

The following table describes the nested `Settings` object applied to an individual OAuth handler, controlling sign-in card presentation, retry behavior, timeouts, and optional OBO exchange configuration.

| Property | Required | Type | Description |
| --- | --- | --- | --- |
| `AzureBotOAuthConnectionName` | Yes | string | OAuth connection name defined on the Azure Bot resource. |
| `OBOConnectionName` | No \(OBO only\) | string | Name of an Agents SDK connection used to perform an On‑Behalf‑Of token exchange. |
| `OBOScopes` | No \(OBO only\) | string\[\] | Scopes requested during OBO exchange. If omitted with `OBOConnectionName`, you can call [ExchangeTurnTokenAsync](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.userauth.userauthorization.exchangeturntokenasync) manually. |
| `Title` | No | string | Custom sign‑in card title. Defaults to **Sign In**. |
| `Text` | No | string | Sign‑in card button text. Defaults to **Please sign in**. |
| `InvalidSignInRetryMax` | No | int | Maximum number of retries allowed when user enters an invalid code. Default is 2. |
| `InvalidSignInRetryMessage` | No | string | Message shown after an invalid code entry. Defaults to **Invalid sign in code. Please enter the 6-digit code.** |
| `Timeout` | No | int \(ms\) | Number of milliseconds before an in‑progress sign‑in attempt expires. The default is 900000 \(15 minutes\). |

Note

`AzureBotOAuthConnectionName`, `OBOConnectionName`, `OBOScopes`, `Title`, and `Text` apply to all three languages \(using the per-language key casing described in [Language support for OAuth](#language-support-for-oauth)\). `InvalidSignInRetryMax`, `InvalidSignInRetryMessage`, and `Timeout` are .NET settings.

## What type should you use?

Use the following table to decide which approach fits your scenario.

| Choice | Use when |
| --- | --- |
| Auto sign-in \(.NET only\) | You want every incoming activity to automatically acquire a token, or you want a filtered subset \(for example, only messages or everything except events\) by supplying a predicate to [UserAuthorizationOptions.AutoSignIn](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.userauth.userauthorizationoptions.autosignin). Supported only in .NET. |
| Per-route | Only specific route handlers need tokens or different routes must use different OAuth connections \(and therefore different tokens\). This option is the only option in JavaScript and Python. In .NET, it's additive with global auto sign-in. If both are enabled in .NET, the turn has access to tokens from each. |

## Use the token in code \(non-OBO\)

This section shows how to retrieve and use the user token directly returned by your Azure Bot OAuth connection without performing an On‑Behalf‑Of exchange. In .NET, you can use global auto sign-in or per‑route handlers. JavaScript and Python use per‑route handlers only. Inside your activity handler, retrieve the token \(`GetTurnTokenAsync` in .NET, `authorization.getToken` in JavaScript, `auth.get_token` in Python\) as late as possible so that the SDK can refresh the token if it's near expiry. The following examples illustrate both patterns.

### Auto sign-in \(.NET only\)

Note

Global auto sign-in and `DefaultHandlerName` are available only in .NET. For JavaScript and Python, use [Per-route configuration](#per-route-configuration).

Use this configuration when global auto sign-in should acquire a token for every incoming activity without needing to specify per‑route handlers.

```json
  "AgentApplication": {
    "UserAuthorization": {
      "DefaultHandlerName": "auto",
      "Handlers": {
        "auto": {
          "Settings": {
            "AzureBotOAuthConnectionName": "teams_sso",
          }
        }
      }
    }
  },
```

Your agent code would look something like this:

```csharp
public class MyAgent : AgentApplication
{
    [MessageRoute]
    public async Task OnMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        var token = await UserAuthorization.GetTurnTokenAsync(turnContext);

        // use the token 
    }
}
```

### Per-route configuration

Use a per-route configuration when you want fine-grained control: only the routes you explicitly mark acquire tokens. Per-route configuration has the following advantages:

- It reduces unnecessary token retrieval.
- It allows different routes to target distinct OAuth connections \(and therefore different resources or scopes\).
- It lets you mix authenticated and unauthenticated routes within the same agent.

In the following example, a single `graph` handler is attached only to the message route.

In .NET, global auto sign-in is disabled and the `graph` handler is attached to the route by using `autoSignInHandlers`.

```json
  "AgentApplication": {
    "UserAuthorization": {
      "AutoSignIn": false,
      "Handlers": {
        "graph": {
          "Settings": {
            "AzureBotOAuthConnectionName": "teams_sso",
          }
        }
      }
    }
  },
```

Your agent code would look something like this:

```csharp
public class MyAgent : AgentApplication
{
    [MessageRoute(autoSignInHandlers: "graph")]
    public async Task OnMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        var token = await UserAuthorization.GetTurnTokenAsync(turnContext, "graph");

        // use the token
    }
}
```

In JavaScript, pass an array of handler names as the last argument to the route registration. Only that route triggers sign-in for the `graph` handler.

```ini
AgentApplication__UserAuthorization__Handlers__graph__Settings__azureBotOAuthConnectionName=teams_sso
AgentApplication__UserAuthorization__Handlers__graph__Settings__title=Graph Sign In
AgentApplication__UserAuthorization__Handlers__graph__Settings__text=Sign in with Microsoft Graph
```

Your agent code would look something like this:

```javascript
class MyAgent extends AgentApplication {
  constructor () {
    super({ storage: new MemoryStorage() })
    // the `graph` handler runs only for this route
    this.onMessage('-me', this._profileRequest, ['graph'])
  }

  private _profileRequest = async (context, state) => {
    const tokenResponse = await this.authorization.getToken(context, 'graph')

    // use tokenResponse.token
  }
}
```

In Python, pass `auth_handlers` to the route decorator. Only that route triggers sign-in for the `GRAPH` handler.

```ini
AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__GRAPH__SETTINGS__AZUREBOTOAUTHCONNECTIONNAME=teams_sso
```

Your agent code would look something like this:

```python
@AGENT_APP.message(re.compile(r"^/(me|profile)$", re.IGNORECASE), auth_handlers=["GRAPH"])
async def profile_request(context: TurnContext, state: TurnState) -> None:
    token_response = await AGENT_APP.auth.get_token(context, "GRAPH")

    # use token_response.token
```

### Retrieve the token during a turn

Retrieve the user token whenever you need it during a turn. You can call it multiple times. Call it immediately before use so that refresh logic \(if necessary\) is handled transparently.

| Language | Call |
| --- | --- |
| .NET | [GetTurnTokenAsync](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.userauth.userauthorization.getturntokenasync)`(turnContext, handlerName)` |
| JavaScript | `authorization.getToken(context, handlerName)` |
| Python | `auth.get_token(context, handler_name)` |

## Use the token in code \(OBO\)

On-Behalf-Of \(OBO\) relies on the initial user sign-in returning an exchangeable token. That requires the OAuth connection's scopes to include one that corresponds to a scope exposed by the downstream API \(for example if the exposed scope is `defaultScopes`, the configured scope might be `api://botid-{{clientId}}/defaultScopes`\). The Agents SDK then performs a Microsoft Authentication Library \(MSAL\) exchange using a configured connection identified by `OBOConnectionName` and the list of `OBOScopes`. When both `OBOConnectionName` and `OBOScopes` are present in configuration the exchange occurs automatically, and you obtain the final token through the standard token call \(`GetTurnTokenAsync` / `getToken` / `get_token`\). If either is missing you can perform the exchange explicitly at runtime \(`ExchangeTurnTokenAsync` in .NET, `authorization.exchangeToken` in JavaScript, `auth.exchange_token` in Python\), allowing you to resolve the connection or scope list dynamically.

### OBO in config

Use this pattern when you know the downstream resource and scopes you need at configuration time. When you provide both `OBOConnectionName` and `OBOScopes`, the SDK automatically performs the On‑Behalf‑Of exchange during sign-in. This means subsequent calls to the standard token getter return the OBO token directly with no extra runtime code needed.

```json
  "AgentApplication": {
    "UserAuthorization": {
      "AutoSignIn": false,
      "Handlers": {
        "graph": {
          "Settings": {
            "AzureBotOAuthConnectionName": "teams_sso",
            "OBOConnectionName": "ServiceConnection",
            "OBOScopes": [
              "https://graph.microsoft.com/.default"
            ]
          }
        }
      }
    }
  },
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "FederatedCredentials",
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{TenantId}}",
        "ClientId": "{{ClientId}}",
        "FederatedClientId": "{{ManagedIdentityClientId}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  },
```

Your agent code would look something like this:

```csharp
public class MyAgent : AgentApplication
{
    [MessageRoute(autoSignInHandlers: "graph")]
    public async Task OnMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        // returns the OBO token because OBOConnectionName and OBOScopes are configured
        var token = await UserAuthorization.GetTurnTokenAsync(turnContext, "graph");

        // use the token
    }
}
```

In JavaScript, define an OBO connection in the connections map and reference it from the handler with `oboConnectionName` and `oboScopes`.

```ini
# Agent's own connection
connections__serviceConnection__settings__clientId=
connections__serviceConnection__settings__clientSecret=
connections__serviceConnection__settings__tenantId=

# OBO connection
connections__oboConnection__settings__clientId=
connections__oboConnection__settings__clientSecret=
connections__oboConnection__settings__tenantId=

connectionsMap__0__connection=serviceConnection
connectionsMap__0__serviceUrl=*
connectionsMap__1__connection=oboConnection
connectionsMap__1__serviceUrl=obo

AgentApplication__UserAuthorization__Handlers__graph__Settings__azureBotOAuthConnectionName=teams_sso
AgentApplication__UserAuthorization__Handlers__graph__Settings__oboConnectionName=oboConnection
AgentApplication__UserAuthorization__Handlers__graph__Settings__oboScopes=https://graph.microsoft.com/.default
```

Your agent code would look something like this:

```javascript
class MyAgent extends AgentApplication {
  constructor () {
    super({ storage: new MemoryStorage() })
    this.onActivity('message', this._onMessage, ['graph'])
  }

  private _onMessage = async (context, state) => {
    // returns the OBO token because oboConnectionName and oboScopes are configured
    const tokenResponse = await this.authorization.getToken(context, 'graph')

    // use tokenResponse.token
  }
}
```

In Python, define an OBO connection under `CONNECTIONS` and reference it from the handler with `OBOCONNECTIONNAME` and `OBOSCOPES`.

```ini
# Agent's own connection
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID=
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET=
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID=

# OBO connection
CONNECTIONS__OBO__SETTINGS__CLIENTID=
CONNECTIONS__OBO__SETTINGS__CLIENTSECRET=
CONNECTIONS__OBO__SETTINGS__TENANTID=

AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__GRAPH__SETTINGS__AZUREBOTOAUTHCONNECTIONNAME=teams_sso
AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__GRAPH__SETTINGS__OBOCONNECTIONNAME=OBO
AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__GRAPH__SETTINGS__OBOSCOPES=https://graph.microsoft.com/.default
```

Your agent code would look something like this:

```python
@AGENT_APP.message(re.compile(r".*"), auth_handlers=["GRAPH"])
async def on_message(context: TurnContext, state: TurnState) -> None:
    # returns the OBO token because OBOCONNECTIONNAME and OBOSCOPES are configured
    token_response = await AGENT_APP.auth.get_token(context, "GRAPH")

    # use token_response.token
```

### OBO Exchange at runtime

Use a runtime exchange when you can't fix the downstream resource, scopes, or connection in the configuration. This situation happens, for example, when scopes depend on tenant, user role, or a feature flag. In this model, you optionally configure the OBO connection, then call the exchange method with the scopes you decide at turn time. You receive an exchanged token that you can immediately apply.

Call [ExchangeTurnTokenAsync](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.userauth.userauthorization.exchangeturntokenasync) with the scopes you decide at turn time.

```json
  "AgentApplication": {
    "UserAuthorization": {
      "AutoSignIn": false,
      "Handlers": {
        "graph": {
          "Settings": {
            "AzureBotOAuthConnectionName": "teams_sso",
            "OBOConnectionName": "ServiceConnection"
          }
        }
      }
    }
  },
  "Connections": {
    "ServiceConnection": {
      "Settings": {
        "AuthType": "FederatedCredentials",
        "AuthorityEndpoint": "https://login.microsoftonline.com/{{TenantId}}",
        "ClientId": "{{ClientId}}",
        "FederatedClientId": "{{ManagedIdentityClientId}}",
        "Scopes": [
          "https://api.botframework.com/.default"
        ]
      }
    }
  },
```

Your agent code would look something like this:

```csharp
public class MyAgent : AgentApplication
{
    [MessageRoute(autoSignInHandlers: "graph")]
    public async Task OnMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        var scopes = GetScopes();

        var exchangedToken = await UserAuthorization.ExchangeTurnTokenAsync(turnContext, "graph", exchangeScopes: scopes);

        // use the token
    }
}
```

Call `authorization.exchangeToken` with the handler name and the scopes you decide at turn time.

```ini
connections__oboConnection__settings__clientId=
connections__oboConnection__settings__clientSecret=
connections__oboConnection__settings__tenantId=

connectionsMap__1__connection=oboConnection
connectionsMap__1__serviceUrl=obo

AgentApplication__UserAuthorization__Handlers__graph__Settings__azureBotOAuthConnectionName=teams_sso
AgentApplication__UserAuthorization__Handlers__graph__Settings__oboConnectionName=oboConnection
```

Your agent code would look something like this:

```javascript
class MyAgent extends AgentApplication {
  constructor () {
    super({ storage: new MemoryStorage() })
    this.onActivity('message', this._onMessage, ['graph'])
  }

  private _onMessage = async (context, state) => {
    const scopes = getScopes()
    const exchangedToken = await this.authorization.exchangeToken(context, 'graph', { scopes })

    // use exchangedToken.token
  }
}
```

Call `auth.exchange_token` with the scopes you decide at turn time and the handler name.

```ini
CONNECTIONS__MCS__SETTINGS__CLIENTID=
CONNECTIONS__MCS__SETTINGS__CLIENTSECRET=
CONNECTIONS__MCS__SETTINGS__TENANTID=

AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__MCS__SETTINGS__AZUREBOTOAUTHCONNECTIONNAME=teams_sso
AGENTAPPLICATION__USERAUTHORIZATION__HANDLERS__MCS__SETTINGS__OBOCONNECTIONNAME=MCS
```

Your agent code would look something like this:

```python
@AGENT_APP.message(re.compile(r".*"), auth_handlers=["MCS"])
async def on_message(context: TurnContext, state: TurnState) -> None:
    scopes = get_scopes()
    token_response = await AGENT_APP.auth.exchange_token(context, scopes, "MCS")

    # use token_response.token
```

### Regional OAuth settings

For non-US regions, update the token service endpoint that your agent uses.

The following example shows the .NET configuration. Add it to `appsettings.json`:

```csharp
"RestChannelServiceClientFactory": {
   "TokenServiceEndpoint": "{{service-endpoint-uri}}"
}
```

For `service-endpoint-url`, use the appropriate value from the following table for public-cloud bots with data residency in the specified region.

| URI | Region |
| --- | --- |
| `https://europe.api.botframework.com` | Europe |
| `https://unitedstates.api.botframework.com` | United States |
| `https://india.api.botframework.com` | India |
