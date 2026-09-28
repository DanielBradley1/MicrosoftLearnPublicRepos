<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Build daemon applications and agent identities with Microsoft.Identity.Web

In this article, you build daemon applications, background services, and autonomous agents using Microsoft.Identity.Web. These applications run without user interaction and authenticate using **application identity** \(client credentials\) or **agent identities**.

## Understand supported scenarios

Microsoft.Identity.Web supports three types of non-interactive applications:

| **Scenario** | **Authentication Type** | **Token Type** | **Use Case** |
| --- | --- | --- | --- |
| **Standard Daemon** | Client credentials \(secret/certificate\) | App-only access token | Background services, scheduled jobs, data processing |
| **Autonomous Agent** | Agent identity with client credentials | App-only access token for agent | Copilot agents, autonomous services acting on behalf of an Agent identity. \(Usually in a protected Web API\) |
| **Agent User Identity** | Agent user identity | Agent user identity with client credentials | Autonomous services acting on behalf of an Agent user identity. \(Usually in a protected Web API\) |

## Get started

### Prerequisites

Before you begin, make sure you have:

- .NET 8.0 or later
- Microsoft Entra app registration with **client credentials** \(client secret or certificate\)
- For agent scenarios: Agent identities configured in your Microsoft Entra tenant

### Install packages

Add the required NuGet packages to your project:

```bash
dotnet add package Microsoft.Identity.Web
dotnet add package Microsoft.Extensions.Hosting
```

### Choose a configuration approach

Microsoft.Identity.Web provides two ways to configure daemon applications:

#### Option 1: TokenAcquirerFactory \(recommended for simple scenarios\)

**Best for:** Quick prototypes, console apps, testing, and simple daemon services.

The following code creates a `TokenAcquirerFactory`, configures downstream APIs and Microsoft Graph, and calls the Graph API:

```csharp
using Microsoft.Identity.Abstractions;
using Microsoft.Identity.Web;

// Get the token acquirer factory instance
var tokenAcquirerFactory = TokenAcquirerFactory.GetDefaultInstance();

// Configure downstream API and Microsoft Graph (optional)
tokenAcquirerFactory.Services.AddDownstreamApis(
    tokenAcquirerFactory.Configuration.GetSection("DownstreamApis"))
    .AddMicrosoftGraph();

var serviceProvider = tokenAcquirerFactory.Build();

// Call Microsoft Graph
var graphClient = serviceProvider.GetRequiredService<GraphServiceClient>();
var users = await graphClient.Users.GetAsync();
```

**Advantages:**

- Minimal boilerplate code
- Automatically loads `appsettings.json`
- Perfect for simple scenarios
- One-line initialization

**Disadvantages:**

- Not suitable for tests running in parallel \(singleton\)

#### Option 2: Full ServiceCollection \(recommended for production\)

**Best for:** Production applications, complex scenarios, dependency injection, testability.

The following code uses the .NET Generic Host to configure authentication, token acquisition, caching, and a background service:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Identity.Web;

var host = Host.CreateDefaultBuilder(args)
    .ConfigureServices((context, services) =>
    {
        // Configure authentication
        services.Configure<MicrosoftIdentityApplicationOptions>(
            context.Configuration.GetSection("AzureAd"));

        // Add token acquisition (true = singleton lifetime)
        services.AddTokenAcquisition(true);

        // Add token cache (in-memory for development)
        services.AddInMemoryTokenCaches();

        // Add HTTP client for API calls
        services.AddHttpClient();

        // Add Microsoft Graph (optional)
        services.AddMicrosoftGraph();

        // Add your background service
        services.AddHostedService<DaemonWorker>();
    })
    .Build();

