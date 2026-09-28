<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Integrate MSAL.NET with Microsoft.Identity.Web in .NET Framework

This guide shows you how to use Microsoft.Identity.Web token cache and certificate packages with MSAL.NET in .NET Framework, .NET Standard 2.0, and classic .NET applications \(.NET 4.7.2+\).

## Understand the overview

Starting with **Microsoft.Identity.Web 1.17+**, you can use Microsoft.Identity.Web utility packages with MSAL.NET in non-ASP.NET Core environments.

### Identify package benefits

| Feature | Benefit |
| --- | --- |
| **Token Cache Serialization** | Reusable cache adapters for in-memory, SQL Server, Redis, Cosmos DB, PostgreSQL |
| **Certificate Helpers** | Simplified certificate loading from KeyVault, file system, or cert stores |
| **Claims Extensions** | Utility methods for `ClaimsPrincipal` manipulation |
| **.NET Standard 2.0** | Compatible with .NET Framework 4.7.2+, .NET Core, and .NET 5+ |
| **Minimal Dependencies** | Targeted packages without ASP.NET Core dependencies |

### Review supported scenarios

The following scenarios are supported with the targeted utility packages.

- **.NET Framework Console Applications** \(daemon scenarios\)
- **Desktop Applications** \(.NET Framework\)
- **Worker Services** \(.NET Framework\)
- **.NET Standard 2.0 Libraries** \(cross-platform compatibility\)
- **Non-web MSAL.NET applications**

Note

For ASP.NET MVC/Web API applications, see [OWIN Integration](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/owin) instead.

---

## Select packages

Choose the package that matches your scenario.

### Identify core packages for MSAL.NET

| Package | Purpose | Dependencies | .NET Target |
| --- | --- | --- | --- |
| **Microsoft.Identity.Web.TokenCache** | Token cache serializers, `ClaimsPrincipal` extensions | Minimal | .NET Standard 2.0 |
| **Microsoft.Identity.Web.Certificate** | Certificate loading utilities | Minimal | .NET Standard 2.0 |

### Install packages

Use one of the following methods to add the packages to your project.

**Package Manager Console:**

```powershell
# Token cache serialization
Install-Package Microsoft.Identity.Web.TokenCache

# Certificate management
Install-Package Microsoft.Identity.Web.Certificate
```

**.NET CLI:**

```bash
dotnet add package Microsoft.Identity.Web.TokenCache
dotnet add package Microsoft.Identity.Web.Certificate
```

## Understand core package limitations

The core `Microsoft.Identity.Web` package includes ASP.NET Core dependencies \(`Microsoft.AspNetCore.*`\), which:

- Are incompatible with ASP.NET Framework
- Increase package size unnecessarily
- Create dependency conflicts

**Use targeted packages instead** for .NET Framework and .NET Standard scenarios.

---

## Configure token cache serialization

### Understand token cache adapters

Microsoft.Identity.Web provides token cache adapters that work seamlessly with MSAL.NET's `IConfidentialClientApplication`.

### Build a confidential client with token cache

The following example creates a confidential client application and attaches an in-memory token cache.

```csharp
using Microsoft.Identity.Client;
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.TokenCacheProviders;

public class MsalAppBuilder
{
    private static IConfidentialClientApplication _app;

    public static IConfidentialClientApplication BuildConfidentialClientApplication()
    {
        if (_app == null)
        {
            string clientId = ConfigurationManager.AppSettings["AzureAd:ClientId"];
            string clientSecret = ConfigurationManager.AppSettings["AzureAd:ClientSecret"];
            string tenantId = ConfigurationManager.AppSettings["AzureAd:TenantId"];

            // Create the confidential client application
            _app = ConfidentialClientApplicationBuilder.Create(clientId)
                .WithClientSecret(clientSecret)
                .WithTenantId(tenantId)
                .WithAuthority(AzureCloudInstance.AzurePublic, tenantId)
                .Build();

            // Add token cache serialization (choose one option below)
            _app.AddInMemoryTokenCache();
        }

        return _app;
    }
}
```

