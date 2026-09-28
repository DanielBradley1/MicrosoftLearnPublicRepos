<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/advanced/api-gateways -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Deploy protected APIs behind gateways

Deploy ASP.NET Core web APIs protected with Microsoft.Identity.Web behind Azure API gateways and reverse proxies, including Azure API Management \(APIM\), Azure Front Door, and Azure Application Gateway.

## Understand gateway requirements

When you deploy protected APIs behind gateways, you must handle several concerns:

- **Forwarded headers** - Preserve original request context \(scheme, host, IP\)
- **Token validation** - Ensure audience claims match gateway URLs
- **CORS configuration** - Handle cross-origin requests correctly
- **Health endpoints** - Provide unauthenticated health checks
- **Path-based routing** - Support gateway-level path prefixes
- **SSL/TLS termination** - Handle HTTPS properly when gateway terminates SSL

## Review common gateway scenarios

Choose a gateway based on your requirements. The following sections describe the most common Azure gateway services for protected APIs.

### Azure API Management \(APIM\)

**Use case:** Enterprise API gateway with policies, rate limiting, transformation

**Architecture:**

```
Client → Microsoft Entra ID → Token
Client → APIM (apim.azure-api.net) → Backend API (app.azurewebsites.net)
```

**Key considerations:**

- APIM policies can validate JWT tokens before forwarding to the backend
- The backend API still validates tokens
- The audience claim must match the APIM URL or backend URL \(configure accordingly\)

### Azure Front Door

**Use case:** Global load balancing, CDN, DDoS protection

**Architecture:**

```
Client → Microsoft Entra ID → Token
Client → Front Door (azurefd.net) → Backend API (regional endpoints)
```

**Key considerations:**

- Front Door forwards requests with `X-Forwarded-*` headers
- SSL/TLS termination at Front Door
- Token audience validation needs configuration

### Azure Application Gateway

**Use case:** Regional load balancing, WAF, path-based routing

**Architecture:**

```
Client → Microsoft Entra ID → Token
Client → Application Gateway → Backend API (multiple instances)
```

**Key considerations:**

- Web Application Firewall \(WAF\) integration
- Path-based routing rules
- Backend health probes need unauthenticated endpoints

---

## Configure common patterns

Apply these configuration patterns to ensure your protected API works correctly behind any gateway.

### 1. Forwarded headers middleware

Always configure forwarded headers middleware when behind a gateway. The following code registers the middleware and sets it to run before authentication:

```csharp
using Microsoft.AspNetCore.HttpOverrides;

var builder = WebApplication.CreateBuilder(args);

// Configure forwarded headers BEFORE authentication
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;

    // Clear known networks/proxies to accept forwarded headers from any source
    // (Azure infrastructure will be the proxy)
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();

    // Limit to specific headers if needed
    options.ForwardedForHeaderName = "X-Forwarded-For";
    options.ForwardedProtoHeaderName = "X-Forwarded-Proto";
    options.ForwardedHostHeaderName = "X-Forwarded-Host";
});

// Add authentication
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

var app = builder.Build();

// USE forwarded headers BEFORE authentication middleware
app.UseForwardedHeaders();
app.UseAuthentication();
app.UseAuthorization();

app.Run();
```

Forwarded headers middleware is critical because it:

- Preserves the original client IP address for logging
- Ensures `HttpContext.Request.Scheme` reflects the original HTTPS scheme
- Provides the correct `Host` header for redirect URLs and token validation

### 2. Token audience configuration

#### Option A: Accept both gateway and backend URLs

Add multiple valid audiences in your `appsettings.json` configuration:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "Audience": "api://your-client-id",
    "TokenValidationParameters": {
      "ValidAudiences": [
        "api://your-client-id",
        "https://your-backend.azurewebsites.net",
        "https://your-apim.azure-api.net"
      ]
    }
  }
}
```

Alternatively, configure multiple audiences programmatically in `Program.cs`:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.Identity.Web;

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();

// Customize token validation to accept multiple audiences
builder.Services.Configure<JwtBearerOptions>(JwtBearerDefaults.AuthenticationScheme, options =>
{
    var existingValidation = options.TokenValidationParameters.AudienceValidator;

    options.TokenValidationParameters.AudienceValidator = (audiences, token, parameters) =>
    {
        var validAudiences = new[]
        {
            "api://your-client-id",
            "https://your-backend.azurewebsites.net",
            "https://your-apim.azure-api.net",
            builder.Configuration["AzureAd:ClientId"] // Also accept ClientId
        };

        return audiences.Any(a => validAudiences.Contains(a, StringComparer.OrdinalIgnoreCase));
    };
});
```

