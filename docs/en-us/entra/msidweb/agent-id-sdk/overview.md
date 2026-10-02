<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Overview of the Microsoft Entra ID Auth SDK \(sidecar\)

The Microsoft Entra ID Auth SDK \(sidecar\) is a containerized web service that handles token acquisition, validation, and secure downstream API calls. It runs as a companion container alongside your application, allowing you to offload identity logic to a dedicated service. By centralizing identity operations in the Microsoft Entra ID Auth SDK \(sidecar\), you eliminate the need to embed complex token management logic in each service, reducing code duplication and potential security vulnerabilities.

If you're building with Kubernetes, containerized services with Docker, or modern microservices on Azure, the Microsoft Entra ID Auth SDK \(sidecar\) provides a standardized way to handle authentication and authorization in cloud-native applications.

## What is the Microsoft Entra ID Auth SDK \(sidecar\)?

The Microsoft Entra ID Auth SDK \(sidecar\) communicates with your application through a HTTP API for authentication and authorization, providing consistent integration patterns regardless of your technology stack. Instead of embedding identity logic directly in your application code, the Microsoft Entra ID Auth SDK \(sidecar\) handles token management, validation, and API calls through standard HTTP requests.

This approach enables polyglot microservices architectures where different services can be written in Python, Node.js, Go, Java, and others while maintaining consistent authentication patterns.

The typical architecture is as follows:

*Client Application → Your Web API → Microsoft Entra ID Auth SDK \(sidecar\) → Microsoft Entra ID*

For the latest container image and version tags, see the [Container Image](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) to get started.

### Security

Ensure your Microsoft Entra ID Auth SDK \(sidecar\) deployment follows best practices for secure operation. The SDK must run in a containerized environment with restricted network access, to prevent unauthorized access. Exposing the SDK API publicly can lead to security vulnerabilities, such as unauthorized token acquisition.

Consult [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security) to ensure best practices for network, credential, and runtime security recommendations.

Caution

The the SDK API must not be publicly accessible. It should only be reachable by applications within the same trust boundary \(e.g., same pod or virtual network\) to prevent unauthorized token acquisition.

## Quick start

To get started with the Microsoft Entra ID Auth SDK \(sidecar\), the following steps are recommended:

1. **[Choose your deployment](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation)** - Select Kubernetes, Docker, or AKS
2. **[Configure settings](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)** - Set up environment variables
3. **[Pick a scenario](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)** - Follow a guided example
4. **[Deploy to production](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)** - Review security best practices

## Key benefits

The architecture separates identity concerns from business logic, providing the following benefits:

| Benefit | Description |
| --- | --- |
| **Multiple Language Support** | Call via HTTP from Python, Node.js, Go, Java, and others |
| **Centralized Security config** | One place for identity configuration, token management and credential management |
| **Container Native** | Built for Kubernetes, Docker, AKS and other modern deployments |
| **Zero Trust Ready** | Integrates with managed identity and proof-of-possession tokens - keeping sensitive data out of your application code |

## When to use the Microsoft Entra ID Auth SDK \(sidecar\) or Microsoft.Identity.Web

| Scenario | Use Microsoft Entra ID Auth SDK \(sidecar\) | Use Microsoft.Identity.Web |
| --- | --- | --- |
| **Language Support** | Multiple languages \(Python, Node.js, Go, Java, etc.\) | .NET only |
| **Deployment Model** | Containers \(Kubernetes, Docker, AKS\) | Any deployment model |
| **Identity Patterns** | Consistent patterns across all services | Deep .NET framework integration |
| **Agent Identity** | Available in all supported languages | .NET only |
| **Token Validation** | Available in all supported languages | .NET only |
| **Security Model** | Secrets and tokens isolated from application code | Integrated with application |
| **Performance** | Additional network hop required | Direct in-process calls |
| **Framework Integration** | HTTP API integration | Native .NET integration |
| **Containerization** | Designed for containerized environments | Works with or without containers |

See [Comparison with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/comparison) for detailed guidance on choosing between the two approaches.

### Token validation

The Microsoft Entra ID Auth SDK \(sidecar\) validates access and ID tokens issued by Microsoft Entra ID, including app-only access tokens embedded in SHR PoP credentials, by verifying their signatures against Microsoft Entra ID's public keys, checking expiration times, and ensuring the tokens are intended for your application. For SHR PoP credentials, it also validates the SHR signature and always validates the timestamp \(`ts`\). By default, it validates the HTTP method \(`m`\), host or host and port \(`u`\), and path \(`p`\); operators can disable those checks. Query binding \(`q`\) is opt-in, and the URI scheme, headers \(`h`\), and body \(`b`\) aren't validated. Once validated, you can extract claims, roles, and scopes to make informed authorization decisions within your application logic.

