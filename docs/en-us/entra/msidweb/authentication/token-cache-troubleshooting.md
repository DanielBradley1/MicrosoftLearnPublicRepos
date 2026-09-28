<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-troubleshooting -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Resolve token cache issues in Microsoft.Identity.Web

This article helps you diagnose and resolve token cache problems in Microsoft.Identity.Web. Token cache issues can cause authentication failures, degraded performance, or unexpected sign-in prompts. For an overview of how token caching works in Microsoft.Identity.Web, see [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview).

## Prerequisites

Before you troubleshoot, confirm the following:

- You're using a [supported version of Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web).
- Your application has token caching configured in `Program.cs` or `Startup.cs`.
- You have access to application logs and, if applicable, your distributed cache infrastructure.

## Enable token cache logging and diagnostics

Enable detailed logging as your first diagnostic step. Microsoft.Identity.Web uses the ASP.NET Core logging infrastructure and emits events through the Microsoft Authentication Library \(MSAL\).

### Enable MSAL logging

Set the log level to `Debug` for identity libraries in your `appsettings.json`:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.Identity.Web": "Debug",
      "Microsoft.IdentityModel": "Debug"
    }
  }
}
```

### Subscribe to MSAL cache events

Subscribe to MSAL token cache notification events to track cache hits, misses, and serialization activity:

```csharp
services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDistributedTokenCaches();

services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.OnL2CacheFailure = (ex) =>
    {
        logger.LogWarning(ex, "L2 cache failure encountered.");
        // Return true to allow the operation to continue despite the cache failure.
        // Return false to propagate the exception.
        return true;
    };
});
```

### Monitor cache metrics

For production monitoring, track these key metrics:

- **Cache hit rate** — a low hit rate indicates tokens aren't being retrieved from cache.
- **L2 cache latency** — high latency suggests a distributed cache connectivity or performance issue.
- **Cache serialization errors** — errors during read or write indicate corruption or version mismatch.
- **Memory consumption** — sustained growth can indicate missing eviction policies.

## Distributed cache \(L2\) connection failures

### Symptom

Application logs show connection timeout errors or intermittent authentication failures. Users experience sign-in delays, and you see exceptions such as:

```text
Microsoft.Extensions.Caching.StackExchangeRedis.RedisCache:
  StackExchange.Redis.RedisConnectionException: 
  No connection is active/available to service this operation.
```

Or for SQL Server distributed cache:

```text
Microsoft.Data.SqlClient.SqlException:
  A network-related or instance-specific error occurred while 
  establishing a connection to SQL Server.
```

### Cause

The distributed cache backing store \(Redis or SQL Server\) is unreachable. Common causes include:

- Incorrect connection string or expired access credentials.
- Network firewall rules blocking the connection from the app host.
- The cache service is down or undergoing maintenance.
- SSL/TLS configuration mismatch between the client and cache server.

### Diagnostic steps

Follow these steps to identify the connection failure:

1. **Verify connectivity.** From the application host, test the connection to Redis or SQL Server by using `Test-NetConnection` \(PowerShell\) or `redis-cli`.
2. **Check the connection string.** Confirm the connection string matches the cache server's hostname, port, and credentials.
3. **Review firewall rules.** In Azure, verify that the app service or virtual network can reach the cache resource.
4. **Check service health.** In the Azure portal, review the health and metrics of your Azure Cache for Redis or SQL Database instance.

### Solution

**Step 1: Correct the connection string**

Verify the connection string in your `appsettings.json`:

```json
{
  "ConnectionStrings": {
    "Redis": "your-redis-instance.redis.cache.windows.net:6380,password=your-access-key,ssl=True,abortConnect=False"
  }
}
```

Important

Set `abortConnect=False` in the Redis connection string. This setting allows the application to reconnect automatically after transient connection failures rather than throwing immediately.

**Step 2: Configure retry and resilience**

Configure the `OnL2CacheFailure` callback so your application degrades gracefully when the distributed cache is temporarily unavailable:

```csharp
services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.OnL2CacheFailure = (ex) =>
    {
        // Log the failure for monitoring and alerting.
        logger.LogWarning(ex, "Distributed token cache is unavailable. " +
            "Falling back to in-memory cache.");
        return true; // Continue without the L2 cache.
    };

    // Set a timeout to avoid blocking the request pipeline.
    options.AbsoluteExpirationRelativeToNow = TimeSpan.FromHours(12);
});
```

**Step 3: Open firewall rules**

If the application runs in Azure App Service and the cache is in a virtual network, add the App Service outbound IP addresses to the cache firewall allow list.

## Cache deserialization errors

### Symptom

After you upgrade Microsoft.Identity.Web or MSAL.NET, the application throws deserialization exceptions when reading from the distributed cache. Users must sign in again, and you see exceptions such as:

```text
System.Text.Json.JsonException:
  The JSON value could not be converted to the expected type.