#### Option B: Rewrite audience in APIM policy

Configure APIM to validate the audience claim before forwarding to the backend:

```xml
<policies>
    <inbound>
        <validate-jwt header-name="Authorization" failed-validation-httpcode="401">
            <openid-config url="https://login.microsoftonline.com/{tenant-id}/v2.0/.well-known/openid-configuration" />
            <audiences>
                <audience>api://your-client-id</audience>
            </audiences>
        </validate-jwt>

        <!-- Optionally modify token claims for backend -->
        <set-header name="X-Gateway-Validated" exists-action="override">
            <value>true</value>
        </set-header>
    </inbound>
</policies>
```

### 3. Health endpoint configuration

Gateways require unauthenticated health endpoints for probes. Map a health endpoint before the authentication middleware to bypass token validation:

```csharp
var app = builder.Build();

// Health endpoint BEFORE authentication middleware
app.MapGet("/health", () => Results.Ok(new { status = "healthy" }))
    .AllowAnonymous();

app.UseForwardedHeaders();
app.UseAuthentication();
app.UseAuthorization();

// Protected endpoints require authentication
app.MapControllers();

app.Run();
```

Alternatively, use the built-in ASP.NET Core Health Checks framework for richer health reporting:

```csharp
using Microsoft.Extensions.Diagnostics.HealthChecks;

builder.Services.AddHealthChecks()
    .AddCheck("api", () => HealthCheckResult.Healthy());

var app = builder.Build();

app.MapHealthChecks("/health").AllowAnonymous();
app.MapHealthChecks("/ready").AllowAnonymous();

app.UseForwardedHeaders();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();

app.Run();
```

### 4. CORS configuration behind gateways

When you use Azure Front Door or APIM with frontend applications, configure CORS to allow requests from your gateway origins:

```csharp
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowGateway", policy =>
    {
        policy.WithOrigins(
            "https://your-apim.azure-api.net",
            "https://your-frontend.azurefd.net",
            "https://your-app.azurewebsites.net"
        )
        .AllowAnyMethod()
        .AllowAnyHeader()
        .AllowCredentials(); // If using cookies
    });
});

var app = builder.Build();

app.UseForwardedHeaders();
app.UseCors("AllowGateway");
app.UseAuthentication();
app.UseAuthorization();

app.Run();
```

Important

CORS must be configured **after** forwarded headers and **before** authentication.

---

## Integrate with Azure API Management

This section provides the complete configuration for deploying a protected API behind Azure API Management.

### Configure the backend API

Set up forwarded headers and Microsoft Entra ID authentication in `Program.cs`:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.AspNetCore.HttpOverrides;
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// Forwarded headers for APIM
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.All;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

// Authentication
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddControllers();

var app = builder.Build();

// Middleware order matters
app.UseForwardedHeaders();
app.UseHttpsRedirection();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();

app.Run();
```

Add the Microsoft Entra configuration to `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-backend-api-client-id",
    "Audience": "api://your-backend-api-client-id"
  }
}
```

### Add APIM inbound policy for JWT validation

Define an inbound policy that validates the JWT token, applies rate limiting, and forwards the request to the backend:

```xml
<policies>
    <inbound>
        <base />

        <!-- Validate JWT token -->
        <validate-jwt header-name="Authorization" failed-validation-httpcode="401" failed-validation-error-message="Unauthorized">
            <openid-config url="https://login.microsoftonline.com/{your-tenant-id}/v2.0/.well-known/openid-configuration" />
            <audiences>
                <audience>api://your-backend-api-client-id</audience>
            </audiences>
            <issuers>
                <issuer>https://login.microsoftonline.com/{your-tenant-id}/v2.0</issuer>
            </issuers>
            <required-claims>
                <claim name="scp" match="any">
                    <value>access_as_user</value>
                </claim>
            </required-claims>
        </validate-jwt>

        <!-- Rate limiting -->
        <rate-limit calls="100" renewal-period="60" />

        <!-- Forward original host header -->
        <set-header name="X-Forwarded-Host" exists-action="override">
            <value>@(context.Request.OriginalUrl.Host)</value>
        </set-header>

        <!-- Forward to backend -->
        <set-backend-service base-url="https://your-backend.azurewebsites.net" />
    </inbound>

    <backend>
        <base />
    </backend>

    <outbound>
        <base />
    </outbound>

    <on-error>
        <base />
    </on-error>
