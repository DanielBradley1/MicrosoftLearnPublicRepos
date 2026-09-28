<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/getting-started/packages -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Microsoft.Identity.Web NuGet packages

Microsoft.Identity.Web is a set of NuGet packages that simplify adding authentication and authorization to applications that integrate with the Microsoft identity platform. Each package targets a specific scenario, so you install only what your application needs. This article describes the available packages and helps you choose the right one.

## Core packages

These packages provide the fundamental functionality for authentication and token management.

| Package | Description |
| --- | --- |
| **Microsoft.Identity.Web** | The main package for ASP.NET Core web apps and web APIs. Enables sign-in, token validation, and calling downstream APIs. |
| **Microsoft.Identity.Web.UI** | Provides UI components for ASP.NET Core web apps, including sign-in and sign-out controllers and views. |
| **Microsoft.Identity.Web.TokenAcquisition** | Higher-level API for token acquisition in confidential client applications \(ASP.NET Core and .NET SDK\). Handles token management automatically. |
| **Microsoft.Identity.Web.TokenCache** | Token cache serializers for MSAL.NET confidential client applications. Supports in-memory, distributed, and session-based caching. |

## Credential management packages

These packages handle different authentication credential types.

| Package | Description |
| --- | --- |
| **Microsoft.Identity.Web.Certificate** | Certificate management capabilities for MSAL.NET, including loading certificates from Azure Key Vault and local stores. |
| **Microsoft.Identity.Web.Certificateless** | Certificateless authentication scenarios such as managed identities and workload identity federation. |

## Downstream API and integration packages

These packages help you call protected APIs and integrate with Azure services.

| Package | Description |
| --- | --- |
| **Microsoft.Identity.Web.DownstreamApi** | Higher-level interface for calling downstream protected APIs from confidential client applications with automatic token management. |
| **Microsoft.Identity.Web.Azure** | Enables ASP.NET Core web apps and web APIs to use Azure SDKs with the Microsoft identity platform by providing `TokenCredential` implementations. |
| **Microsoft.Identity.Web.OWIN** | Enables ASP.NET web apps \(OWIN/Katana\) and web APIs on .NET Framework to use the Microsoft identity platform. |

## Microsoft Graph packages

These packages provide integration with Microsoft Graph for calling Microsoft 365 services.

| Package | Description |
| --- | --- |
| **Microsoft.Identity.Web.GraphServiceClient** | Microsoft Graph integration using the Graph SDK v5 and later. Recommended for new projects. |
| **Microsoft.Identity.Web.GraphServiceClientBeta** | Microsoft Graph Beta integration using the Graph SDK v5 and later. Use this package to access preview features. |
| **Microsoft.Identity.Web.MicrosoftGraph** | Microsoft Graph integration using the Graph SDK v4. Use `GraphServiceClient` packages for new projects. |
| **Microsoft.Identity.Web.MicrosoftGraphBeta** | Microsoft Graph Beta integration using the Graph SDK v4. |

## Advanced scenario packages

These packages support specialized authentication scenarios.

| Package | Description |
| --- | --- |
| **Microsoft.Identity.Web.Diagnostics** | Diagnostic and logging support for troubleshooting authentication issues. |
| **Microsoft.Identity.Web.OidcFIC** | Cloud Federation Identity Credential \(FIC\) provider implementation. Enables cross-cloud authentication scenarios. |
| **Microsoft.Identity.Web.AgentIdentities** | Helper methods for agent identity scenarios, including building autonomous agents and copilot integrations. |

## Choose the right package

Use the following examples to install the packages that match your application scenario.

### Web applications that sign in users

For ASP.NET Core web apps that sign in users with Microsoft Entra ID, install the core package and the UI package:

```bash
dotnet add package Microsoft.Identity.Web
dotnet add package Microsoft.Identity.Web.UI
```

### Protected web APIs

For ASP.NET Core web APIs that validate tokens from authenticated callers, install the core package:

```bash
dotnet add package Microsoft.Identity.Web
```

### Daemon applications and background services

For daemon apps or background services that acquire tokens without user interaction, install the token acquisition package:

```bash
dotnet add package Microsoft.Identity.Web.TokenAcquisition
```

### Calling Microsoft Graph

For new projects, use the Graph SDK v5 package:

```bash
dotnet add package Microsoft.Identity.Web.GraphServiceClient
```

If your project uses Graph SDK v4, install the earlier integration package instead:

```bash
dotnet add package Microsoft.Identity.Web.MicrosoftGraph
```

### Using Azure SDKs

To authenticate Azure SDK clients with the Microsoft identity platform, install the Azure integration package:

```bash
dotnet add package Microsoft.Identity.Web.Azure
```

### Calling custom downstream APIs

To call your own protected APIs with automatic token management, install the downstream API package:

```bash
dotnet add package Microsoft.Identity.Web.DownstreamApi
```

### Agent and copilot scenarios

For building autonomous agents or copilot integrations, install the agent identities package:

```bash
dotnet add package Microsoft.Identity.Web.AgentIdentities
```

### OWIN applications \(.NET Framework\)

For ASP.NET web apps and web APIs on .NET Framework \(OWIN/Katana\), install the OWIN package:

```bash
dotnet add package Microsoft.Identity.Web.OWIN
```

## Related content

- [Quickstart: Sign in users in a web app](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp)
- [Quickstart: Protect a web API](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi)
- [Daemon applications](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app)
- [Calling downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)
- [Agent identities](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities)
- [All Microsoft.Identity.Web packages on NuGet.org](https://www.nuget.org/packages?q=Microsoft.Identity.Web)