```

Or:

```text
Microsoft.Identity.Client.MsalClientException:
  Error code: json_parse_failed
```

### Cause

The token cache serialization format changed between library versions. Tokens cached by the previous version can't be deserialized by the new version. This issue occurs most often during major version upgrades of MSAL.NET or Microsoft.Identity.Web.

### Solution

**Option A: Clear the cache**

The simplest fix is to clear all entries in the distributed cache. Users reauthenticate once, and subsequent tokens are written in the new format.

Flush the Redis cache:

```bash
redis-cli FLUSHDB
```

Or clear the SQL Server distributed cache table:

```sql
DELETE FROM [dbo].[TokenCache];
```

Note

Clearing the cache causes all active users to reauthenticate. Plan this operation during a maintenance window if your application serves a large user base.

**Option B: Handle deserialization errors gracefully**

Configure the cache adapter to treat deserialization failures as cache misses rather than fatal errors:

```csharp
services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.OnL2CacheFailure = (ex) =>
    {
        if (ex is JsonException or MsalClientException)
        {
            logger.LogWarning(ex, "Cache deserialization failed. " +
                "Treating as cache miss.");
            return true;
        }
        return false; // Propagate unexpected errors.
    };
});
```

With this approach, affected cache entries are automatically replaced as users reauthenticate, and no manual cache flush is required.

## Encryption key mismatch across servers

### Symptom

Deserialization errors occur in multi-instance deployments even though the distributed cache is working. Tokens cached by one server instance can't be read by another. You see `json_parse_failed` or `IDW10802` errors in the logs.

### Cause

When cache encryption is enabled \(`options.Encrypt = true`\), Microsoft.Identity.Web uses ASP.NET Core Data Protection to encrypt cache entries. By default, each server instance generates its own Data Protection keys, so one instance can't decrypt entries written by another.

### Solution

Configure ASP.NET Core Data Protection to share encryption keys across all server instances.

**Option A: Azure Blob Storage + Azure Key Vault \(recommended for Azure deployments\)**

```csharp
using Microsoft.AspNetCore.DataProtection;
using Azure.Identity;

builder.Services.AddDataProtection()
    .PersistKeysToAzureBlobStorage(
        new Uri("https://yourstorageaccount.blob.core.windows.net/dataprotection/keys.xml"),
        new DefaultAzureCredential())
    .ProtectKeysWithAzureKeyVault(
        new Uri("https://yourkeyvault.vault.azure.net/keys/dataprotection-key"),
        new DefaultAzureCredential());

builder.Services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.Encrypt = true;
});
```

This configuration stores the Data Protection key ring in Azure Blob Storage and protects the keys at rest with Azure Key Vault. All application instances that access the same blob and key can encrypt and decrypt each other's cache entries.

**Option B: Shared file system with certificate protection**

```csharp
builder.Services.AddDataProtection()
    .PersistKeysToFileSystem(new DirectoryInfo(@"\\server\share\keys"))
    .ProtectKeysWithCertificate(certificate);