await host.RunAsync();
```

**Advantages:**

- Full control over configuration providers
- Better testability with constructor injection
- Integrates with ASP.NET Core hosting model
- Supports complex scenarios \(multiple auth schemes\)
- Production-ready architecture
- Supports parallel test execution \(isolated service provider per test\)

Note

The parameter `true` in `AddTokenAcquisition(true)` means the service is registered as a **singleton** \(single instance for the app lifetime\). Use `false` for scoped lifetime in web applications.

> **Recommendation:** Start with `TokenAcquirerFactory` for prototypes and single-threaded tests. Migrate to the full `ServiceCollection` pattern when building production applications or running parallel tests.

---

## Configure standard daemon applications

Standard daemon applications authenticate using **client credentials** \(client secret or certificate\) and obtain **app-only access tokens** to call APIs.

### Configure authentication settings

Add the following configuration to your **appsettings.json** file. You can use either a client secret or a certificate \(recommended for production\):

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientSecret": "your-client-secret",

    "ClientCredentials": [
      // Option 1: Client Secret
      {
        "SourceType": "ClientSecret",
        "ClientSecret": "your-client-secret",
      },
      // Option 2: Certificate (recommended for production)
      {
        "SourceType": "StoreWithDistinguishedName",
        "CertificateStorePath": "CurrentUser/My",
        "CertificateDistinguishedName": "CN=DaemonAppCert"
      }
      // More options: https://aka.ms/ms-id-web/client-credentials
    ]
  }
}
```

**Important:** Set your `appsettings.json` to copy to the output directory. Add the following to your `.csproj` file:

```xml
<ItemGroup>
  <None Update="appsettings.json">
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
  </None>
</ItemGroup>
```

ASP.NET Core applications copy this file automatically, but daemon apps \(and OWIN apps\) don't.

### Set up service configuration

The following **Program.cs** code registers Microsoft Identity options, token acquisition, caching, and a hosted background service:

```csharp
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Identity.Web;

var host = Host.CreateDefaultBuilder(args)
    .ConfigureServices((context, services) =>
    {
        IConfiguration configuration = context.Configuration;

        // Configure Microsoft Identity options
        services.Configure<MicrosoftIdentityApplicationOptions>(
            configuration.GetSection("AzureAd"));

        // Add token acquisition (true = singleton)
        services.AddTokenAcquisition(true);

        // Add token cache
        services.AddInMemoryTokenCaches(); // For development
        // services.AddDistributedTokenCaches(); // For production

        // Add HTTP client
        services.AddHttpClient();

        // Add Microsoft Graph SDK (optional)
        services.AddMicrosoftGraph();

        // Add your background service
        services.AddHostedService<DaemonWorker>();
    })
    .Build();

await host.RunAsync();
```

### Call Microsoft Graph

The following **DaemonWorker.cs** class uses the Graph SDK to list users on a recurring schedule:

```csharp
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;
using Microsoft.Graph;
using Microsoft.Identity.Abstractions;

public class DaemonWorker : BackgroundService
{
    private readonly GraphServiceClient _graphClient;
    private readonly ILogger<DaemonWorker> _logger;

    public DaemonWorker(
        GraphServiceClient graphClient,
        ILogger<DaemonWorker> logger)
    {
        _graphClient = graphClient;
        _logger = logger;
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            try
            {
                // Call Microsoft Graph with app-only permissions
                var users = await _graphClient.Users
                    .GetAsync(cancellationToken: stoppingToken);

                _logger.LogInformation($"Found {users?.Value?.Count} users");
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error calling Microsoft Graph");
            }

            await Task.Delay(TimeSpan.FromMinutes(5), stoppingToken);
        }
    }
}
```

### Use IAuthorizationHeaderProvider

For more control over HTTP calls, use `IAuthorizationHeaderProvider` to create authorization headers manually:

```csharp
using Microsoft.Identity.Abstractions;

public class DaemonService
{
    private readonly IAuthorizationHeaderProvider _authProvider;
    private readonly HttpClient _httpClient;

    public DaemonService(
        IAuthorizationHeaderProvider authProvider,
        IHttpClientFactory httpClientFactory)
    {
        _authProvider = authProvider;
        _httpClient = httpClientFactory.CreateClient();
    }

    public async Task<string> CallApiAsync()
    {
        // Get authorization header for app-only access
        string authHeader = await _authProvider
            .CreateAuthorizationHeaderForAppAsync(
                scopes: "https://graph.microsoft.com/.default");

        // Add to HTTP request
        _httpClient.DefaultRequestHeaders.Clear();
        _httpClient.DefaultRequestHeaders.Add("Authorization", authHeader);

        var response = await _httpClient.GetStringAsync(
            "https://graph.microsoft.com/v1.0/users");

        return response;
    }
}
```

See also [Calling downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview) to learn about all the ways Microsoft Identity Web proposes to call downstream APIs.

---

## Configure autonomous agents \(agent identity\)

Autonomous agents use **agent identities** to obtain app-only tokens. This pattern is useful for Copilot scenarios and autonomous services.