</policies>
```

### Configure APIM API settings

Use the following named values and API settings to complete the APIM configuration:

**Named Values \(for reusability\):**

- `tenant-id`: Your Microsoft Entra tenant ID
- `backend-api-client-id`: Backend API's client ID
- `backend-base-url`: `https://your-backend.azurewebsites.net`

**API Settings:**

- **API URL suffix**: `/api` \(optional path prefix\)
- **Web service URL**: Set via policy using named values
- **Subscription required**: Yes \(adds another layer of security\)

### Configure the client application

Client apps request tokens for the **backend API**, not APIM. The following code acquires a token and calls the API through the APIM endpoint:

```csharp
// Client app requests token
var result = await app.AcquireTokenSilent(
    scopes: new[] { "api://your-backend-api-client-id/access_as_user" },
    account)
    .ExecuteAsync();

// Call APIM URL with token
var client = new HttpClient();
client.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", result.AccessToken);

// Add APIM subscription key
client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", "your-subscription-key");

var response = await client.GetAsync("https://your-apim.azure-api.net/api/weatherforecast");
```

---

## Integrate with Azure Front Door

Configure your protected API for global distribution behind Azure Front Door.

### Configure the backend API

Set up forwarded headers for Azure Front Door in `Program.cs`:

```csharp
using Microsoft.AspNetCore.HttpOverrides;

var builder = WebApplication.CreateBuilder(args);

// Configure for Azure Front Door
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;

    // Accept headers from any source (Azure Front Door)
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();

    // Front Door specific headers
    options.ForwardedForHeaderName = "X-Forwarded-For";
    options.ForwardedProtoHeaderName = "X-Forwarded-Proto";
});

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

var app = builder.Build();

app.UseForwardedHeaders();
app.UseAuthentication();
app.UseAuthorization();

app.MapControllers();

app.Run();
```

### Configure Front Door origins

Complete the following steps in the Azure portal to set up the Front Door origin:

1. Create Front Door profile
2. Add origin group with your backend API instances
3. Configure health probes to `/health` endpoint
4. Set HTTPS only forwarding
5. Enable WAF policy \(optional\)

**Health Probe Settings:**

- **Path**: `/health`
- **Protocol**: HTTPS
- **Method**: GET
- **Interval**: 30 seconds

### Handle multiple regions

When you deploy to multiple regions behind Front Door, add region awareness for logging and diagnostics:

```csharp
// Add region awareness for logging/diagnostics
builder.Services.AddSingleton<IHttpContextAccessor, HttpContextAccessor>();

app.Use(async (context, next) =>
{
    // Log the actual client IP and region
    var clientIp = context.Connection.RemoteIpAddress?.ToString();
    var forwardedFor = context.Request.Headers["X-Forwarded-For"].ToString();
    var frontDoorId = context.Request.Headers["X-Azure-FDID"].ToString();

    // Add to logger scope or response headers
    context.Response.Headers.Add("X-Served-By-Region",
        builder.Configuration["Region"] ?? "unknown");

    await next();
});
```

### Validate tokens with Front Door

If clients request tokens scoped to the Front Door URL, add it to the valid audiences list:

```csharp
builder.Services.Configure<JwtBearerOptions>(JwtBearerDefaults.AuthenticationScheme, options =>
{
    options.TokenValidationParameters.ValidAudiences = new[]
    {
        "api://your-backend-api-client-id",
        "https://your-frontend.azurefd.net", // Front Door URL
        builder.Configuration["AzureAd:ClientId"]
    };
});
```

---

## Integrate with Azure Application Gateway

Configure your protected API behind Azure Application Gateway with Web Application Firewall \(WAF\) support.

### Configure the backend API

Set up forwarded headers for Application Gateway in `Program.cs`:

```csharp
using Microsoft.AspNetCore.HttpOverrides;

var builder = WebApplication.CreateBuilder(args);

// Application Gateway uses standard forwarded headers
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddHealthChecks();

var app = builder.Build();

// Health endpoint for Application Gateway probes
app.MapHealthChecks("/health").AllowAnonymous();

app.UseForwardedHeaders();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();

app.Run();
```

### Configure Application Gateway settings

Set the following backend, health probe, and WAF settings in the Azure portal:

**Backend Settings:**

- **Protocol**: HTTPS \(recommended\) or HTTP
- **Port**: 443 or 80
- **Override backend path**: No \(unless needed\)
- **Custom probe**: Yes, pointing to `/health`

**Health Probe:**

- **Protocol**: HTTPS or HTTP
- **Host**: Leave default or specify
- **Path**: `/health`
- **Interval**: 30 seconds
- **Unhealthy threshold**: 3

**WAF Policy:**

- Enable WAF with OWASP 3.2 ruleset
- **Important**: Ensure JWT tokens in `Authorization` headers aren't blocked
- You might need to create WAF exclusions for `RequestHeaderNames` containing "Authorization"

### Set up path-based routing

When you use path-based routing rules, configure your backend API to handle the path prefix:

```csharp
// Backend API should work regardless of path prefix
var app = builder.Build();

// Option 1: Use path base (if gateway adds prefix)
app.UsePathBase("/api/v1");

// Option 2: Configure routing explicitly
app.UseForwardedHeaders();
app.UseAuthentication();
app.UseAuthorization();

app.MapControllers();

app.Run();
```

**Application Gateway Rule:**

- **Path**: `/api/v1/*`
- **Backend target**: Your backend pool
- **Backend settings**: Use configured settings

---

## Troubleshoot common issues

Use these solutions to resolve the most common problems when deploying protected APIs behind gateways.

### Problem: 401 Unauthorized after deployment behind gateway

**Symptoms:**

- API works locally but returns 401 behind gateway
- Token seems valid when decoded at jwt.ms

**Possible causes:**

1. **Audience claim mismatch**

   ```bash
   # Check token audience
   # Decode token and verify 'aud' claim matches one of:
   # - api://your-client-id
   # - https://your-backend.azurewebsites.net
   # - https://your-gateway-url
   ```

2. **Missing forwarded headers middleware**

   ```csharp
   // Ensure this is BEFORE authentication
   app.UseForwardedHeaders();
   app.UseAuthentication();
   ```

3. **HTTPS redirection issues**

   ```csharp
   // If gateway terminates SSL, may need to disable or configure carefully
   if (!app.Environment.IsDevelopment())
   {
       app.UseHttpsRedirection();
   }
   ```

**Solution:**

- Enable debug logging to see token validation details
- Add multiple valid audiences in token validation
- Verify that `X-Forwarded-*` headers are forwarded by the gateway

### Problem: Health probes failing

**Symptoms:**

- Gateway marks the backend as unhealthy
- Health endpoint returns 401

**Solution:**

Ensure the health endpoint runs before authentication middleware:

```csharp
// Ensure health endpoint is BEFORE authentication
app.MapHealthChecks("/health").AllowAnonymous();

// Alternative: Use custom middleware
app.Map("/health", healthApp =>
{
    healthApp.Run(async context =>
    {
        context.Response.StatusCode = 200;
        await context.Response.WriteAsync("healthy");
    });
});

app.UseAuthentication(); // Health endpoint bypasses this
```

### Problem: CORS errors behind Front Door

**Symptoms:**

- Preflight OPTIONS requests fail
- Browser console shows CORS errors

**Solution:**

Add your Front Door and frontend origins to the CORS policy:

```csharp
builder.Services.AddCors(options =>
{
    options.AddDefaultPolicy(policy =>
    {
        policy.WithOrigins(
            "https://your-frontend.azurefd.net",
            "https://your-app.com"
        )
        .AllowAnyMethod()
        .AllowAnyHeader()
        .AllowCredentials();
    });
});

var app = builder.Build();

app.UseForwardedHeaders();
app.UseCors(); // Before authentication
app.UseAuthentication();
app.UseAuthorization();
```

### Problem: "Forwarded header" warnings in logs

**Symptoms:**

```
Microsoft.AspNetCore.HttpOverrides.ForwardedHeadersMiddleware: Unknown proxy
```