### Choose token cache options

Select the cache provider that best fits your deployment scenario.

#### Configure in-memory token cache

The following example adds a simple in-memory cache:

```csharp
using Microsoft.Identity.Web.TokenCacheProviders;

_app.AddInMemoryTokenCache();
```

**In-memory cache with size limits** \(Microsoft.Identity.Web 1.20+\):

```csharp
using Microsoft.Extensions.Caching.Memory;

_app.AddInMemoryTokenCache(services =>
{
    // Configure memory cache options
    services.Configure<MemoryCacheOptions>(options =>
    {
        options.SizeLimit = 5000000;  // 5 MB limit
    });
});
```

**Characteristics:**

- Fast access
- No external dependencies
- Not shared across processes
- Lost on app restart

**Use case:** Single-instance console apps, desktop applications

---

#### Configure distributed in-memory token cache

Use the following code to add a distributed in-memory cache for multi-instance environments:

```csharp
_app.AddDistributedTokenCaches(services =>
{
    // Requires: Microsoft.Extensions.Caching.Memory (NuGet)
    services.AddDistributedMemoryCache();
});
```

**Characteristics:**

- Shared across app instances
- Better for load-balanced scenarios
- Requires additional NuGet package
- Still lost on app restart

**Use case:** Multi-instance services with acceptable token re-acquisition

---

#### Configure SQL Server token cache

Use the following code to add a persistent, distributed SQL Server cache:

```csharp
using Microsoft.Extensions.Caching.SqlServer;

_app.AddDistributedTokenCaches(services =>
{
    // Requires: Microsoft.Extensions.Caching.SqlServer (NuGet)
    services.AddDistributedSqlServerCache(options =>
    {
        options.ConnectionString = ConfigurationManager.ConnectionStrings["TokenCache"].ConnectionString;
        options.SchemaName = "dbo";
        options.TableName = "TokenCache";

        // IMPORTANT: Set expiration above token lifetime
        // Access tokens typically expire after 1 hour
        options.DefaultSlidingExpiration = TimeSpan.FromMinutes(90);
    });
});
```

Run the following SQL to create the required cache table:

```sql
-- Create the cache table
CREATE TABLE [dbo].[TokenCache] (
    [Id] NVARCHAR(449) NOT NULL,
    [Value] VARBINARY(MAX) NOT NULL,
    [ExpiresAtTime] DATETIMEOFFSET NOT NULL,
    [SlidingExpirationInSeconds] BIGINT NULL,
    [AbsoluteExpiration] DATETIMEOFFSET NULL,
    PRIMARY KEY ([Id])
);

-- Create index for performance
CREATE INDEX [Index_ExpiresAtTime] ON [dbo].[TokenCache] ([ExpiresAtTime]);
```

**Characteristics:**

- Persistent across restarts
- Shared across multiple instances
- Reliable and scalable
- Requires SQL Server setup

**Use case:** Production daemon services, scheduled tasks, multi-instance workers

---

#### Configure Redis token cache

Use the following code to add a high-performance Redis distributed cache:

```csharp
using StackExchange.Redis;
using Microsoft.Extensions.Caching.StackExchangeRedis;

_app.AddDistributedTokenCaches(services =>
{
    // Requires: Microsoft.Extensions.Caching.StackExchangeRedis (NuGet)
    services.AddStackExchangeRedisCache(options =>
    {
        options.Configuration = ConfigurationManager.AppSettings["Redis:ConnectionString"];
        options.InstanceName = "TokenCache_";
    });
});
```

The following example shows a production-ready Redis configuration:

```csharp
services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = ConfigurationManager.AppSettings["Redis:ConnectionString"];
    options.InstanceName = "MyDaemonApp_";

    // Optional: Configure Redis options
    options.ConfigurationOptions = new ConfigurationOptions
    {
        AbortOnConnectFail = false,
        ConnectTimeout = 5000,
        SyncTimeout = 5000
    };
});
```