Note

Microsoft recommends that agents calling downstream APIs do so from within protected web APIs, even when the agents acquire an app token.

### Configure agent services

The following code sets up authentication, token acquisition, and agent identity support using in-memory configuration:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Configuration;
using Microsoft.Identity.Web;

var services = new ServiceCollection();

// Configuration
var configuration = new ConfigurationBuilder()
    .AddInMemoryCollection(new Dictionary<string, string?>
    {
        ["AzureAd:Instance"] = "https://login.microsoftonline.com/",
        ["AzureAd:TenantId"] = "your-tenant-id",
        ["AzureAd:ClientId"] = "your-agent-app-client-id",
        ["AzureAd:ClientCredentials:0:SourceType"] = "StoreWithDistinguishedName",
        ["AzureAd:ClientCredentials:0:CertificateStorePath"] = "CurrentUser/My",
        ["AzureAd:ClientCredentials:0:CertificateDistinguishedName"] = "CN=YourCert"
    })
    .Build();

services.AddSingleton<IConfiguration>(configuration);

// Configure Microsoft Identity
services.Configure<MicrosoftIdentityApplicationOptions>(
    configuration.GetSection("AzureAd"));

services.AddTokenAcquisition(true);
services.AddInMemoryTokenCaches();
services.AddHttpClient();
services.AddMicrosoftGraph();

// Add agent identities support
services.AddAgentIdentities();

var serviceProvider = services.BuildServiceProvider();
```

### Acquire tokens with agent identity

After configuring agent services, acquire tokens using either `IAuthorizationHeaderProvider` or the Microsoft Graph SDK:

```csharp
using Microsoft.Identity.Abstractions;
using Microsoft.Graph;

// Your agent identity GUID
string agentIdentityId = "d84da24a-2ea2-42b8-b5ab-8637ec208024";

// Option 1: Using IAuthorizationHeaderProvider
IAuthorizationHeaderProvider authProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

var options = new AuthorizationHeaderProviderOptions()
    .WithAgentIdentity(agentIdentityId);

string authHeader = await authProvider.CreateAuthorizationHeaderForAppAsync(
    scopes: "https://graph.microsoft.com/.default",
    options);

// Option 2: Using Microsoft Graph SDK
GraphServiceClient graphClient =
    serviceProvider.GetRequiredService<GraphServiceClient>();

var applications = await graphClient.Applications.GetAsync(request =>
{
    request.Options.WithAuthenticationOptions(authOptions =>
    {
        authOptions.WithAgentIdentity(agentIdentityId);
    });
});
```

### Review a complete autonomous agent example

The following class wraps agent identity token acquisition and Graph API calls into a reusable service:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Configuration;
using Microsoft.Graph;
using Microsoft.Identity.Abstractions;
using Microsoft.Identity.Web;

public class AutonomousAgentService
{
    private readonly GraphServiceClient _graphClient;
    private readonly IAuthorizationHeaderProvider _authProvider;
    private readonly string _agentIdentityId;

    public AutonomousAgentService(
        string agentIdentityId,
        IServiceProvider serviceProvider)
    {
        _agentIdentityId = agentIdentityId;
        _graphClient = serviceProvider.GetRequiredService<GraphServiceClient>();
        _authProvider = serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();
    }

    public async Task<string> GetAuthorizationHeaderAsync()
    {
        var options = new AuthorizationHeaderProviderOptions()
            .WithAgentIdentity(_agentIdentityId);

        return await _authProvider.CreateAuthorizationHeaderForAppAsync(
            "https://graph.microsoft.com/.default",
            options);
    }

    public async Task<IEnumerable<Application>> ListApplicationsAsync()
    {
        var apps = await _graphClient.Applications.GetAsync(request =>
        {
            request.Options.WithAuthenticationOptions(options =>
            {
                options.WithAgentIdentity(_agentIdentityId);
            });
        });

        return apps?.Value ?? Enumerable.Empty<Application>();
    }
}
```

---

## Configure agent user identity

Agent user identity allows agents to act **on behalf of an agent user** with delegated permissions. Use this pattern for agents that need their own mailbox or other user-scoped resources.

### Prerequisites

To use agent user identity, you need:

- Agent blueprint registered in Microsoft Entra ID
- Agent identity created and linked to the agent application
- Agent user identity associated with the agent identity

### Configure agent user services

