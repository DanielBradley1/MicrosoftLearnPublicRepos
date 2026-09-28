<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/faq -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Frequently asked questions about the Microsoft Entra ID Auth SDK \(sidecar\)

## General questions

### What is the Microsoft Entra ID Auth SDK \(sidecar\)?

The Microsoft Entra ID Auth SDK \(sidecar\) is a containerized web service that handles token acquisition, validation, and secure downstream API calls. It runs as a companion container alongside your application, allowing you to offload identity logic to a dedicated service. By centralizing identity operations in the SDK, you eliminate the need to embed complex token management logic in each service, reducing code duplication and potential security vulnerabilities.

### Why would I use the Microsoft Entra ID Auth SDK \(sidecar\) instead of Microsoft.Identity.Web?

| Feature | Microsoft.Identity.Web | Microsoft Entra ID Auth SDK \(sidecar\) |
| --- | --- | --- |
| **Language Support** | C# / .NET only | Any language \(HTTP\) |
| **Deployment** | In-process library | Separate container |
| **Token Acquisition** | Direct MSAL.NET | Via HTTP API |
| **Token Caching** | In-memory, distributed | In-memory, distributed |
| **OBO Flow** | Native support | Via HTTP endpoint |
| **Client Credentials** | Native support | Via HTTP endpoint |
| **Managed Identity** | Direct support | Direct support |
| **Agent Identities** | Via extensions | Query parameters |
| **Token Validation** | Middleware | /Validate endpoint |
| **Downstream API** | IDownstreamApi | /DownstreamApi endpoint |
| **Microsoft Graph** | Graph SDK integration | Via DownstreamApi |
| **Performance** | In-process \(fastest\) | HTTP overhead |
| **Configuration** | `appsettings.json` and code | `appsettings.json` and Environment variables |
| **Debugging** | Standard .NET debugging | Container debugging |
| **Hot Reload** | .NET Hot Reload | Container restart |
| **Package Updates** | NuGet packages | Container images |
| **License** | MIT | MIT |

See [Comparison Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/comparison) for detailed guidance.

### Is the Microsoft Entra ID Auth SDK \(sidecar\) production-ready?