**Characteristics:**

- Extremely fast
- Shared across instances
- Persistent \(with Redis persistence enabled\)
- Requires Redis server

**Use case:** High-volume daemon apps, distributed systems, microservices

---

#### Configure Cosmos DB token cache

Use the following code to add a globally distributed Cosmos DB cache:

```csharp
using Microsoft.Extensions.Caching.Cosmos;

_app.AddDistributedTokenCaches(services =>
{
    // Requires: Microsoft.Extensions.Caching.Cosmos (preview)
    services.AddCosmosCache(options =>
    {
        options.ContainerName = "TokenCache";
        options.DatabaseName = "IdentityCache";
        options.ClientBuilder = new CosmosClientBuilder(
            ConfigurationManager.AppSettings["CosmosConnectionString"]);
        options.CreateIfNotExists = true;
    });
});
```

**Characteristics:**

- Globally distributed
- Highly available
- Automatic scaling
- Higher latency than Redis
- Higher cost

**Use case:** Global daemon services, geo-distributed applications

---

#### Configure PostgreSQL token cache

Use the following code to add a distributed PostgreSQL cache:

```csharp
_app.AddDistributedTokenCaches(services =>
{
    // Requires: Microsoft.Extensions.Caching.Postgres (NuGet)
    services.AddDistributedPostgresCache(options =>
    {
        options.ConnectionString = ConfigurationManager.ConnectionStrings["PostgresCache"].ConnectionString;
        options.SchemaName = ConfigurationManager.AppSettings["PostgresCache:SchemaName"];
        options.TableName = ConfigurationManager.AppSettings["PostgresCache:TableName"];
        options.CreateIfNotExists = bool.Parse(
            ConfigurationManager.AppSettings["PostgresCache:CreateIfNotExists"] ?? "true");

        // Set expiration above token lifetime.
        // Access tokens typically expire after 1 hour.
        options.DefaultSlidingExpiration = TimeSpan.FromMinutes(90);
    });
});
```

**Characteristics:**

- Persistent across restarts
- Shared across multiple instances
- Familiar SQL semantics
- Works with Azure Database for PostgreSQL
- Requires a PostgreSQL server

**Use case:** Applications already using PostgreSQL as their primary database, or Azure-hosted services using Azure Database for PostgreSQL

---

### Build a complete daemon application

The following example shows a full daemon application that acquires tokens using client credentials and a SQL Server token cache.

```csharp
using Microsoft.Identity.Client;
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.TokenCacheProviders;
using System;
using System.Threading.Tasks;

namespace DaemonApp
{
    class Program
    {
        private static IConfidentialClientApplication _app;

        static async Task Main(string[] args)
        {
            // Build confidential client with token cache
            _app = BuildConfidentialClient();

            // Acquire token for app-only access
            string[] scopes = new[] { "https://graph.microsoft.com/.default" };

            try
            {
                var result = await _app.AcquireTokenForClient(scopes)
                    .ExecuteAsync();

                Console.WriteLine($"Token acquired successfully!");
                Console.WriteLine($"Token source: {result.AuthenticationResultMetadata.TokenSource}");
                Console.WriteLine($"Expires on: {result.ExpiresOn}");

                // Use token to call API
                await CallProtectedApi(result.AccessToken);
            }
            catch (MsalServiceException ex)
            {
                Console.WriteLine($"Error acquiring token: {ex.ErrorCode}");
                Console.WriteLine($"CorrelationId: {ex.CorrelationId}");
            }
        }

        private static IConfidentialClientApplication BuildConfidentialClient()
        {
            var app = ConfidentialClientApplicationBuilder
                .Create(ConfigurationManager.AppSettings["ClientId"])
                .WithClientSecret(ConfigurationManager.AppSettings["ClientSecret"])
                .WithTenantId(ConfigurationManager.AppSettings["TenantId"])
                .Build();

            // Add SQL Server token cache for persistence
            app.AddDistributedTokenCaches(services =>
            {
                services.AddDistributedSqlServerCache(options =>
                {
                    options.ConnectionString = ConfigurationManager
                        .ConnectionStrings["TokenCache"].ConnectionString;
                    options.SchemaName = "dbo";
                    options.TableName = "TokenCache";
                    options.DefaultSlidingExpiration = TimeSpan.FromMinutes(90);
                });
            });

            return app;
        }

        private static async Task CallProtectedApi(string accessToken)
        {
            // Your API call logic
        }
    }
}
```