The following code configures agent application identity with a certificate credential and registers the required services:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Identity.Web;
using System.Security.Cryptography.X509Certificates;

var services = new ServiceCollection();

// Configure agent application
services.Configure<MicrosoftIdentityApplicationOptions>(options =>
{
    options.Instance = "https://login.microsoftonline.com/";
    options.TenantId = "your-tenant-id";
    options.ClientId = "your-agent-app-client-id";

    // Use certificate for agent authentication
    options.ClientCredentials = new[]
    {
        CertificateDescription.FromStoreWithDistinguishedName(
            "CN=YourCertificate",
            StoreLocation.CurrentUser,
            StoreName.My)
    };
});

// Add services (true = singleton)
services.AddSingleton<IConfiguration>(new ConfigurationBuilder().Build());
services.AddTokenAcquisition(true);
services.AddInMemoryTokenCaches();
services.AddHttpClient();
services.AddMicrosoftGraph();
services.AddAgentIdentities();

var serviceProvider = services.BuildServiceProvider();
```

### Acquire user tokens with agent identity

You can identify the target user by UPN or object ID.

#### By username \(UPN\)

```csharp
using Microsoft.Identity.Abstractions;
using Microsoft.Graph;

string agentIdentityId = "your-agent-identity-id";
string userUpn = "user@yourtenant.onmicrosoft.com";

// Get authorization header
IAuthorizationHeaderProvider authProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

var options = new AuthorizationHeaderProviderOptions()
    .WithAgentUserIdentity(
        agentApplicationId: agentIdentityId,
        username: userUpn);

string authHeader = await authProvider.CreateAuthorizationHeaderForUserAsync(
    scopes: new[] { "https://graph.microsoft.com/.default" },
    options);

// Or use Microsoft Graph SDK
GraphServiceClient graphClient =
    serviceProvider.GetRequiredService<GraphServiceClient>();

var me = await graphClient.Me.GetAsync(request =>
{
    request.Options.WithAuthenticationOptions(options =>
        options.WithAgentUserIdentity(agentIdentityId, userUpn));
});
```

#### By user Object ID

```csharp
string agentIdentityId = "your-agent-identity-id";
Guid userObjectId = Guid.Parse("user-object-id");

var options = new AuthorizationHeaderProviderOptions()
    .WithAgentUserIdentity(
        agentApplicationId: agentIdentityId,
        userId: userObjectId);

string authHeader = await authProvider.CreateAuthorizationHeaderForUserAsync(
    scopes: new[] { "https://graph.microsoft.com/.default" },
    options);

// With Graph SDK
var me = await graphClient.Me.GetAsync(request =>
{
    request.Options.WithAuthenticationOptions(options =>
        options.WithAgentUserIdentity(agentIdentityId, userObjectId));
});
```

### Cache tokens with ClaimsPrincipal

For better performance, cache user tokens by passing a `ClaimsPrincipal` instance. The first call populates the principal with `uid` and `utid` claims; subsequent calls reuse the cached token:

```csharp
using System.Security.Claims;
using Microsoft.Identity.Abstractions;

// First call - creates cache entry
ClaimsPrincipal userPrincipal = new ClaimsPrincipal();

string authHeader = await authProvider.CreateAuthorizationHeaderForUserAsync(
    scopes: new[] { "https://graph.microsoft.com/.default" },
    options,
    userPrincipal);

// ClaimsPrincipal now has uid and utid claims for caching
bool hasUserId = userPrincipal.HasClaim(c => c.Type == "uid");
bool hasTenantId = userPrincipal.HasClaim(c => c.Type == "utid");

// Subsequent calls - uses cache
authHeader = await authProvider.CreateAuthorizationHeaderForUserAsync(
    scopes: new[] { "https://graph.microsoft.com/.default" },
    options,
    userPrincipal); // Reuse the same principal
```

### Override the tenant

For multi-tenant scenarios, you can override the tenant at runtime. This is useful when the app is configured with `"common"` but needs to target a specific tenant:

```csharp
var options = new AuthorizationHeaderProviderOptions()
    .WithAgentUserIdentity(agentIdentityId, userUpn);

// Override tenant (useful when app is configured with "common")
options.AcquireTokenOptions.Tenant = "specific-tenant-id";

string authHeader = await authProvider.CreateAuthorizationHeaderForUserAsync(
    scopes: new[] { "https://graph.microsoft.com/.default" },
    options);