Yes, the SDK is production ready. Refer to the [GitHub releases](https://github.com/AzureAD/microsoft-identity-web/releases) for the latest release status and production readiness guidelines.

### Are container images available?

Yes - Refer to the [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation#container-image) for available images and version tags.

### Can I run the SDK outside Kubernetes?

Yes - Refer to the [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation#docker-compose) for instructions on running the SDK in Docker Compose or other container environments \(Docker Compose, Azure Container Instances, AWS ECS/Fargate, Standalone Docker\).

### What network ports does the SDK use?

Default port: `5000` \(configurable\)

The SDK should only be accessible from your application container, never exposed externally.

## Deployment

Learn about deployment options, resource requirements, and integration with container platforms like Docker Compose and Kubernetes.

### What are the resource requirements?

See the [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation#resource-requirements) for detailed resource requirements.

### Can I use the SDK with Docker compose?

Yes - see the [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation#docker-compose) for Docker Compose examples.

### How do I deploy to AKS with Managed Identity?

Yes - follow the [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation#azure-kubernetes-service-aks-with-managed-identity) in the *Azure Kubernetes Service \(AKS\) with Managed Identity* section.

## Configuration

Configure the SDK settings including credentials, downstream APIs, and request overrides to match your deployment requirements.

### Is a configuration reference available?

Yes - see the [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration#required-configuration) for detailed configuration options.

### Should I use client secrets or certificates?

**Prefer certificates** over client secrets:

- More secure
- Easier to rotate
- Recommended by Microsoft

**Best**: Use Managed Identity in Azure \(no credentials needed\)

See [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security) for guidance.

### Can I configure multiple downstream APIs?

Yes. Configure each with its own section:

```yaml
DownstreamApis__Graph__BaseUrl: "https://graph.microsoft.com/v1.0"
DownstreamApis__Graph__Scopes: "User.Read"

DownstreamApis__MyApi__BaseUrl: "https://api.contoso.com"
DownstreamApis__MyApi__Scopes: "api://myapi/.default"
```

### How do I override configuration per request?

Use query parameters on endpoints:

```bash
# Override scopes
GET /AuthorizationHeader/Graph?optionsOverride.Scopes=User.Read

# Request app token instead of OBO
GET /AuthorizationHeader/Graph?optionsOverride.RequestAppToken=true

# Override relative path
GET /DownstreamApi/Graph?optionsOverride.RelativePath=me/messages
```

See [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration) for all options.

## Agent identities

Agent identities enable scenarios where an agent application can operate autonomously or on behalf of a user, with proper context isolation and scoping.

### What are agent identities?

Agent identities enable scenarios where an agent application acts either:

- **Autonomously** - in its own application context
- **Interactive** - on behalf of the user that called it

See [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities) for comprehensive documentation.

### When should I use autonomous agent mode?

Use autonomous agent mode for:

- Batch processing without user context
- Background tasks
- System-to-system operations
- Scheduled jobs

Example:

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=<agent-client-id>
```

### When should I use interactive agent mode?

Use delegated agent mode for:

- Interactive agent applications
- AI assistants acting on behalf of users
- User-scoped automation
- Personalized workflows

Example:

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=<agent-client-id>&AgentUsername=user@contoso.com
```

### Why can't I use AgentUsername without AgentIdentity?

`AgentUsername` is a modifier that specifies which user the agent operates on behalf of. It requires `AgentIdentity` to specify which agent context to use. Without `AgentIdentity`, the parameter has no meaning.

### Why are AgentUsername and AgentUserId mutually exclusive?

They're two ways to identify the same user:

- `AgentUsername` - User Principal Name \(UPN\)
- `AgentUserId` - Object ID \(OID\)

Allowing both creates ambiguity. Choose the one that fits your scenario:

- Use `AgentUsername` when you have the user's UPN
- Use `AgentUserId` when you have the user's object ID

## API usage

The SDK exposes several HTTP endpoints for token acquisition, validation, and downstream API calls with support for both authenticated and unauthenticated flows.

### What endpoints does the SDK expose?

- `/Validate` - Validate token and return claims
- `/AuthorizationHeader/{serviceName}` - Get authorization header with token
- `/AuthorizationHeaderUnauthenticated/{serviceName}` - Get token without inbound user token
- `/DownstreamApi/{serviceName}` - Call downstream API directly
- `/DownstreamApiUnauthenticated/{serviceName}` - Call downstream API without inbound user token
- `/healthz` - Health probe

See [Endpoints Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints) for details.

### What's the difference between authenticated and unauthenticated endpoints?

**Authenticated**: Require bearer token in `Authorization` header \(for OBO flows\) **Unauthenticated**: Don't validate inbound token \(for app-only or agent scenarios\)

### How do I validate a user token?

```bash
GET /Validate
Authorization: Bearer <user-token>
```

Response includes all claims from the token.

### How do I get an access token for a downstream API?

```bash
GET /AuthorizationHeader/Graph
Authorization: Bearer <user-token>
```

Response includes authorization header ready to use with downstream API.

### Can I override HTTP method or path per request?

Yes, using query parameters:

```bash
# Override method
GET /DownstreamApi/Graph?optionsOverride.HttpMethod=POST

# Override path
GET /DownstreamApi/Graph?optionsOverride.RelativePath=me/messages
```

## Token caching

The SDK automatically caches tokens in memory to optimize performance and reduce redundant token acquisition requests.

### Does the SDK cache tokens?

Yes - the SDK caches tokens in memory by default.

### How long are tokens cached?

Tokens are cached until near expiration, then automatically refreshed. Exact duration depends on token lifetime \(typically 1 hour for Entra ID tokens\).

### Can I disable caching?

Token caching is automatic and optimized. There's currently no option to disable it.

### Is token cache shared across SDK instances?

No - each SDK instance maintains its own in-memory cache. In high-availability deployments, each pod has independent caching.

## Security

Secure SDK deployments follow Microsoft Entra identity and data protection best practices, including managed identity usage, network isolation, and proper credential handling.

### Is it safe to run the SDK?

Yes - see the [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security#is-it-safe-to-run-the-sdk) for security best practices.

### Should I expose the SDK externally?

**Never** - The SDK should only be accessible from your application container. For detailed security best practices, see [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security).

### How should I secure the SDK?

See [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security#best-practices-checklist) for comprehensive guidance.

### What credentials should I use?

Preference order:

1. **Managed Identity** \(Azure\) - Most secure, no credentials
2. **Certificates** - Secure, can be rotated
3. **Client Secrets** - Less preferred, keep in secure vault

### Is the SDK compliance-certified?

Check the [GitHub repository](https://github.com/AzureAD/microsoft-identity-web) for current compliance information.

## Performance

SDK performance depends on token caching effectiveness and network round-trip latency, with typical response times between 10-50ms for cached tokens.

### What's the performance impact of using the SDK?

Typical HTTP round-trip: 10-50ms

Token caching minimizes repeated acquisitions. The first request is slower \(token acquisition\), subsequent requests use cached tokens.

### How does SDK performance compare to in-process libraries?

In-process libraries are faster \(no network round-trip\) but the SDK provides:

- Language agnostic access
- Centralized configuration
- Shared token cache across services
- Simplified scaling

See [Comparison Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/comparison) for details.

### Can I scale the SDK horizontally?

Yes. Deploy multiple SDK replicas using Kubernetes Deployment. Each pod maintains independent token caching.

## Migration

Moving from Microsoft.Identity.Web to the SDK offers advantages in multi-language support, centralized configuration, and simplified scaling across services.

### Can I migrate from Microsoft.Identity.Web to the Microsoft Entra ID Auth SDK \(sidecar\)?

Yes - see the [Comparison Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/comparison#migration-guidance) for detailed migration steps

## Support

Get help with issues, find additional documentation, and access community resources through official channels.

### Where do I report bugs?

Report issues on the [GitHub repository](https://github.com/AzureAD/microsoft-identity-web/issues), using the Entra ID template.

## Troubleshooting

When you encounter issues with the SDK, refer to the comprehensive troubleshooting guide for diagnostic steps, common problems, and solutions in [Troubleshooting Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting).

## Related content

- [Microsoft Learn Documentation](https://learn.microsoft.com/en-us/entra)
- [Identity Platform Docs](https://learn.microsoft.com/en-us/entra/identity-platform)
- [Agent Identity Platform](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform)