---

## Manage certificates

### Understand certificate loading

Microsoft.Identity.Web simplifies certificate loading from various sources for client credential flows.

### Load certificates with DefaultCertificateLoader

The following example demonstrates how to load a certificate from Azure Key Vault and create a confidential client application.

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Client;

public class CertificateHelper
{
    public static IConfidentialClientApplication CreateAppWithCertificate()
    {
        string clientId = ConfigurationManager.AppSettings["AzureAd:ClientId"];
        string tenantId = ConfigurationManager.AppSettings["AzureAd:TenantId"];

        // Define certificate source
        var certDescription = CertificateDescription.FromKeyVault(
            keyVaultUrl: "https://my-keyvault.vault.azure.net",
            keyVaultCertificateName: "MyCertificate"
        );

        // Load certificate
        ICertificateLoader certificateLoader = new DefaultCertificateLoader();
        certificateLoader.LoadIfNeeded(certDescription);

        // Create confidential client with certificate
        var app = ConfidentialClientApplicationBuilder.Create(clientId)
            .WithCertificate(certDescription.Certificate)
            .WithTenantId(tenantId)
            .Build();

        // Add token cache
        app.AddInMemoryTokenCache();

        return app;
    }
}
```

### Choose certificate sources

#### Load from Azure Key Vault

Load a certificate stored in Azure Key Vault by specifying the vault URL and certificate name.

```csharp
var certDescription = CertificateDescription.FromKeyVault(
    keyVaultUrl: "https://my-keyvault.vault.azure.net",
    keyVaultCertificateName: "MyApplicationCert"
);

ICertificateLoader loader = new DefaultCertificateLoader();
loader.LoadIfNeeded(certDescription);

var app = ConfidentialClientApplicationBuilder.Create(clientId)
    .WithCertificate(certDescription.Certificate)
    .WithTenantId(tenantId)
    .Build();
```

**Prerequisites:**

- Managed Identity or Service Principal with Key Vault access
- `Azure.Identity` NuGet package
- Key Vault permission: `Get` on certificates

---

#### Load from certificate store

Load a certificate from the Windows certificate store by distinguished name.

```csharp
var certDescription = CertificateDescription.FromStoreWithDistinguishedName(
    distinguishedName: "CN=MyApp.contoso.com",
    storeName: StoreName.My,
    storeLocation: StoreLocation.CurrentUser
);

ICertificateLoader loader = new DefaultCertificateLoader();
loader.LoadIfNeeded(certDescription);

var app = ConfidentialClientApplicationBuilder.Create(clientId)
    .WithCertificate(certDescription.Certificate)
    .WithTenantId(tenantId)
    .Build();
```

You can also find a certificate by thumbprint:

```csharp
var certDescription = CertificateDescription.FromStoreWithThumbprint(
    thumbprint: "ABCDEF1234567890ABCDEF1234567890ABCDEF12",
    storeName: StoreName.My,
    storeLocation: StoreLocation.LocalMachine
);
```

---

#### Load from file system

Load a certificate from a PFX file on the local file system.

```csharp
var certDescription = CertificateDescription.FromPath(
    path: @"C:\Certificates\MyAppCert.pfx",
    password: ConfigurationManager.AppSettings["Certificate:Password"]
);

ICertificateLoader loader = new DefaultCertificateLoader();
loader.LoadIfNeeded(certDescription);