**Solution:**

Clear the known networks and proxies to accept forwarded headers from Azure infrastructure:

```csharp
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    // Clear known networks to accept from any proxy
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();

    // Or explicitly add Azure IP ranges (more secure but complex)
    // options.KnownProxies.Add(IPAddress.Parse("20.x.x.x"));
});
```

### Problem: APIM returns 401 but backend returns 200

**Symptoms:**

- Token is valid for the backend
- APIM `validate-jwt` policy fails

**Solution:**

Verify the APIM policy audience matches the token audience:

```xml
<validate-jwt header-name="Authorization">
    <openid-config url="https://login.microsoftonline.com/{tenant}/v2.0/.well-known/openid-configuration" />
    <audiences>
        <!-- Must match the 'aud' claim in your token -->
        <audience>api://your-backend-api-client-id</audience>
    </audiences>
</validate-jwt>
```

### Problem: Multiple authentication schemes conflict

**Symptoms:**

- Using both JWT bearer and other schemes
- Wrong scheme is selected

**Solution:**

Specify the authentication scheme explicitly in the controller:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.Identity.Web;

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"))
    .AddScheme<MyCustomOptions, MyCustomHandler>("CustomScheme", options => {});

// In controller, specify scheme explicitly
[Authorize(AuthenticationSchemes = JwtBearerDefaults.AuthenticationScheme)]
public class WeatherForecastController : ControllerBase
{
    // ...
}
```

---

## Follow best practices

Apply these practices to build a secure, resilient API deployment behind gateways.

### 1. Defense in depth

**Always validate tokens in the backend API**, even if the gateway validates them:

```csharp
// Gateway validates token (APIM policy)
// Backend ALSO validates token (Microsoft.Identity.Web)
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));
```

Gateway configuration can change and tokens can be replayed. Defense in depth is critical for security.

### 2. Use managed identities for gateway-to-backend communication

If your gateway calls the backend with its own identity, configure the backend to accept both user tokens and managed identity tokens:

```csharp
// Backend accepts both user tokens and gateway's managed identity
builder.Services.Configure<JwtBearerOptions>(JwtBearerDefaults.AuthenticationScheme, options =>
{
    options.TokenValidationParameters.ValidAudiences = new[]
    {
        "api://backend-api-client-id", // User tokens
        "https://management.azure.com" // Managed identity tokens (if applicable)
    };
});
```

### 3. Monitor gateway metrics

Track these key metrics to maintain visibility into your gateway deployment:

- 401/403 error rates
- Token validation failures
- Health probe failures
- Forwarded headers \(for debugging\)

### 4. Use Application Insights

Add Application Insights telemetry to log gateway-specific request properties:

```csharp
builder.Services.AddApplicationInsightsTelemetry();

// Log custom properties
app.Use(async (context, next) =>
{
    var telemetry = context.RequestServices.GetRequiredService<TelemetryClient>();
    telemetry.TrackEvent("ApiRequest", new Dictionary<string, string>
    {
        ["ForwardedFor"] = context.Request.Headers["X-Forwarded-For"],
        ["OriginalHost"] = context.Request.Headers["X-Forwarded-Host"],
        ["Gateway"] = "APIM" // or "FrontDoor", "AppGateway"
    });

    await next();
});
```

### 5. Separate health from ready

Use distinct endpoints for liveness \(is the service running?\) and readiness \(can the service accept traffic?\) checks:

```csharp
// Health: Is the service running?
app.MapGet("/health", () => Results.Ok()).AllowAnonymous();

// Ready: Can the service accept traffic?
app.MapHealthChecks("/ready", new HealthCheckOptions
{
    Predicate = check => check.Tags.Contains("ready")
}).AllowAnonymous();

builder.Services.AddHealthChecks()
    .AddCheck("database", () => /* check DB */ , tags: new[] { "ready" })
    .AddCheck("cache", () => /* check cache */ , tags: new[] { "ready" });
