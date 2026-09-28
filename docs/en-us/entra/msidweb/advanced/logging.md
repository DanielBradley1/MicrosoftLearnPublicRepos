<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Configure logging in Microsoft.Identity.Web

Microsoft.Identity.Web integrates with ASP.NET Core's logging infrastructure. Use it to diagnose issues across:

- **Authentication flows** - Sign-in, sign-out, token validation
- **Token acquisition** - Token cache hits/misses, MSAL operations
- **Downstream API calls** - HTTP requests, token acquisition for APIs
- **Error conditions** - Exceptions, validation failures

## Understand logged components

| Component | Log Source | Purpose |
| --- | --- | --- |
| **Microsoft.Identity.Web** | Core authentication logic | Configuration, token acquisition, API calls |
| **MSAL.NET** | `Microsoft.Identity.Client` | Token cache operations, authority validation |
| **IdentityModel** | Token validation | JWT parsing, signature validation, claims extraction |
| **ASP.NET Core Auth** | `Microsoft.AspNetCore.Authentication` | Cookie operations, challenge/forbid actions |

---

## Get started with logging

### Minimal configuration

Add the following log-level entries to `appsettings.json` to enable identity logging:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.Identity": "Information"
    }
  }
}
```

This enables **Information-level** logging for Microsoft.Identity.Web and its dependencies \(MSAL.NET, IdentityModel\).

### Development configuration

For detailed diagnostics during development:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Identity": "Debug",
      "Microsoft.AspNetCore.Authentication": "Information"
    }
  },
  "AzureAd": {
    "EnablePiiLogging": true  // Development only!
  }
}
```

### Production configuration

For production, minimize log volume while capturing errors:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning",
      "Microsoft": "Warning",
      "Microsoft.Identity": "Warning"
    }
  },
  "AzureAd": {
    "EnablePiiLogging": false  // Never true in production
  }
}
```

---

## Configure log filtering

### Namespace-based filtering

Control log verbosity by namespace. The following configuration sets granular levels for each identity-related namespace:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",

      // General Microsoft namespaces
      "Microsoft": "Warning",
      "Microsoft.AspNetCore": "Warning",

      // Identity-specific namespaces
      "Microsoft.Identity": "Information",
      "Microsoft.Identity.Web": "Information",
      "Microsoft.Identity.Client": "Information",

      // ASP.NET Core authentication
      "Microsoft.AspNetCore.Authentication": "Information",
      "Microsoft.AspNetCore.Authentication.JwtBearer": "Information",
      "Microsoft.AspNetCore.Authentication.OpenIdConnect": "Debug",

      // Token validation
      "Microsoft.IdentityModel": "Warning"
    }
  }
}
```

### Disable specific logging

To silence noisy components without affecting others, set their log level to `None` or `Warning`:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.Identity.Web": "None",  // Completely disable
      "Microsoft.Identity.Client": "Warning"  // Only errors/warnings
    }
  }
}
```

### Environment-specific configuration

Use `appsettings.{Environment}.json` for per-environment settings:

**appsettings.Development.json:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity": "Debug"
    }
  },
  "AzureAd": {
    "EnablePiiLogging": true
  }
}
```

**appsettings.Production.json:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity": "Warning"
    }
  },
  "AzureAd": {
    "EnablePiiLogging": false
  }
}
```

---

## Understand log levels

ASP.NET Core defines the following log levels. Choose the level that balances diagnostic detail against log volume for your environment.

### ASP.NET Core log levels

| Level | Usage | Volume | Production? |
| --- | --- | --- | --- |
| **Trace** | Most detailed, every operation | Very High | No |
| **Debug** | Detailed flow, useful for dev | High | No |
| **Information** | General flow, key events | Moderate | Selective |
| **Warning** | Unexpected but handled conditions | Low | Yes |
| **Error** | Errors and exceptions | Very Low | Yes |
| **Critical** | Unrecoverable failures | Very Low | Yes |
| **None** | Disable logging | None | Selective |

### Map MSAL.NET to ASP.NET Core levels

| MSAL.NET Level | ASP.NET Core Equivalent | Description |
| --- | --- | --- |
| `Verbose` | `Debug` or `Trace` | Most detailed messages |
| `Info` | `Information` | Key authentication events |
| `Warning` | `Warning` | Abnormal but handled conditions |
| `Error` | `Error` or `Critical` | Errors and exceptions |

### Apply recommended settings by environment

Use the following configurations per environment.

**Development:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity": "Debug",
      "Microsoft.Identity.Client": "Information"
    }
  }
}
```