var app = ConfidentialClientApplicationBuilder.Create(clientId)
    .WithCertificate(certDescription.Certificate)
    .WithTenantId(tenantId)
    .Build();
```

**Security note:** Never hardcode passwords. Use secure configuration.

---

#### Load from Base64-encoded string

Load a certificate from a Base64-encoded string stored in configuration.

```csharp
string base64Cert = ConfigurationManager.AppSettings["Certificate:Base64"];

var certDescription = CertificateDescription.FromBase64Encoded(
    base64EncodedValue: base64Cert,
    password: ConfigurationManager.AppSettings["Certificate:Password"]  // Optional
);

ICertificateLoader loader = new DefaultCertificateLoader();
loader.LoadIfNeeded(certDescription);
```

---

### Configure certificate loading from App.config

Define certificate settings in your App.config file and load them at runtime.

**App.config:**

```xml
<appSettings>
  <add key="AzureAd:ClientId" value="your-client-id" />
  <add key="AzureAd:TenantId" value="your-tenant-id" />

  <!-- Option 1: KeyVault -->
  <add key="Certificate:SourceType" value="KeyVault" />
  <add key="Certificate:KeyVaultUrl" value="https://my-vault.vault.azure.net" />
  <add key="Certificate:KeyVaultCertificateName" value="MyCert" />

  <!-- Option 2: Store -->
  <!--
  <add key="Certificate:SourceType" value="StoreWithThumbprint" />
  <add key="Certificate:CertificateThumbprint" value="ABCD..." />
  <add key="Certificate:CertificateStorePath" value="CurrentUser/My" />
  -->
</appSettings>

<connectionStrings>
  <add name="TokenCache"
       connectionString="Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=TokenCache;Integrated Security=True;" />
</connectionStrings>
```

Use the following helper method to load the certificate based on configuration:

```csharp
public static CertificateDescription GetCertificateFromConfig()
{
    string sourceType = ConfigurationManager.AppSettings["Certificate:SourceType"];

    return sourceType switch
    {
        "KeyVault" => CertificateDescription.FromKeyVault(
            ConfigurationManager.AppSettings["Certificate:KeyVaultUrl"],
            ConfigurationManager.AppSettings["Certificate:KeyVaultCertificateName"]
        ),

        "StoreWithThumbprint" => CertificateDescription.FromStoreWithThumbprint(
            ConfigurationManager.AppSettings["Certificate:CertificateThumbprint"],
            StoreName.My,
            StoreLocation.CurrentUser
        ),

        _ => throw new ConfigurationErrorsException("Invalid certificate source type")
    };
}
```

---

## Explore sample applications

Review these samples to see working implementations.

### Review official Microsoft samples

The following table lists official samples that demonstrate token caching and certificate loading.

| Sample | Platform | Description |
| --- | --- | --- |
| [ConfidentialClientTokenCache](https://github.com/Azure-Samples/active-directory-dotnet-v1-to-v2/tree/master/ConfidentialClientTokenCache) | Console \(.NET Framework\) | Token cache serialization patterns |
| [active-directory-dotnetcore-daemon-v2](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2) | Console \(.NET Core\) | Certificate loading from Key Vault |

---

## Follow best practices

Apply these patterns to build reliable and secure applications.

### Follow recommended patterns

**1. Use the singleton pattern for IConfidentialClientApplication:**

Create a single instance and reuse it across your application.

```csharp
private static IConfidentialClientApplication _app;

public static IConfidentialClientApplication GetApp()
{
    if (_app == null)
    {
        _app = ConfidentialClientApplicationBuilder.Create(clientId)
            .WithClientSecret(clientSecret)
            .WithTenantId(tenantId)
            .Build();

        _app.AddDistributedTokenCaches(/* ... */);
    }

    return _app;
}
```

**2. Set appropriate token cache expiration:**

Configure the sliding expiration above the token lifetime to prevent unnecessary re-acquisition.

```csharp
// Access tokens typically expire after 1 hour
// Set cache expiration ABOVE token lifetime
options.DefaultSlidingExpiration = TimeSpan.FromMinutes(90);
```

**3. Use secure certificate storage:**

Store certificates in Azure Key Vault or a properly secured certificate store.

```csharp
// Azure Key Vault (production)
var cert = CertificateDescription.FromKeyVault(keyVaultUrl, certName);