// With Graph SDK
var me = await graphClient.Me.GetAsync(request =>
{
    request.Options.WithAuthenticationOptions(options =>
    {
        options.WithAgentUserIdentity(agentIdentityId, userUpn);
        options.AcquireTokenOptions.Tenant = "specific-tenant-id";
    });
});
```

### Review a complete agent user identity example

The following class provides methods to get user profiles and authorization headers using agent user identity:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Graph;
using Microsoft.Identity.Abstractions;
using System.Security.Claims;

public class AgentUserService
{
    private readonly IAuthorizationHeaderProvider _authProvider;
    private readonly GraphServiceClient _graphClient;
    private readonly string _agentIdentityId;

    public AgentUserService(
        string agentIdentityId,
        IServiceProvider serviceProvider)
    {
        _agentIdentityId = agentIdentityId;
        _authProvider = serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();
        _graphClient = serviceProvider.GetRequiredService<GraphServiceClient>();
    }

    public async Task<User> GetUserProfileAsync(string userUpn)
    {
        var me = await _graphClient.Me.GetAsync(request =>
        {
            request.Options.WithAuthenticationOptions(options =>
                options.WithAgentUserIdentity(_agentIdentityId, userUpn));
        });

        return me!;
    }

    public async Task<User> GetUserProfileByIdAsync(Guid userObjectId)
    {
        var me = await _graphClient.Me.GetAsync(request =>
        {
            request.Options.WithAuthenticationOptions(options =>
                options.WithAgentUserIdentity(_agentIdentityId, userObjectId));
        });

        return me!;
    }

    public async Task<string> GetAuthHeaderForUserAsync(
        string userUpn,
        ClaimsPrincipal? cachedPrincipal = null)
    {
        var options = new AuthorizationHeaderProviderOptions()
            .WithAgentUserIdentity(_agentIdentityId, userUpn);

        return await _authProvider.CreateAuthorizationHeaderForUserAsync(
            scopes: new[] { "https://graph.microsoft.com/.default" },
            options,
            cachedPrincipal ?? new ClaimsPrincipal());
    }
}
```

---

## Create reusable service configuration

### Define an extension method

Create a reusable extension method to encapsulate agent identity configuration across your application:

```csharp
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.TokenCacheProviders.InMemory;

public static class ServiceCollectionExtensions
{
    public static IServiceProvider ConfigureServicesForAgentIdentities(
        this IServiceCollection services,
        IConfiguration configuration)
    {
        // Add configuration
        services.AddSingleton(configuration);

        // Configure Microsoft Identity options
        services.Configure<MicrosoftIdentityApplicationOptions>(
            configuration.GetSection("AzureAd"));

        services.AddTokenAcquisition(true);

        // Add token caching
        services.AddInMemoryTokenCaches();

        // Add HTTP client
        services.AddHttpClient();

        // Add Microsoft Graph (optional)
        services.AddMicrosoftGraph();

        // Add agent identities support
        services.AddAgentIdentities();

        return services.BuildServiceProvider();
    }
}
```

### Use the extension method

Call the extension method to configure services in a single line:

```csharp
var services = new ServiceCollection();
var configuration = new ConfigurationBuilder()
    .AddJsonFile("appsettings.json")
    .Build();

var serviceProvider = services.ConfigureServicesForAgentIdentities(configuration);
```

---

## Call APIs

This section shows how to call APIs using each of the three authentication patterns.

### Call Microsoft Graph

The following examples demonstrate calling Microsoft Graph as a standard daemon, an autonomous agent, and an agent user identity:

```csharp
using Microsoft.Graph;

GraphServiceClient graphClient =
    serviceProvider.GetRequiredService<GraphServiceClient>();

// Standard daemon (app-only)
var users = await graphClient.Users.GetAsync();

// Autonomous agent (app-only with agent identity)
var apps = await graphClient.Applications.GetAsync(request =>
{
    request.Options.WithAuthenticationOptions(options =>
    {
        options.WithAgentIdentity("agent-identity-id");
        options.RequestAppToken = true;
    });
});

// Agent user identity (delegated with user context)
var me = await graphClient.Me.GetAsync(request =>
{
    request.Options.WithAuthenticationOptions(options =>
        options.WithAgentUserIdentity("agent-identity-id", "user@tenant.com"));
});
```

### Call custom APIs with IDownstreamApi

