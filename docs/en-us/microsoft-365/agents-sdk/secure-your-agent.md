<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/secure-your-agent -->
<!-- Sitemap-Last-Modified: 2026-08-29 -->

# Secure your agent for production

An agent is a web service that receives untrusted input from channels and users, and makes outbound, often token-bearing, calls back to those channels and to downstream services. Securing an agent means defending both directions of that traffic.

This guide covers complementary controls that form a defense-in-depth posture:

| Control | Direction | Protects against |
| --- | --- | --- |
| [Inbound token validation](#validate-inbound-requests) | Inbound | Unauthenticated requests and spoofed callers |
| [Caller authorization](#restrict-which-callers-can-reach-your-agent) | Inbound | Authenticated but unauthorized callers |
| [Service URL validation](#validate-the-service-url) | Outbound | Spoofed activity service URLs and confused-deputy attacks |
| [Outbound host allow list](#restrict-outbound-hosts) | Outbound | Server-side request forgery \(SSRF\) and token exfiltration |

Important

Outbound host validation is opt-in and disabled by default to preserve backward compatibility. Enable it explicitly for production agents that handle sensitive tokens.

## Prerequisites

- A Python agent built with `microsoft-agents-hosting-core` and either `microsoft-agents-hosting-fastapi` or `microsoft-agents-hosting-aiohttp`. See the [Quickstart](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart).
- An Azure Bot resource and its Microsoft Entra app registration \(Client ID and Tenant ID\). See [Provision Azure Bot Service resources manually](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually).

- A Node.js agent built with `@microsoft/agents-hosting`. See the [Quickstart](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart).
- An Azure Bot resource and its Microsoft Entra app registration \(Client ID and Tenant ID\). See [Provision Azure Bot Service resources manually](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually).

- A .NET agent built with `Microsoft.Agents.Hosting.AspNetCore` and `Microsoft.Agents.Builder`. See the [Quickstart](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart).
- An Azure Bot resource and its Microsoft Entra app registration \(Client ID and Tenant ID\). See [Provision Azure Bot Service resources manually](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually).

## Validate inbound requests

Every request to your agent's messaging endpoint must include a valid JWT bearer token issued by Azure Bot Service or a trusted Microsoft Entra tenant.

Configure the agent connection and apply JWT authorization to the messaging endpoint. FastAPI provides a `jwt_authorization_decorator` used to decorate individual FastAPI route handlers and a `JwtAuthorizationMiddleware` class that can be applied via `add_middleware` to a FastAPI object. Meanwhile, the aiohttp hosting package similarly provides a `jwt_authorization_decorator` function used on each aiohttp route handler and a `jwt_authorization_middleware` that can be applied as middleware to an aiohttp `Application` object.

```python
app = FastAPI(title="Agent Sample", version="1.0.0")
app.state.agent_configuration = (
    connection_manager.get_default_connection_configuration()
)


@app.post("/api/messages")
@jwt_authorization_decorator
async def messages_handler(request: Request):
    """Main endpoint for processing bot messages."""
    return await start_agent_process(
        request,
        agent_app,
        agent_app.adapter,
    )
```

or

```python
app = FastAPI(title="Agent Sample", version="1.0.0")
app.add_middleware(JwtAuthorizationMiddleware)
app.state.agent_configuration = (
    connection_manager.get_default_connection_configuration()
)

@app.post("/api/messages")
async def messages_handler(request: Request):
    """Main endpoint for processing bot messages."""
    return await start_agent_process(
        request,
        agent_app,
        agent_app.adapter,
    )
```

Anonymous access is disabled by default. Keep `ANONYMOUS_ALLOWED` set to `false` in production. Set `CONNECTIONS__SERVICE_CONNECTION__SETTINGS__VALIDATE_ISSUER=true` to require the token issuer to match the connection's configured or tenant-derived issuer allow list.

For complete connection settings, see [Configure authentication in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal).

Load the authentication configuration and apply `authorizeJWT` to the messaging endpoint before the adapter processes the activity:

```typescript
import {
  AgentApplication,
  authorizeJWT,
  CloudAdapter,
  loadAuthConfigFromEnv
} from '@microsoft/agents-hosting'

const authConfig = loadAuthConfigFromEnv()
const adapter = new CloudAdapter(authConfig)
const agent = new AgentApplication({ adapter })

server.post(
  '/api/messages',
  authorizeJWT(authConfig),
  (req, res) => adapter.process(req, res, (context) => agent.run(context))
)
```

Set `CONNECTIONS__SERVICE_CONNECTION__SETTINGS__VALIDATEISSUER=true` to require the token issuer to match the connection's configured or tenant-derived issuer allow list.

Configure the connection-map audience as the exact Client ID of the agent. Do not use a wildcard audience. Validate the complete production authentication configuration at startup and stop startup when the client ID, tenant ID, audience, issuer validation, or connection mapping is missing or unsafe.

Use `startServer` or `createAgentRequestHandler` when the helper's complete HTTP pipeline fits your application. These helpers already apply JWT authorization. Don't add `authorizeJWT` a second time. Use an explicit adapter pipeline when caller or channel authorization must run between JWT validation and activity processing.

For an explicit Express pipeline, keep this order:

1. Apply a bounded JSON parser before the route.
2. Apply `authorizeJWT`.
3. Apply caller authorization when the scenario requires it.
4. Call `adapter.process`, where the enabled outbound validator checks the service URL claim and host allow list.
5. Handle errors after the route and return generic client responses.

Keep health endpoints anonymous and read-only. Protect every other endpoint that changes data, sends messages, or calls a downstream API.

For complete connection settings, see [Configure authentication in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal).

The SDK samples wire up inbound validation by using the `AddAgentAspNetAuthentication` extension method from the shared [`AspNetExtensions.cs`](https://github.com/microsoft/Agents-for-net/blob/main/src/samples/Shared/AspNetExtensions.cs) sample. Add this file to your project to configure ASP.NET Core JWT bearer authentication from a `TokenValidation` configuration section.

Note

`AspNetExtensions` isn't part of the Agents SDK or its NuGet packages. It's a sample-provided mechanism for JWT token validation that you copy into and maintain with your agent project.

Add the configuration section to *appsettings.json*:

```json
"TokenValidation": {
  "Audiences": [ "{{ClientId}}" ],
  "TenantId": "{{TenantId}}"
}
```

Register authentication and require it on the agent endpoints in *Program.cs*:

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.AddAgentDefaults()
    .AddAgent<MyAgent>()
    .AddAgentAuthorization(b => b.AddAgentAspNetAuthentication());

WebApplication app = builder.Build();
app.UseAgents();
app.MapDefaultAgentEndpoints();
app.Run();
```

### Understand the authentication extensions

The .NET quickstart registers authentication through `AddAgentAuthorization` and adds the Agents middleware to the request pipeline:

```csharp
using QuickStart;
using Microsoft.Agents.Hosting.AspNetCore;
using Microsoft.Agents.Storage;
using Microsoft.AspNetCore.Builder;
using Microsoft.Extensions.DependencyInjection;

WebApplicationBuilder builder = WebApplication.CreateBuilder(args);

// Add the AgentApplication, which contains the logic for responding to
// user messages.
builder.AddAgentDefaults()
    .AddAgent<MyAgent>()
    .AddAgentAuthorization(b => b.AddAgentAspNetAuthentication());

// Register IStorage.  For development, MemoryStorage is suitable.
// For production Agents, persisted storage should be used so
// that state survives Agent restarts, and operates correctly
// in a cluster of Agent instances.
builder.Services.AddSingleton<IStorage, MemoryStorage>();

WebApplication app = builder.Build();

// Add the authentication and authorization middleware to the request pipeline.
app.UseAgents();

// Map the default agent endpoints: GET "/" and the agent message endpoints.
app.MapDefaultAgentEndpoints();

app.Run();
```

`AddAgentAspNetAuthentication` reads the default `TokenValidation` configuration section when it runs inside `AddAgentAuthorization`.

At startup, the extension verifies that the configuration section exists, that at least one audience is present, and that every audience is a GUID. Invalid configuration causes an exception instead of allowing the agent to start without token validation.

For each request, the extension:

1. Selects the Azure Bot Service or Microsoft Entra OpenID metadata endpoint based on the unvalidated token issuer.
2. Validates the token's issuer, audience, lifetime, signature, and signing key issuer.
3. For Microsoft Entra tokens, verifies that the token tenant ID matches its issuer.
4. Applies the `AllowedCallers` check to Microsoft Entra tokens.

Important

The initial issuer read only selects the metadata endpoint. The token is still fully validated against the configured issuers and signing keys before the request is authenticated.

The most important `TokenValidationOptions` settings are:

| Setting | Description |
| --- | --- |
| `Audiences` | **Required.** One or more Client IDs \(GUIDs\) of your Azure Bot registration. |
| `TenantId` | Recommended. Adds tenant-specific issuer URLs to the trusted issuer list. |
| `ValidIssuers` | Optional override of the trusted issuer list. |
| `IsGov` | Selects Azure Government issuer and metadata defaults. |
| `AzureBotServiceOnly` | Accepts only tokens that use the Azure Bot Service Bot Framework issuer when `ValidIssuers` isn't set. |
| `AzureBotServiceOpenIdMetadataUrl` | OpenID metadata URL for tokens issued directly by Azure Bot Service. |
| `OpenIdMetadataUrl` | OpenID metadata URL for Microsoft Entra tokens. |
| `AzureBotServiceTokenHandling` | Enables separate metadata handling for Azure Bot Service tokens. The default is `true`. |
| `OpenIdMetadataRefresh` | How frequently OpenID metadata is refreshed. The default is 12 hours. |
| `AllowedCallers` | Optional caller allow list. |

### Configure cloud-specific validation

For Azure Government, set `IsGov` so the extension selects the government issuer and metadata defaults:

```json
"TokenValidation": {
  "Audiences": [ "{{ClientId}}" ],
  "TenantId": "{{TenantId}}",
  "IsGov": true
}
```

For Azure China or another sovereign cloud, explicitly configure the Azure Bot Service metadata URL, Microsoft Entra metadata URL, and valid issuers for that cloud:

```json
"TokenValidation": {
  "Audiences": [ "{{ClientId}}" ],
  "TenantId": "{{TenantId}}",
  "AzureBotServiceOpenIdMetadataUrl": "{{AzureBotServiceOpenIdMetadataUrl}}",
  "OpenIdMetadataUrl": "{{MicrosoftEntraOpenIdMetadataUrl}}",
  "ValidIssuers": [
    "{{AzureBotServiceIssuer}}",
    "{{MicrosoftEntraIssuer}}"
  ]
}
```

If the agent should accept only legacy Azure Bot Service Bot Framework tokens, set `AzureBotServiceOnly`:

```json
"TokenValidation": {
  "Audiences": [ "{{ClientId}}" ],
  "TenantId": "{{TenantId}}",
  "AzureBotServiceOnly": true
}
```

Keep `AzureBotServiceTokenHandling` set to `true` with this option. As Azure Bot Service channels migrate to Microsoft Entra tokens, use an explicit `ValidIssuers` list if you need to accept those tokens while restricting other callers.

Warning

Only disable authentication for local development against the Agents Playground. A deployed agent must require authentication.

## Restrict which callers can reach your agent

Token validation confirms that a caller is authenticated, but it doesn't confirm that the caller is allowed to call your agent. This restriction matters most for agent-to-agent scenarios, where you want to accept requests only from specific applications.

The Python SDK doesn't currently expose a built-in caller allow list. After JWT validation succeeds, add application authorization that compares the authenticated identity's `azp` \(v2 tokens\) or `appid` \(v1 tokens\) claim with your trusted application IDs. Reject the request before calling the adapter when the caller isn't allowed.

The JavaScript SDK doesn't currently expose a built-in caller allow list. After `authorizeJWT` succeeds, add application authorization that compares `req.user.azp` \(v2 tokens\) or `req.user.appid` \(v1 tokens\) with your trusted application IDs. Reject the request before calling `adapter.process` when the caller isn't allowed.

The following Express middleware uses an exact, case-insensitive application ID allow list:

```typescript
import type { Request, RequestHandler } from 'express'

function requireTrustedCaller (trustedApplicationIds: readonly string[]): RequestHandler {
  const allowed = new Set(trustedApplicationIds.map((id) => id.toLowerCase()))

  return (req, res, next) => {
    const identity = (req as Request & {
      user?: { azp?: unknown, appid?: unknown }
    }).user
    const caller = identity?.azp ?? identity?.appid

    if (typeof caller !== 'string' || !allowed.has(caller.toLowerCase())) {
      res.status(403).json({ error: 'Request could not be processed.' })
      return
    }

    next()
  }
}
```

Record whether caller authorization applies to the selected channel. Don't require an application claim on a channel path that legitimately uses service-level Azure Bot Service tokens. For example, a Web Chat-only endpoint reached through Azure Bot Service can record caller authorization as not applicable. Agent-to-agent and trusted-application endpoints must use an explicit allow list.

Use `AllowedCallers` to restrict access by the calling application's ID. When the list is empty or contains `"*"`, any authenticated caller is accepted. When it contains specific Client IDs, the `azp` \(v2 tokens\) or `appid` \(v1 tokens\) claim must match one of them.

```json
"TokenValidation": {
  "Audiences": [ "{{ClientId}}" ],
  "TenantId": "{{TenantId}}",
  "AllowedCallers": [
    "11111111-1111-1111-1111-111111111111",
    "22222222-2222-2222-2222-222222222222"
  ]
}
```

The `AllowedCallers` check applies only to Microsoft Entra tokens. Tokens issued directly by Azure Bot Service use service-level issuers and are excluded from this check.

## Validate the service URL

Each incoming activity carries a service URL that tells your agent where to send replies. Because this value arrives in the request body, a malicious caller can spoof it to redirect the agent's outbound, token-bearing replies to a host it controls.

Azure Bot Service tokens can include a `serviceurl` claim. When outbound host validation is enabled, the `CloudAdapter` compares the host in the activity's service URL with the host in that claim and rejects the request when they don't match. The static allow list described next also validates service URLs when the token doesn't include the claim.

Note

When outbound host validation is disabled, a `serviceurl` claim mismatch is logged as a warning and the request is processed.

## Restrict outbound hosts

The SDK provides an outbound host validator with a static allow list of hosts that the agent can call. A configured host suffix matches both the exact host and its subdomains. For example, `contoso.com` matches both `contoso.com` and `files.contoso.com`.

Create an `OutboundHostValidator` and pass it to the FastAPI or aiohttp `CloudAdapter`:

```python
from microsoft_agents.hosting.core import OutboundHostValidator
from microsoft_agents.hosting.fastapi import CloudAdapter

outbound_host_validator = OutboundHostValidator(
    enabled=True,
    include_default_microsoft_hosts=True,
    hosts=["contoso.com"],
)

adapter = CloudAdapter(
    connection_manager=connection_manager,
    host_validator=outbound_host_validator,
)
```

The Python validator enforces the allow list for activity service URLs before the agent handles the activity. It also enables `serviceurl` claim comparison.

Configure the validator with environment variables:

```dotenv
OutboundHostValidator__Enabled=true
OutboundHostValidator__IncludeDefaultMicrosoftHosts=true
OutboundHostValidator__Hosts=contoso.com,fabrikam.com
```

Indexed host variables such as `OutboundHostValidator__Hosts__0=contoso.com` are also supported.

For explicit configuration, reuse the same policy in the adapter and attachment downloaders:

```typescript
import {
  AgentApplication,
  AttachmentDownloader,
  CloudAdapter,
  loadAuthConfigFromEnv,
  OutboundHostValidator
} from '@microsoft/agents-hosting'

const authConfig = loadAuthConfigFromEnv()
const outboundHostValidator = new OutboundHostValidator({
  enabled: true,
  includeDefaultMicrosoftHosts: true,
  hosts: ['contoso.com']
})

const adapter = new CloudAdapter(
  authConfig,
  undefined,
  undefined,
  undefined,
  outboundHostValidator
)

const agent = new AgentApplication({
  adapter,
  fileDownloaders: [
    new AttachmentDownloader('inputFiles', outboundHostValidator)
  ]
})
```

The JavaScript validator enforces the allow list for activity service URLs and for attachment URLs when the validator is used by `AttachmentDownloader` or `TeamsAttachmentDownloader`. It also enables `serviceurl` claim comparison.

Keep `includeDefaultMicrosoftHosts` set to `true` for the generic configuration. Set it to `false` only when the deployment has a narrow, tested host set and explicitly lists every required host. A configured host is a suffix rule and also allows its subdomains.

The validator isn't a process-wide firewall. It doesn't automatically protect arbitrary `fetch` calls, model clients, retrieval clients, or tool implementations. Apply a typed destination allow list, URL parsing, redirect controls, timeouts, and network egress controls to those clients.

Enable the validator by using the `OutboundHostValidator` section in *appsettings.json*:

```json
"OutboundHostValidator": {
  "Enabled": true,
  "IncludeDefaultMicrosoftHosts": true,
  "Hosts": [
    "contoso.com"
  ]
}
```

| Setting | Default | Description |
| --- | --- | --- |
| `Enabled` | `false` | Enables service URL claim validation and allow list enforcement. |
| `IncludeDefaultMicrosoftHosts` | `true` | Includes the built-in Microsoft first-party host allow list. |
| `Hosts` | *\(empty\)* | Additional allowed host suffixes. A leading `*.` is accepted and ignored. A full URL or `host:port` value is also accepted; only the host is used. |

The .NET validator enforces the allow list for activity service URLs and for token-bearing downloads made by `AttachmentDownloader` and `M365AttachmentDownloader`. It also enables `serviceurl` claim comparison.

The built-in Microsoft first-party host suffixes are:

- `botframework.com`: Bot connector and channel service URLs
- `smba.trafficmanager.net`, `teams.microsoft.com`, `teams.microsoft.us`: Teams service URLs
- `graph.microsoft.com`: Microsoft Graph
- `sharepoint.com`: SharePoint and OneDrive hosted attachments
- `svc.ms`: Teams attachment CDN
- `blob.core.windows.net`: Azure Blob Storage and the Attachment Management Service

Tip

If your agent only calls Microsoft first-party channels and services, enable the validator with the defaults and an empty custom-host list. Add hosts only for custom channels or self-hosted service URLs.

Note

Local testing tools such as the Agents Playground call back to a `localhost` service without authentication. Leave the validator disabled for local development, or explicitly allow the required local host. Enable the validator in production.

## Putting it together

Apply JWT authorization to the endpoint and inject an enabled validator into the adapter:

```python
outbound_host_validator = OutboundHostValidator(
    enabled=True,
    include_default_microsoft_hosts=True,
)

adapter = CloudAdapter(
    connection_manager=connection_manager,
    host_validator=outbound_host_validator,
)

@app.post("/api/messages")
@jwt_authorization_decorator
async def messages_handler(request: Request):
    return await start_agent_process(request, agent_app, adapter)
```

Keep `ANONYMOUS_ALLOWED` set to `false` and set `VALIDATE_ISSUER` to `true` in the connection configuration.

Enable the outbound policy in the environment:

```dotenv
OutboundHostValidator__Enabled=true
OutboundHostValidator__IncludeDefaultMicrosoftHosts=true
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__VALIDATEISSUER=true
```

Set the connection-map audience to the exact agent Client ID. Then load the authentication configuration and protect the endpoint. The example uses a bounded JSON parser and the configured outbound validator:

```typescript
import express from 'express'
import {
  AgentApplication,
  authorizeJWT,
  CloudAdapter,
  loadAuthConfigFromEnv
} from '@microsoft/agents-hosting'

const authConfig = loadAuthConfigFromEnv()
const adapter = new CloudAdapter(authConfig)
const agent = new AgentApplication({ adapter })
const server = express()

server.use(express.json({ limit: '256kb' }))

server.post(
  '/api/messages',
  authorizeJWT(authConfig),
  async (req, res, next) => {
    try {
      await adapter.process(req, res, (context) => agent.run(context))
    } catch (error) {
      next(error)
    }
  }
)

server.use((error, req, res, next) => {
  if (res.headersSent) {
    next(error)
    return
  }

  res.status(500).json({ error: 'Request could not be processed.' })
})
```

Add `requireTrustedCaller` after `authorizeJWT` only when caller authorization applies. Keep detailed, redacted diagnostics in server telemetry only.

A hardened *appsettings.json* combines inbound validation, caller authorization, service URL validation, and the outbound host allow list:

```json
{
  "TokenValidation": {
    "Audiences": [ "{{ClientId}}" ],
    "TenantId": "{{TenantId}}",
    "AllowedCallers": [ "{{TrustedCallerAppId}}" ]
  },
  "OutboundHostValidator": {
    "Enabled": true,
    "IncludeDefaultMicrosoftHosts": true,
    "Hosts": []
  }
}
```

## Security checklist

- \[ \] Require JWT authentication on messaging endpoints in production.
- \[ \] Protect every non-health endpoint that changes data, sends messages, or calls a downstream API.
- \[ \] Configure an exact audience and reject missing, malformed, expired, wrong-audience, wrong-issuer, and wrong-tenant tokens.
- \[ \] Enable issuer validation and configure the correct tenant and cloud-specific authority or issuers.
- \[ \] Record whether caller authorization applies. Restrict `azp` or `appid` when only specific applications should reach the agent.
- \[ \] Enable outbound host validation and add any custom channel hosts to the allow list.
- \[ \] Share the outbound validator with supported attachment downloaders so token-bearing downloads use the same policy.
- \[ \] Apply separate destination and network egress controls to arbitrary HTTP, model, retrieval, and tool clients.
- \[ \] Run JWT validation before caller authorization and adapter processing.
- \[ \] Fail startup when required production security settings are missing or unsafe.
- \[ \] Test disallowed hosts and service URL claim mismatches with signed tokens in the target environment.

## Next steps

- [Configure authentication in your agent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/configure-authentication-msal)