```

### 6. Document your gateway configuration

Create a README or wiki page that documents:

- Which gateway\(s\) are in use
- Token audience expectations
- CORS configuration
- Health probe endpoints
- Forwarded headers configuration
- Emergency rollback procedures

---

## Build a complete example with Azure API Management

This section provides a full, production-ready example of an ASP.NET Core API behind Azure API Management with Microsoft Entra ID authentication.

### Backend API \(ASP.NET Core\)

The following `Program.cs` configures forwarded headers, Microsoft Entra authentication, health checks, and Application Insights:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.AspNetCore.HttpOverrides;
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// Forwarded headers for APIM
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.All;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

// Authentication
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddMicrosoftGraph()
    .AddInMemoryTokenCaches();

// Application Insights
builder.Services.AddApplicationInsightsTelemetry();

// Health checks
builder.Services.AddHealthChecks();

builder.Services.AddControllers();

var app = builder.Build();

// Health endpoint (unauthenticated)
app.MapHealthChecks("/health").AllowAnonymous();

// Middleware order is critical
app.UseForwardedHeaders();
app.UseHttpsRedirection();
app.UseAuthentication();
app.UseAuthorization();

app.MapControllers();

app.Run();
```

Add the following Microsoft Entra and Application Insights configuration to `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "backend-api-client-id",
    "Audience": "api://backend-api-client-id"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "Microsoft.Identity.Web": "Debug"
    }
  },
  "ApplicationInsights": {
    "ConnectionString": "your-connection-string"
  }
}
```

The following controller requires authentication and logs forwarded headers for debugging:

```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Identity.Web.Resource;

[Authorize]
[ApiController]
[Route("[controller]")]
[RequiredScope("access_as_user")]
public class WeatherForecastController : ControllerBase
{
    private readonly ILogger<WeatherForecastController> _logger;

    public WeatherForecastController(ILogger<WeatherForecastController> logger)
    {
        _logger = logger;
    }

    [HttpGet]
    public IActionResult Get()
    {
        // Log forwarded headers for debugging
        var forwardedFor = HttpContext.Request.Headers["X-Forwarded-For"];
        var forwardedHost = HttpContext.Request.Headers["X-Forwarded-Host"];

        _logger.LogInformation(
            "Request from {ForwardedFor} via {ForwardedHost}",
            forwardedFor,
            forwardedHost);

        return Ok(new[] { "Weather", "Forecast", "Data" });
    }
}
```

### APIM configuration

The following inbound policy validates JWT tokens, applies rate limiting, forwards headers, and configures CORS:

```xml
<policies>
    <inbound>
        <base />

        <!-- Rate limiting per subscription -->
        <rate-limit-by-key calls="100" renewal-period="60"
                           counter-key="@(context.Subscription.Id)" />

        <!-- Validate JWT -->
        <validate-jwt header-name="Authorization"
                      failed-validation-httpcode="401"
                      failed-validation-error-message="Unauthorized">
            <openid-config url="https://login.microsoftonline.com/{tenant-id}/v2.0/.well-known/openid-configuration" />
            <audiences>
                <audience>api://backend-api-client-id</audience>
            </audiences>
            <issuers>
                <issuer>https://login.microsoftonline.com/{tenant-id}/v2.0</issuer>
            </issuers>
            <required-claims>
                <claim name="scp" match="any">
                    <value>access_as_user</value>
                </claim>
            </required-claims>
        </validate-jwt>

        <!-- Forward headers -->
        <set-header name="X-Forwarded-Host" exists-action="override">
            <value>@(context.Request.OriginalUrl.Host)</value>
        </set-header>
        <set-header name="X-Forwarded-Proto" exists-action="override">
            <value>@(context.Request.OriginalUrl.Scheme)</value>
        </set-header>

        <!-- Backend URL -->
        <set-backend-service base-url="https://your-backend.azurewebsites.net" />
    </inbound>

    <backend>
        <base />
    </backend>

    <outbound>
        <base />

        <!-- Add CORS headers if needed -->
        <cors>
            <allowed-origins>
                <origin>https://your-frontend.com</origin>
            </allowed-origins>
            <allowed-methods>
                <method>GET</method>
                <method>POST</method>
            </allowed-methods>
            <allowed-headers>
                <header>*</header>
            </allowed-headers>
        </cors>
    </outbound>

    <on-error>
        <base />
    </on-error>
</policies>
```

## Related content

- [Deploying Web Apps Behind Proxies and Gateways](https://learn.microsoft.com/en-us/entra/msidweb/advanced/web-apps-behind-proxies)
- [Quickstart: Protect a web API](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi)
- [Authorization](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)
- [Logging and Diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging)
