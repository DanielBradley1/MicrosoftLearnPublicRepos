<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/overview -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Overview of Microsoft Identity Web

Microsoft.Identity.Web is a set of libraries that simplifies adding authentication and authorization to applications that integrate with the Microsoft identity platform, including Microsoft Entra ID. It supports:

- **[.NET Aspire](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/aspire)** distributed applications
- **ASP.NET Core** web applications and web APIs
- **OWIN** applications on .NET Framework
- **.NET** daemon applications and background services

Whether you build web apps that sign in users, web APIs that validate tokens, or background services that call protected APIs, Microsoft.Identity.Web handles the authentication complexity for you.

## Why use Microsoft Identity Web?

Microsoft.Identity.Web reduces boilerplate code and provides built-in best practices for common identity scenarios. Key capabilities include:

- **Simplified authentication** - Minimal configuration for signing in users and validating tokens
- **Downstream API calls** - Call Microsoft Graph, Azure SDKs, or your own protected APIs with automatic token management

  - **Token acquisition** - Acquire tokens on behalf of users or your application
  - **Token cache management** - Distributed cache support with Redis, SQL Server, Cosmos DB, and PostgreSQL

- **Multiple credential types** - Support for certificates, managed identities, and certificateless authentication
- **Automatic authorization headers** - Authentication is handled transparently when calling APIs

See [NuGet packages](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/packages) for an overview of all available packages and when to use them.

### Call APIs with automatic authentication

You can call protected APIs without manually managing tokens. Microsoft.Identity.Web supports the following integration patterns:

- **Microsoft Graph** - Use `GraphServiceClient` with automatic token acquisition
- **Azure SDKs** - Use `TokenCredential` implementations that integrate with Microsoft.Identity.Web
- **Your own APIs** - Use `IDownstreamApi` or `IAuthorizationHeaderProvider` for seamless API calls
- **Agent identities** - Call APIs on behalf of managed identities or service principals with automatic credential handling

Authentication headers are added to your requests automatically, and tokens are acquired and cached transparently. For details, see [Calling downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview), [Daemon applications](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app), and the [Agent identities guide](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities).

## Configuration approaches

You can configure Microsoft.Identity.Web through settings files or programmatically. Both approaches support all authentication scenarios.

### Configuration by file \(recommended\)

Configure authentication in `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id"
  }
}
```

Important

For daemon apps and console applications, ensure your `appsettings.json` file is copied to the output directory. In Visual Studio, set the **Copy to Output Directory** property to **Copy if newer** or **Copy always**, or add the following to your `.csproj`:

```xml
<ItemGroup>
  <None Update="appsettings.json">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
</ItemGroup>
```

### Configuration by code

Alternatively, configure authentication directly in your application startup code:

```csharp
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(options =>
    {
        options.Instance = "https://login.microsoftonline.com/";
        options.TenantId = "your-tenant-id";
        options.ClientId = "your-client-id";
    });
```

## Next steps

Choose the scenario that matches your application:

- **[Web app - Sign in users](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp)** - Add authentication to your ASP.NET Core web application
- **[Web API - Protect your API](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi)** - Secure your ASP.NET Core web API with bearer tokens
- **[Daemon app - Call APIs](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app)** - Build background services that call protected APIs