Use `IDownstreamApi` to call your own protected APIs with any of the three authentication patterns:

```csharp
using Microsoft.Identity.Abstractions;

IDownstreamApi downstreamApi =
    serviceProvider.GetRequiredService<IDownstreamApi>();

// Standard daemon
var result = await downstreamApi.GetForAppAsync<ApiResponse>(
    serviceName: "MyApi",
    options => options.RelativePath = "api/data");

// With agent identity
var result = await downstreamApi.GetForAppAsync<ApiResponse>(
    serviceName: "MyApi",
    options =>
    {
        options.RelativePath = "api/data";
        options.WithAgentIdentity("agent-identity-id");
    });

// Agent user identity
var result = await downstreamApi.GetForUserAsync<ApiResponse>(
    serviceName: "MyApi",
    options =>
    {
        options.RelativePath = "api/data";
        options.WithAgentUserIdentity("agent-identity-id", "user@tenant.com");
    });
```

### Make manual HTTP calls

Use `IAuthorizationHeaderProvider` directly when you need full control over HTTP requests:

```csharp
using Microsoft.Identity.Abstractions;

IAuthorizationHeaderProvider authProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

HttpClient httpClient = new HttpClient();

// Standard daemon
string authHeader = await authProvider.CreateAuthorizationHeaderForAppAsync(
    "https://graph.microsoft.com/.default");

httpClient.DefaultRequestHeaders.Add("Authorization", authHeader);
var response = await httpClient.GetStringAsync("https://graph.microsoft.com/v1.0/users");

// With agent identity
var options = new AuthorizationHeaderProviderOptions()
    .WithAgentIdentity("agent-identity-id");

authHeader = await authProvider.CreateAuthorizationHeaderForAppAsync(
    "https://graph.microsoft.com/.default",
    options);

// Agent user identity
var userOptions = new AuthorizationHeaderProviderOptions()
    .WithAgentUserIdentity("agent-identity-id", "user@tenant.com");

authHeader = await authProvider.CreateAuthorizationHeaderForUserAsync(
    new[] { "https://graph.microsoft.com/.default" },
    userOptions);
```

---

## Configure token caching

Choose a caching strategy based on your environment.

### Development: In-memory cache

Use in-memory caching for local development and testing:

```csharp
services.AddInMemoryTokenCaches();
```

### Production: Distributed cache

For production, use a distributed cache to persist tokens across app restarts and scale-out instances.

#### SQL Server

Store tokens in a SQL Server table:

```csharp
services.AddDistributedSqlServerCache(options =>
{
    options.ConnectionString = configuration["ConnectionStrings:TokenCache"];
    options.SchemaName = "dbo";
    options.TableName = "TokenCache";
});
services.AddDistributedTokenCaches();
```

#### Redis

Use Redis for high-performance, distributed token caching:

```csharp
services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = configuration["Redis:ConnectionString"];
    options.InstanceName = "TokenCache_";
});
services.AddDistributedTokenCaches();
```

#### Cosmos DB

Use Cosmos DB for globally distributed token caching:

```csharp
services.AddCosmosDbTokenCaches(options =>
{
    options.CosmosDbConnectionString = configuration["CosmosDb:ConnectionString"];
    options.DatabaseId = "TokenCache";
    options.ContainerId = "Tokens";
});
```

**Learn more:** [Token Cache Configuration](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)

---

## Explore Azure samples

Microsoft provides samples that demonstrate daemon app patterns.

### Sample repository

**[active-directory-dotnetcore-daemon-v2](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2)**

This repository contains multiple scenarios:

| **Sample** | **Description** | **Link** |
| --- | --- | --- |
| **1-Call-MSGraph** | Basic daemon calling Microsoft Graph with client credentials | [View Sample](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2/tree/master/1-Call-MSGraph) |
| **2-Call-OwnApi** | Daemon calling your own protected web API | [View Sample](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2/tree/master/2-Call-OwnApi) |
| **3-Using-KeyVault** | Daemon using Azure Key Vault for certificate storage | [View Sample](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2/tree/master/3-Using-KeyVault) |
| **4-Multi-Tenant** | Multi-tenant daemon application | [View Sample](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2/tree/master/4-Multi-Tenant) |
| **5-Call-MSGraph-ManagedIdentity** | Daemon using Managed Identity on Azure | [View Sample](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2/tree/master/5-Call-MSGraph-ManagedIdentity) |