```

Tip

When rotating the Data Protection certificate, use `UnprotectKeysWithAnyCertificate` to include both the current and previous certificates. This allows decryption of keys that were protected with the old certificate during the rotation window.

## Memory growth with in-memory cache

### Symptom

Application memory consumption grows steadily over time. If the application runs in a container or App Service plan with a fixed memory limit, it eventually restarts or throws `OutOfMemoryException`. Monitoring shows the managed heap growing without reclamation by garbage collection.

### Cause

Using `AddInMemoryTokenCaches()` without size limits causes unbounded cache growth. This situation is especially problematic in applications that serve many users, because each user's token entry consumes memory indefinitely.

By default, `MemoryCache` doesn't enforce a maximum size and doesn't evict entries unless an expiration policy is set.

### Solution

**Option A: Set a size limit and sliding expiration**

Configure the in-memory cache with expiration policies:

```csharp
services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();

services.Configure<MsalMemoryTokenCacheOptions>(options =>
{
    options.AbsoluteExpirationRelativeToNow = TimeSpan.FromHours(12);
    options.SlidingExpiration = TimeSpan.FromHours(2);
});
```

With these settings, entries expire after 12 hours regardless of access, and entries idle for 2 hours are evicted earlier.

**Option B: Switch to a distributed cache**

For applications with many concurrent users, an in-memory cache doesn't scale. Switch to a distributed cache such as Redis:

```csharp
services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = Configuration.GetConnectionString("Redis");
});

services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDistributedTokenCaches();
```

A distributed cache offloads memory from the application process, persists tokens across restarts, and supports multi-instance deployments.

**Option C: Use the L1/L2 hybrid architecture**

Microsoft.Identity.Web supports a hybrid approach that combines a fast in-memory L1 cache with a persistent distributed L2 cache. Configure the L1/L2 hybrid cache:

```csharp
services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDistributedTokenCaches();

services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.L1CacheOptions = new MsalMemoryTokenCacheOptions
    {
        AbsoluteExpirationRelativeToNow = TimeSpan.FromMinutes(5),
        SlidingExpiration = TimeSpan.FromMinutes(2)
    };
});
```

With L1/L2 caching, frequently accessed tokens are served from in-memory \(L1\) with sub-millisecond latency. The L2 cache provides persistence and cross-instance consistency. The L1 cache uses short expirations to limit memory growth.

## Repeated MFA or consent prompts

### Symptom

Users are repeatedly prompted for multifactor authentication \(MFA\) or consent even though they completed these steps recently. The application can't find existing tokens in the cache.

### Cause

This issue occurs when the token cache lookup fails to match a cached entry to the current user account. Common causes include:

- The cache key differs from the one used when the token was stored. This situation can occur if the `HomeAccountId` or tenant context changes.
- The application runs multiple instances behind a load balancer with in-memory caching, and requests route to an instance that doesn't have the user's token.
- The requested claims or scopes changed, so the cached token doesn't satisfy the new requirement.
- Session affinity isn't enabled, so users route to different instances that lack their cached tokens.

### Diagnostic steps

Follow these steps to identify why tokens aren't found in the cache:

1. **Check the cache type.** If you use `AddInMemoryTokenCaches()` in a multi-instance deployment, tokens cached on one instance aren't available on another. Switch to a distributed cache.
2. **Verify the account identifier.** Enable Debug-level logging and search for the `HomeAccountId`. Confirm that the identifier is consistent across requests.
3. **Inspect the scopes.** Confirm that the scopes requested by `GetAccessTokenForUserAsync` match the scopes originally consented to. A scope mismatch causes MSAL to request a new token.
4. **Review Conditional Access policies.** A Microsoft Entra ID Conditional Access policy that requires step-up authentication for specific resources causes additional prompts unrelated to caching.

### Solution

**Step 1: Switch to distributed caching**

If your application runs multiple instances, use a distributed cache to share tokens across instances:

```csharp
services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = Configuration.GetConnectionString("Redis");
});

services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDistributedTokenCaches();
```

**Step 2: Verify consistent scopes**

Ensure the scopes you request when acquiring tokens match the scopes configured during authentication:

```csharp
// In authentication setup — initial scopes.
.EnableTokenAcquisitionToCallDownstreamApi(new[] { "User.Read", "Mail.Read" })

// When acquiring a token — use the same scopes.
var token = await tokenAcquisition.GetAccessTokenForUserAsync(
    new[] { "User.Read", "Mail.Read" });