**Staging:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity": "Information",
      "Microsoft.Identity.Client": "Warning"
    }
  }
}
```

**Production:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity": "Warning",
      "Microsoft.Identity.Client": "Error"
    }
  }
}
```

---

## Configure PII logging

By default, Microsoft.Identity.Web redacts personally identifiable information \(PII\) from logs. Enable PII logging only in development environments to see full user details.

### What is PII?

**Personally Identifiable Information \(PII\)** includes:

- Usernames, email addresses
- Display names
- Object IDs, tenant IDs
- IP addresses
- Token values, claims

### Security warning

> **WARNING**: You and your application are responsible for complying with all applicable regulatory requirements including those set forth by [GDPR](https://www.microsoft.com/trust-center/privacy/gdpr-overview). Before enabling PII logging, ensure you can safely handle this potentially highly sensitive data.

### Enable PII logging \(development only\)

Set `EnablePiiLogging` to `true` in your development configuration file:

**appsettings.Development.json:**

```json
{
  "AzureAd": {
    "EnablePiiLogging": true  //  Development/Testing ONLY
  },
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity": "Debug"
    }
  }
}
```

### Control PII logging programmatically

Toggle PII logging based on the hosting environment:

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.Configure<MicrosoftIdentityOptions>(options =>
{
    // Only enable PII in Development
    options.EnablePiiLogging = builder.Environment.IsDevelopment();
});
```

### What changes with PII enabled?

**Without PII logging:**

```
[Information] Token validation succeeded for user '{hidden}'
[Information] Acquired token from cache for scopes '{hidden}'
```

**With PII enabled:**

```
[Information] Token validation succeeded for user 'john.doe@contoso.com'
[Information] Acquired token from cache for scopes 'user.read api://my-api/.default'
```

### PII redaction in logs

When PII logging is disabled, sensitive data is replaced with:

- `{hidden}` - Hides user identifiers
- `{hash:XXXX}` - Shows hash instead of actual value
- `***` - Obscures tokens

---

## Use correlation IDs

Correlation IDs trace authentication requests across services. Include them in logs and support tickets to speed up issue resolution.

### What are correlation IDs?

A correlation ID is a **GUID** that uniquely identifies an authentication or token acquisition request across:

- Your application
- Microsoft Identity platform
- MSAL.NET library
- Microsoft backend services

### Obtain correlation IDs

**Method 1: From AuthenticationResult**

Extract the correlation ID from `AuthenticationResult` after a successful token acquisition:

```csharp
using Microsoft.Identity.Web;

public class TodoController : ControllerBase
{
    private readonly ITokenAcquisition _tokenAcquisition;
    private readonly ILogger<TodoController> _logger;

    public TodoController(
        ITokenAcquisition tokenAcquisition,
        ILogger<TodoController> logger)
    {
        _tokenAcquisition = tokenAcquisition;
        _logger = logger;
    }

    [HttpGet]
    public async Task<IActionResult> GetTodos()
    {
        var result = await _tokenAcquisition.GetAuthenticationResultForUserAsync(
            new[] { "user.read" });

        _logger.LogInformation(
            "Token acquired. CorrelationId: {CorrelationId}, Source: {TokenSource}",
            result.CorrelationId,
            result.AuthenticationResultMetadata.TokenSource);

        return Ok(result.CorrelationId);
    }
}
```

**Method 2: From MsalServiceException**

Capture the correlation ID from `MsalServiceException` when token acquisition fails:

```csharp
using Microsoft.Identity.Client;

try
{
    var token = await _tokenAcquisition.GetAccessTokenForUserAsync(
        new[] { "user.read" });
}
catch (MsalServiceException ex)
{
    _logger.LogError(ex,
        "Token acquisition failed. CorrelationId: {CorrelationId}, ErrorCode: {ErrorCode}",
        ex.CorrelationId,
        ex.ErrorCode);

    // Return correlation ID to user for support
    return StatusCode(500, new {
        error = "authentication_failed",
        correlationId = ex.CorrelationId
    });
}
```

**Method 3: Set a custom correlation ID**

Assign a custom correlation ID to link application traces with Microsoft Entra ID requests:

```csharp
[HttpGet("{id}")]
public async Task<IActionResult> GetTodo(int id)
{
    // Use request trace ID as correlation ID
    var correlationId = Activity.Current?.Id ?? HttpContext.TraceIdentifier;

    var todo = await _downstreamApi.GetForUserAsync<Todo>(
        "TodoListService",
        options =>
        {
            options.RelativePath = $"api/todolist/{id}";
            options.TokenAcquisitionOptions = new TokenAcquisitionOptions
            {
                CorrelationId = Guid.Parse(correlationId)
            };
        });

    _logger.LogInformation(
        "Called downstream API. TraceId: {TraceId}, CorrelationId: {CorrelationId}",
        HttpContext.TraceIdentifier,
        correlationId);

    return Ok(todo);
}
```

### Provide correlation IDs for support

When you contact Microsoft support, provide the following details:

1. **Correlation ID** - From logs or exception
2. **Timestamp** - When the error occurred \(UTC\)
3. **Tenant ID** - Your Microsoft Entra ID tenant
4. **Error code** - If applicable \(e.g., `AADSTS50058`\)

**Example support request:**

```
Subject: Token acquisition failing for user.read scope

Correlation ID: 12345678-1234-1234-1234-123456789012
Timestamp: 2025-01-15 14:32:45 UTC
Tenant ID: contoso.onmicrosoft.com
Error Code: AADSTS50058
```

---

## Enable token cache logging

Token cache logging helps you understand cache hit/miss behavior and diagnose performance issues with distributed caches.

### Enable token cache diagnostics

For .NET Framework or .NET Core apps using distributed token caches, configure detailed logging:

```csharp
using Microsoft.Extensions.Logging;
using Microsoft.Identity.Web.TokenCacheProviders;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddDistributedTokenCaches();

// Enable detailed token cache logging
builder.Services.AddLogging(configure =>
{
    configure.AddConsole();
    configure.AddDebug();
})
.Configure<LoggerFilterOptions>(options =>
{
    options.MinLevel = LogLevel.Debug;  // Detailed cache operations
});
```

### Token cache log examples

**Cache hit:**

```
[Debug] Token cache: Token found in cache for scopes 'user.read'
[Information] Token source: Cache
```

**Cache miss:**

```
[Debug] Token cache: No token found in cache for scopes 'user.read'
[Information] Token source: IdentityProvider
[Debug] Token cache: Token stored in cache
```

### Troubleshoot distributed caches

Enable provider-specific logging to diagnose cache connectivity and performance issues.

**Redis cache:**

```csharp
builder.Services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = builder.Configuration["Redis:ConnectionString"];
});