// Certificate store with proper permissions
var cert = CertificateDescription.FromStoreWithThumbprint(
    thumbprint, StoreName.My, StoreLocation.LocalMachine);
```

**4. Implement proper error handling:**

Catch MSAL exceptions and log the correlation ID for troubleshooting.

```csharp
try
{
    var result = await app.AcquireTokenForClient(scopes).ExecuteAsync();
}
catch (MsalServiceException ex)
{
    logger.Error($"Token acquisition failed. CorrelationId: {ex.CorrelationId}, ErrorCode: {ex.ErrorCode}");
    throw;
}
```

**5. Use a distributed cache for production:**

A distributed cache shares tokens across instances and persists across restarts.

```csharp
// Correct for daemon services
app.AddDistributedTokenCaches(services =>
{
    services.AddDistributedSqlServerCache(/* ... */);
});
```

### Avoid common mistakes

**1. Don't create new IConfidentialClientApplication instances repeatedly:**

```csharp
// Wrong - creates new instance every time
public void AcquireToken()
{
    var app = ConfidentialClientApplicationBuilder.Create(clientId).Build();
    // ...
}

// Correct - use singleton
private static readonly IConfidentialClientApplication _app = BuildApp();
```

**2. Don't hardcode secrets:**

```csharp
// Wrong
.WithClientSecret("supersecretvalue123")

// Correct
.WithClientSecret(ConfigurationManager.AppSettings["AzureAd:ClientSecret"])
```

**3. Don't use in-memory cache for multi-instance services:**

```csharp
// Wrong for services with multiple instances
app.AddInMemoryTokenCache();

// Correct - use distributed cache
app.AddDistributedTokenCaches(services =>
{
    services.AddDistributedSqlServerCache(/* ... */);
});
```

**4. Don't ignore certificate validation:**

```csharp
// Wrong - skips validation
ServicePointManager.ServerCertificateValidationCallback = (sender, cert, chain, errors) => true;

// Correct - validate certificates properly
```

---

## Migrate from ADAL.NET

Review the key differences and update your code to use MSAL.NET with Microsoft.Identity.Web.

### Understand key differences

| Aspect | ADAL.NET \(deprecated\) | MSAL.NET + Microsoft.Identity.Web |
| --- | --- | --- |
| **Scopes** | Resource-based \(`https://graph.microsoft.com`\) | Scope-based \(`https://graph.microsoft.com/.default`\) |
| **Token Cache** | Manual serialization required | Built-in adapters via extension methods |
| **Certificates** | Manual X509Certificate2 loading | `DefaultCertificateLoader` with multiple sources |
| **Authority** | Fixed at construction | Can be overridden per request |

### Compare migration examples

**ADAL.NET \(Old\):**

```csharp
AuthenticationContext authContext = new AuthenticationContext(authority);
ClientCredential credential = new ClientCredential(clientId, clientSecret);
AuthenticationResult result = await authContext.AcquireTokenAsync(resource, credential);
```

**MSAL.NET with Microsoft.Identity.Web \(New\):**

```csharp
var app = ConfidentialClientApplicationBuilder.Create(clientId)
    .WithClientSecret(clientSecret)
    .WithTenantId(tenantId)
    .Build();

app.AddInMemoryTokenCache();  // Add token cache

string[] scopes = new[] { "https://graph.microsoft.com/.default" };
AuthenticationResult result = await app.AcquireTokenForClient(scopes).ExecuteAsync();
```

## Explore related content

Use these resources to learn more about related scenarios.

- [Daemon applications](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app)
- [OWIN integration](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/owin)
- [ASP.NET Framework overview](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/aspnet-framework)
- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