```

**Step 3: Enable session affinity \(temporary workaround\)**

If you can't switch to a distributed cache right away, enable session affinity \(sticky sessions\) on your load balancer. Session affinity routes a user's requests to the same instance. This approach is a temporary workaround with scalability limitations.

## Cache performance issues

### Symptom

Token retrieval is slow and downstream API calls have increased latency. Monitoring shows high average response times for token acquisition requests. The latency isn't from the identity provider—tokens are served from cache.

### Cause

Cache performance issues typically result from:

- **High L2 cache latency.** The distributed cache is under heavy load, geographically distant from the application, or using an undersized service tier.
- **Large token cache entries.** Applications that cache tokens for many resources per user can produce large serialized cache entries that are slow to read and write.
- **No L1 cache.** Every token acquisition goes to the distributed cache over the network, even for tokens that are used frequently.

### Solution

**Step 1: Enable the L1 in-memory cache**

The L1 cache stores frequently accessed tokens in process memory, avoiding network round trips to L2:

```csharp
services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.L1CacheOptions = new MsalMemoryTokenCacheOptions
    {
        AbsoluteExpirationRelativeToNow = TimeSpan.FromMinutes(5),
        SlidingExpiration = TimeSpan.FromMinutes(2)
    };
});
```

With this configuration, tokens served from L1 have sub-millisecond latency. Tokens not in L1 fall back to the L2 distributed cache.

**Step 2: Optimize the distributed cache tier**

If L2 cache latency is high, consider the following actions:

- **Scale up the Redis instance.** Move to a higher tier \(for example, from Basic to Standard or Premium in Azure Cache for Redis\) to get more throughput and lower latency.
- **Enable geo-replication.** If your application serves users in multiple regions, use Azure Cache for Redis geo-replication so that the cache is close to each region's compute.
- **Review network configuration.** Use Private Link or VNet integration to reduce network hops between the application and the cache.

**Step 3: Reduce serialized token size**

If token cache entries are large, review whether the application requests tokens for more resources than necessary. Each unique resource and scope combination adds to the cache entry size. Consolidate API calls where possible to reduce the number of distinct access tokens cached per user.

## Redis cache eviction

### Symptom

Users are intermittently prompted to reauthenticate with no pattern based on token expiration. Redis monitoring shows `evicted_keys` increasing and `used_memory` approaching the `maxmemory` limit.

### Cause

When Redis reaches its `maxmemory` limit, it evicts keys based on the configured `maxmemory-policy`. The default policy \(`volatile-lru`\) evicts the least recently used keys that have an expiration. If the Redis instance is shared with other application data, token cache entries compete for space and can be evicted prematurely.

### Solution

**Step 1: Check the eviction policy**

Check the current eviction policy:

```bash
redis-cli CONFIG GET maxmemory-policy
```

For token caches, `volatile-lru` \(the default\) is appropriate because token cache entries have expirations. However, if other data without expirations consumes memory, token entries are evicted first.

**Step 2: Use a dedicated Redis instance**

Isolate the token cache from other application data by using a dedicated Redis instance:

```json
{
  "ConnectionStrings": {
    "RedisTokenCache": "token-cache-redis.redis.cache.windows.net:6380,password=...,ssl=True,abortConnect=False",
    "RedisAppData": "app-data-redis.redis.cache.windows.net:6380,password=...,ssl=True,abortConnect=False"
  }
}
```

```csharp
// Register the token cache Redis instance specifically for distributed caching.
services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = Configuration.GetConnectionString("RedisTokenCache");
});
```

**Step 3: Increase the Redis memory limit**

If a dedicated instance isn't feasible, increase the `maxmemory` setting. In Azure Cache for Redis, scale up to a higher tier or increase the cache size.

**Step 4: Set appropriate cache entry expirations**

Set reasonable expirations so stale entries are removed before memory runs out:

```csharp
services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.AbsoluteExpirationRelativeToNow = TimeSpan.FromHours(12);
    options.SlidingExpiration = TimeSpan.FromHours(2);
});
```

## SQL distributed cache table growth

### Symptom

The SQL distributed cache table grows continuously, consuming disk space. Database queries against the cache table slow over time, and you might see warnings about table size or storage limits.

### Cause

The SQL Server distributed cache \(`Microsoft.Extensions.Caching.SqlServer`\) doesn't automatically remove expired entries. Expired entries remain until explicitly purged, causing unbounded table growth, degraded query performance, and storage consumption.

### Solution

**Step 1: Set up a recurring cleanup job**

Create a SQL Server Agent job or scheduled task to periodically remove expired entries:

```sql
-- Delete expired entries from the SQL distributed cache table.
-- Schedule this query to run every 30 minutes.
DELETE FROM [dbo].[TokenCache]
WHERE ExpiresAtTime < GETUTCDATE();
```

Tip

In Azure SQL Database, where SQL Server Agent isn't available, use Azure Automation, Azure Functions with a timer trigger, or Elastic Jobs to schedule the cleanup.

**Step 2: Add an index for efficient cleanup**

If the cache table doesn't already have an index on the expiration column, add one to speed up the delete operation:

```sql
CREATE NONCLUSTERED INDEX IX_TokenCache_ExpiresAtTime
ON [dbo].[TokenCache] (ExpiresAtTime);
```

**Step 3: Monitor table size**

Add monitoring to track the row count and table size over time:

```sql
SELECT
    COUNT(*) AS TotalEntries,
    COUNT(CASE WHEN ExpiresAtTime < GETUTCDATE() THEN 1 END) AS ExpiredEntries,
    COUNT(CASE WHEN ExpiresAtTime >= GETUTCDATE() THEN 1 END) AS ActiveEntries