// Enable Redis logging
builder.Services.AddLogging(configure =>
{
    configure.AddFilter("Microsoft.Extensions.Caching", LogLevel.Debug);
});
```

**SQL Server cache:**

Configure SQL Server distributed cache with logging:

```csharp
builder.Services.AddDistributedSqlServerCache(options =>
{
    options.ConnectionString = builder.Configuration["SqlCache:ConnectionString"];
    options.SchemaName = "dbo";
    options.TableName = "TokenCache";
});

// Enable SQL cache logging
builder.Services.AddLogging(configure =>
{
    configure.AddFilter("Microsoft.Extensions.Caching.SqlServer", LogLevel.Information);
});
```

---

## Troubleshoot common issues

Use the following scenarios to diagnose frequent authentication and authorization problems.

### Common logging scenarios

#### Scenario 1: Token validation failures

**Symptom:** 401 Unauthorized responses

**Enable detailed logging:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.AspNetCore.Authentication.JwtBearer": "Debug",
      "Microsoft.IdentityModel": "Information"
    }
  }
}
```

**Look for:**

```
[Information] Microsoft.AspNetCore.Authentication.JwtBearer.JwtBearerHandler:
  Failed to validate the token.
[Debug] Microsoft.IdentityModel.Tokens: IDX10230: Lifetime validation failed.
  The token is expired.
```

#### Scenario 2: Token acquisition failures

**Symptom:** `MsalServiceException` or `MsalUiRequiredException`

**Enable detailed logging:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity.Web": "Debug",
      "Microsoft.Identity.Client": "Information"
    }
  }
}
```

**Look for:**

```
[Error] Microsoft.Identity.Web: Token acquisition failed.
  ErrorCode: invalid_grant, CorrelationId: {guid}
[Information] Microsoft.Identity.Client: MSAL returned exception:
  AADSTS50058: Silent sign-in failed.