### Token acquisition / authorization header creation

- **On-Behalf-Of OAuth 2.0 flow** - Delegate user context to downstream APIs
- **Client Credentials** - Application-to-application authentication
- **Managed Identity** - Native Azure service authentication
- **Agent Identity** - Autonomous or delegated agent patterns

### Downstream API calls

- Acquire and attach tokens automatically
- Optional request overrides \(scopes, method, headers\)
- Signed HTTP Requests \(PoP/SHR\) support

### Scenarios & tutorials

The following guides are comprehensive step-by-step tutorials with practical code examples demonstrating how to integrate the Microsoft Entra ID Auth SDK \(sidecar\) into your applications. Each scenario provides complete request/response examples, code snippets, and implementation patterns tailored for different programming languages and frameworks.

| Scenario | Description |
| --- | --- |
| **[Validate Authorization Header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)** | Extract claims from Bearer tokens or app-only SHR PoP credentials for access control and custom authorization middleware |
| **[Obtain Authorization Header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/obtain-authorization-header)** | Acquire tokens for calling downstream APIs securely |
| **[Call Downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)** | Make HTTP calls to protected APIs with automatic token attachment for multi-language microservices |
| **[Use Managed Identity](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/managed-identity)** | Authenticate as an Azure service for calling Microsoft Graph or other Azure services |
| **[Implement Long-Running OBO Flow](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/long-running-on-behalf)** | Handle user context over extended operations with token refresh and On-Behalf-Of delegation |
| **[Use Signed HTTP Requests](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/signed-http-request)** | Implement proof-of-possession security with PoP tokens |
| **[Agent Autonomous Batch Processing](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/agent-autonomous-batch)** | Process batch jobs with autonomous agent identity |
| **[Integrate from TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript)** | Use the Microsoft Entra ID Auth SDK \(sidecar\) from Node.js/Express/NestJS applications |
| **[Integrate from Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-python)** | Use the Microsoft Entra ID Auth SDK \(sidecar\) from Flask/FastAPI/Django applications |

## Architecture patterns

A typical flow where your client calls a Web API, the API delegates identity operations to the Microsoft Entra ID Auth SDK \(sidecar\) via HTTP endpoints. The SDK validates inbound tokens using the `/Validate` endpoint, acquires tokens using `/AuthorizationHeader` and `/AuthorizationHeaderUnauthenticated`, and can directly invoke downstream APIs using `/DownstreamApi` and `/DownstreamApiUnauthenticated`.

It interacts with Microsoft Entra ID for token issuance and Open ID Connect metadata retrieval, with architecture demonstrated in the following snippet:

```mermaid
%%{init: {
  "theme": "base",
  "themeVariables": {
    "background": "#121212",
    "primaryColor": "#1E1E1E",
    "primaryBorderColor": "#FFFFFF",
    "primaryTextColor": "#FFFFFF",
    "textColor": "#FFFFFF",
    "lineColor": "#FFFFFF",
    "labelBackground": "#000000"
  }
}}%%
flowchart LR
    classDef dnode fill:#1E1E1E,stroke:#FFFFFF,stroke-width:2px,color:#FFFFFF
    linkStyle default stroke:#FFFFFF,stroke-width:2px,color:#FFFFFF

    client[Client Application]:::dnode -->| Bearer or PoP over HTTP | webapi[Web API]:::dnode
    subgraph Pod / Host
        webapi -->|"/Validate<br/>/AuthorizationHeader/{name}<br/>/DownstreamApi/{name}"| sidecar["Microsoft Entra ID Auth SDK (sidecar)"]:::dnode
    end
    sidecar -->|Token validation & acquisition| entra[Microsoft Entra ID]:::dnode
```

## Support and resources

The following resources provide comprehensive guidance and help with troubleshooting issues and answers to common questions.

| Resource | Description |
| --- | --- |
| **[Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities)** | Learn about autonomous and delegated agent patterns for advanced scenarios |
| **[API Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints)** | Complete endpoint documentation with request/response formats, query parameters, and error codes |
| **[Troubleshooting](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting)** | Common issues and step-by-step solutions for deployment and runtime problems |
| **[FAQ](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/faq)** | Frequently asked questions covering configuration, security, and integration topics |

For additional help:

- Report issues on [Microsoft-identity-web repository](https://github.com/AzureAD/microsoft-identity-web/issues)
- Check [Microsoft Entra ID troubleshooting guides](https://learn.microsoft.com/en-us/entra/identity-platform/reference-error-codes)

## Related content

- [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation)
- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Comparison with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/comparison)
- [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