FROM [dbo].[TokenCache];
```

**Step 4: Consider switching to Redis**

If managing SQL cache cleanup is burdensome, switch to Redis, which handles expiration automatically through its built-in TTL mechanism:

```csharp
// Replace SQL distributed cache with Redis.
services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = Configuration.GetConnectionString("Redis");
});
```

## General troubleshooting tips

Use these tips when your issue doesn't match a specific scenario in this article.

### Verify the cache is being used

Add temporary logging to confirm tokens are read from and written to the cache:

```csharp
services.Configure<MsalDistributedTokenCacheAdapterOptions>(options =>
{
    options.Encrypt = false; // Disable encryption temporarily for debugging only.
    options.OnL2CacheFailure = (ex) =>
    {
        logger.LogError(ex, "L2 cache operation failed.");
        return true;
    };
});
```

### Check for multiple cache registrations

If multiple calls to `AddInMemoryTokenCaches()` or `AddDistributedTokenCaches()` exist in your startup code, the last registration wins. Verify that only one cache type is registered.

### Review the token lifetime

Access tokens have a finite lifetime \(typically 60–90 minutes\). If users report reauthenticating after this period, the behavior is expected rather than a cache problem. Refresh tokens obtain new access tokens silently and are stored in the cache. If the refresh token is missing or expired, the user must reauthenticate.

### Test with a clean cache

When diagnosing issues, clear the cache to rule out corrupted or stale entries:

- **In-memory cache:** Restart the application.
- **Redis:** Run `FLUSHDB` on the cache database.
- **SQL Server:** Delete all rows from the cache table.

## Token cache empty after application restart

### Symptom

Users must reauthenticate after every application restart or redeployment. The distributed cache appears empty or tokens aren't persisted.

### Cause

This issue typically occurs when you use an in-memory cache \(`AddInMemoryTokenCaches()`\) or the non-persistent distributed memory cache \(`AddDistributedMemoryCache()`\) in production. Neither option persists tokens across application restarts.

`AddDistributedMemoryCache()` registers an `IDistributedCache` implementation that stores data in memory. Despite the "distributed" name, it doesn't persist data externally and is intended only for development and testing.

### Solution

Switch to a persistent distributed cache:

```csharp
// Register a persistent cache (Redis example).
builder.Services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = builder.Configuration.GetConnectionString("Redis");
    options.InstanceName = "MyApp_";
});

// Use distributed token caches instead of in-memory.
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDistributedTokenCaches();
```

Warning

Don't confuse `AddDistributedMemoryCache()` with a persistent distributed cache. Use `AddStackExchangeRedisCache()` \(Redis\), `AddDistributedSqlServerCache()` \(SQL Server\), or another persistent `IDistributedCache` implementation for production workloads.

## Related content

- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