```

#### Scenario 3: Downstream API call failures

**Symptom:** HTTP 502 or timeout errors calling downstream APIs

**Enable detailed logging:**

```json
{
  "Logging": {
    "LogLevel": {
      "Microsoft.Identity.Abstractions": "Debug",
      "System.Net.Http": "Information"
    }
  }
}
```

Add custom logging in your controller to capture downstream API errors:

```csharp
[HttpGet]
public async Task<IActionResult> GetUserProfile()
{
    try
    {
        _logger.LogInformation("Acquiring token for Microsoft Graph");

        var user = await _downstreamApi.GetForUserAsync<User>(
            "MicrosoftGraph",
            options => options.RelativePath = "me");

        _logger.LogInformation(
            "Successfully retrieved user profile for {UserPrincipalName}",
            user.UserPrincipalName);

        return Ok(user);
    }
    catch (MsalUiRequiredException ex)
    {
        _logger.LogWarning(ex,
            "User interaction required. CorrelationId: {CorrelationId}",
            ex.CorrelationId);
        return Challenge();
    }
    catch (HttpRequestException ex)
    {
        _logger.LogError(ex, "Failed to call Microsoft Graph API");
        return StatusCode(502, "Downstream API error");
    }
}
```

### Interpret log patterns

The following examples show typical log output for common authentication events.

**Successful authentication flow:**

```
[Info] Authentication scheme OpenIdConnect: Authorization response received
[Debug] Correlation id: {guid}
[Info] Authorization code received
[Info] Token validated successfully
[Info] Authentication succeeded for user: {user}
```

**Consent required:**

```
[Warning] Microsoft.Identity.Web: Incremental consent required
[Info] AADSTS65001: User consent is required for scopes: {scopes}
[Info] Redirecting to consent page
```

**Token refresh:**

```
[Debug] Token expired, attempting silent token refresh
[Info] Token source: IdentityProvider
[Info] Token refreshed successfully
```

### Aggregate logs with external providers

Forward identity logs to a centralized logging platform for monitoring and alerting.

**Application Insights integration:**

Send identity telemetry to Application Insights with correlation ID enrichment:

```csharp
using Microsoft.ApplicationInsights.Extensibility;

builder.Services.AddApplicationInsightsTelemetry();

// Enrich telemetry with correlation IDs
builder.Services.AddSingleton<ITelemetryInitializer, CorrelationIdTelemetryInitializer>();
```

**Serilog integration:**

Configure Serilog to capture identity logs to console and rolling file outputs:

```csharp
using Serilog;

Log.Logger = new LoggerConfiguration()
    .MinimumLevel.Information()
    .MinimumLevel.Override("Microsoft.Identity", Serilog.Events.LogEventLevel.Debug)
    .Enrich.FromLogContext()
    .WriteTo.Console()
    .WriteTo.File("logs/identity-.txt", rollingInterval: RollingInterval.Day)
    .CreateLogger();

builder.Host.UseSerilog();
```

---

## Follow logging best practices

Apply these practices to keep your identity logs secure, useful, and performant.

### Do's

**1. Use structured logging:**

Pass values as named parameters so log aggregators can index and query them:

```csharp
_logger.LogInformation(
    "Token acquired for user {UserId} with scopes {Scopes}",
    userId, string.Join(" ", scopes));
```

**2. Log correlation IDs:**

Always include the correlation ID in error logs to simplify support investigations:

```csharp
_logger.LogError(ex,
    "Operation failed. CorrelationId: {CorrelationId}",
    ex.CorrelationId);
```

**3. Use appropriate log levels:**

Match the log level to the severity and audience:

```csharp
_logger.LogDebug("Detailed diagnostic info");      // Development
_logger.LogInformation("Key application events");  // Selective production
_logger.LogWarning("Unexpected but handled");      // Production
_logger.LogError(ex, "Operation failed");          // Production
```

**4. Sanitize logs in production:**

Mask sensitive values before writing them to production logs:

```csharp
var sanitizedEmail = environment.IsProduction()
    ? MaskEmail(email)
    : email;
_logger.LogInformation("Processing request for {Email}", sanitizedEmail);
```

### Don'ts

**1. Don't enable PII in production:**

```csharp
//  Wrong
"EnablePiiLogging": true  // In production config!

//  Correct
"EnablePiiLogging": false
```

**2. Don't log secrets:**

```csharp
//  Wrong
_logger.LogInformation("Token: {Token}", accessToken);

//  Correct
_logger.LogInformation("Token acquired, expires: {ExpiresOn}", expiresOn);
```

**3. Don't use verbose logging in production:**

```csharp
//  Wrong - production appsettings.json
"Microsoft.Identity": "Debug"

//  Correct
"Microsoft.Identity": "Warning"
```

## Related content

- [Customizing Authentication](https://learn.microsoft.com/en-us/entra/msidweb/advanced/customization)
- [Token cache troubleshooting](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-troubleshooting)
- [Calling downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)
- [Authorization](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)