### Compare sample patterns to production patterns

The Azure samples use **`TokenAcquirerFactory.GetDefaultInstance()`** for simplicity—the recommended approach for **simple console apps, prototypes, and tests**. This guide shows both patterns:

**TokenAcquirerFactory Pattern \(Azure Samples\):**

```csharp
// Simple, perfect for prototypes and tests
var tokenAcquirerFactory = TokenAcquirerFactory.GetDefaultInstance();
tokenAcquirerFactory.Services.AddDownstreamApi("MyApi", ...);
var serviceProvider = tokenAcquirerFactory.Build();
```

**Full ServiceCollection Pattern \(Production Apps\):**

```csharp
// More control, testable, follows DI best practices
var services = new ServiceCollection();
services.AddTokenAcquisition(true); // true = singleton
services.Configure<MicrosoftIdentityApplicationOptions>(...);
var serviceProvider = services.BuildServiceProvider();
```

**When to use which:**

- **Use `TokenAcquirerFactory`** for: Console apps, quick prototypes, unit tests, simple daemon services
- **Use `ServiceCollection`** for: Production applications, ASP.NET Core integration, complex DI scenarios, background services with `IHostedService`

Both approaches are fully supported and production-ready. Choose based on your application's complexity and integration needs.

---

## Troubleshoot common errors

### AADSTS700016: Application not found

**Cause:** Invalid `ClientId` or application not registered in the tenant.

**Solution:** Verify the `ClientId` in your configuration matches your Microsoft Entra app registration.

### AADSTS7000215: Invalid client secret

**Cause:** Client secret is incorrect, expired, or not configured.

**Solution:**

- Verify the secret in Azure portal matches your configuration
- Check secret expiration date
- Consider using certificates for production

### AADSTS700027: Client assertion contains invalid signature

**Cause:** Certificate not found, expired, or private key not accessible.

**Solution:**

- Verify certificate is installed in correct certificate store
- Check certificate distinguished name matches configuration
- Ensure application has permission to read private key
- See [Certificate Configuration Guide](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework#manage-certificates)

### AADSTS650052: The app needs access to a service

**Cause:** Required API permissions not granted or admin consent missing.

**Solution:**

1. Navigate to Azure portal → App registrations → Your app → API permissions
2. Add required permissions \(e.g., `User.Read.All` for Microsoft Graph\)
3. Click "Grant admin consent" button

### Agent identity errors

#### AADSTS50105: The signed in user is not assigned to a role

**Cause:** Agent identity not properly configured or not assigned to the application.

**Solution:**

- Verify agent identity exists in Microsoft Entra ID
- Ensure agent identity is linked to your application
- Check that agent identity has required permissions

#### Tokens acquired but with wrong permissions

**Cause:** Using agent user identity but requesting app permissions, or vice versa.

**Solution:**

- For **app-only tokens**: Use `CreateAuthorizationHeaderForAppAsync` with `WithAgentIdentity`
- For **delegated tokens**: Use `CreateAuthorizationHeaderForUserAsync` with `WithAgentUserIdentity`
- Ensure API permissions match token type \(application vs. delegated\)

### Token caching issues

**Problem:** Tokens aren't cached, which forces a new acquisition each time.

**Solution:**

- For agent user identity: Reuse the same `ClaimsPrincipal` instance across calls
- Verify distributed cache connection \(if using Redis/SQL\)
- Enable debug logging to see cache operations

**Detailed diagnostics:** [Logging & Diagnostics Guide](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging)

---

## Related content

- [Calling downstream APIs from web APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis) - OBO patterns
- [MSAL.NET framework guide](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework) - Token cache and certificate configuration for .NET Framework
- [Certificate configuration](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview) - Loading certificates from Key Vault, store, file, or Base64
- [Token cache configuration](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview) - Production caching strategies
- [Logging and diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging) - Troubleshoot token acquisition issues
- [Customization guide](https://learn.microsoft.com/en-us/entra/msidweb/advanced/customization) - Advanced configuration patterns
- [Microsoft identity platform daemon app documentation](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-overview)
- [Azure Samples: daemon applications](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2)
- [Microsoft.Identity.Web NuGet package](https://www.nuget.org/packages/Microsoft.Identity.Web)
- [Microsoft.Identity.Abstractions API reference](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.abstractions)

---
