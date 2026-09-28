<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/advanced/web-apps-behind-proxies -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Deploy web apps behind proxies and gateways

When you deploy ASP.NET Core web apps with Microsoft.Identity.Web behind reverse proxies, load balancers, or Azure gateways, you must handle **redirect URIs** correctly for authentication callbacks to succeed.

Redirect URIs become complex in proxy scenarios because:

- **Microsoft Entra ID redirects users** to the configured redirect URI after sign-in
- **Proxies change the request context** - scheme \(HTTP/HTTPS\), host, port, path
- **Redirect URI must match exactly** what's registered in Microsoft Entra ID
- **CallbackPath** must work through the proxy

## Identify common proxy scenarios

The following scenarios illustrate how different proxy architectures affect redirect URI construction.

### Azure Application Gateway

**Use case:** Regional load balancing, WAF, SSL termination

**Impact on redirect URI:**

- Gateway URL: `https://gateway.contoso.com/myapp`
- Backend URL: `http://backend.internal/`
- Microsoft Entra ID redirect: `https://gateway.contoso.com/myapp/signin-oidc`

### Azure Front Door

**Use case:** Global distribution, CDN, multiple regions

**Impact on redirect URI:**

- Front Door URL: `https://myapp.azurefd.net`
- Backend URLs: `https://app-eastus.azurewebsites.net`, `https://app-westus.azurewebsites.net`
- Microsoft Entra ID redirect: `https://myapp.azurefd.net/signin-oidc`

### On-premises reverse proxy

**Use case:** Corporate network, existing infrastructure

**Impact on redirect URI:**

- Proxy URL: `https://apps.corp.com/myapp`
- Backend URL: `http://appserver:5000/`
- Microsoft Entra ID redirect: `https://apps.corp.com/myapp/signin-oidc`

### Kubernetes ingress

**Use case:** Container orchestration, microservices

**Impact on redirect URI:**

- Ingress URL: `https://apps.k8s.com/webapp`
- Service URL: `http://webapp-service.default.svc.cluster.local`
- Microsoft Entra ID redirect: `https://apps.k8s.com/webapp/signin-oidc`

---

## Configure forwarded headers

Forwarded headers are essential for proxy deployments. Without them, the backend app builds incorrect redirect URIs.

### Why forwarded headers matter

Web apps **need correct request context** to:

1. Build absolute redirect URIs for Microsoft Entra ID
2. Validate the incoming authentication response
3. Generate correct sign-out URIs
4. Handle HTTPS requirement enforcement

**Without forwarded headers middleware:**

```
User visits: https://gateway.contoso.com/myapp
Backend sees: http://localhost:5000/
Redirect URI built: http://localhost:5000/signin-oidc  Wrong!
Microsoft Entra ID redirects to: https://gateway.contoso.com/myapp/signin-oidc
Backend doesn't recognize it: Error!
```

**With forwarded headers middleware:**

```
User visits: https://gateway.contoso.com/myapp
Backend sees forwarded headers: X-Forwarded-Proto: https, X-Forwarded-Host: gateway.contoso.com
Redirect URI built: https://gateway.contoso.com/myapp/signin-oidc  Correct!
Microsoft Entra ID redirects to: https://gateway.contoso.com/myapp/signin-oidc
Backend recognizes it: Success!
```

### Set up basic forwarded headers

Configure the forwarded headers middleware in `Program.cs` before authentication:

```csharp
using Microsoft.AspNetCore.Authentication.OpenIdConnect;
using Microsoft.AspNetCore.HttpOverrides;
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// CRITICAL: Configure forwarded headers BEFORE authentication
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;

    // Accept headers from any source (proxy/gateway)
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();

    // Standard header names
    options.ForwardedForHeaderName = "X-Forwarded-For";
    options.ForwardedProtoHeaderName = "X-Forwarded-Proto";
    options.ForwardedHostHeaderName = "X-Forwarded-Host";
});

// Authentication
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddRazorPages();

var app = builder.Build();

// CRITICAL: Use forwarded headers BEFORE authentication
app.UseForwardedHeaders();

// Only enforce HTTPS if you're sure the proxy forwards the scheme correctly
if (!app.Environment.IsDevelopment())
{
    app.UseHttpsRedirection();
}

app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.MapRazorPages();

app.Run();
```

Add the authentication settings to `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientSecret": "your-client-secret",
    "CallbackPath": "/signin-oidc"
  }
}
```

Register the gateway URL as a redirect URI in the Microsoft Entra app registration:

```
https://gateway.contoso.com/myapp/signin-oidc
```

---

## Handle path-based routing

Use path-based routing when a proxy adds a path prefix to requests.

### Problem: Proxy adds path prefix

**Scenario:**

- Proxy URL: `https://apps.contoso.com/webapp1`
- Backend URL: `http://backend:5000/`
- Backend only knows about `/`, not `/webapp1`

### Solution 1: Use PathBase \(recommended\)

Set `UsePathBase` to tell the app about its path prefix:

```csharp
var app = builder.Build();

// Tell the app it's hosted at a path prefix
app.UsePathBase("/webapp1");

app.UseForwardedHeaders();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.MapRazorPages();

app.Run();
```

**How it works:**

- `HttpContext.Request.Path` removes the `/webapp1` prefix for routing
- `HttpContext.Request.PathBase` contains `/webapp1`
- Link generation automatically includes the path base
- Redirect URIs automatically include the path base

Register the full path in the Microsoft Entra app registration:

```
https://apps.contoso.com/webapp1/signin-oidc
```

### Solution 2: Proxy rewrites path

Some proxies strip the path prefix before forwarding. Configure the proxy to rewrite the path and forward the original headers:

**NGINX configuration:**

```nginx
location /webapp1/ {
    proxy_pass http://backend:5000/;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
    proxy_set_header X-Forwarded-Host $host;
    proxy_set_header X-Original-URL $request_uri;
}
```

When the proxy strips the prefix, no `PathBase` is needed in the application:

```csharp
// No PathBase needed if proxy strips the prefix
app.UseForwardedHeaders();
```

Register the proxy-facing URL in the Microsoft Entra app registration:

```
https://apps.contoso.com/webapp1/signin-oidc
```

### Solution 3: Custom middleware for dynamic PathBase

When the path base varies by environment, read it from configuration or detect it from request headers:

```csharp
// Read path base from configuration or headers
var pathBase = builder.Configuration["PathBase"];
if (!string.IsNullOrEmpty(pathBase))
{
    app.UsePathBase(pathBase);
}

// Or detect from X-Forwarded-Prefix header
app.Use((context, next) =>
{
    var forwardedPrefix = context.Request.Headers["X-Forwarded-Prefix"].ToString();
    if (!string.IsNullOrEmpty(forwardedPrefix))
    {
        context.Request.PathBase = forwardedPrefix;
    }
    return next();
});

app.UseForwardedHeaders();
```

---

## Handle SSL/TLS termination

When a proxy terminates SSL/TLS, the backend receives HTTP requests and builds incorrect redirect URIs unless you configure header forwarding.

### Problem: Proxy terminates HTTPS

**Scenario:**

- User connects to proxy via HTTPS
- Proxy connects to backend via HTTP
- Backend builds HTTP redirect URIs \(wrong!\)

### Solution: X-Forwarded-Proto header

Configure the proxy to send the `X-Forwarded-Proto` header so the backend knows the original scheme.

**Proxy configuration \(NGINX\):**

```nginx
location / {
    proxy_pass http://backend:5000;
    proxy_set_header X-Forwarded-Proto $scheme;  # Critical!
    proxy_set_header X-Forwarded-Host $host;
}
```

Configure the app to read the forwarded proto header and set the request scheme:

```csharp
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

var app = builder.Build();

app.UseForwardedHeaders(); // Reads X-Forwarded-Proto and sets Request.Scheme = "https"

// HTTPS redirection becomes safe
app.UseHttpsRedirection(); // Won't create infinite redirect loop

app.UseAuthentication();
```

### Common mistake: HTTPS redirection loop

**Problem:**

```csharp
// Without UseForwardedHeaders()
app.UseHttpsRedirection(); // Sees Request.Scheme = "http", redirects to HTTPS
// User gets infinite redirect loop!
```

**Solution:**

```csharp
// WITH UseForwardedHeaders()
app.UseForwardedHeaders(); // Sets Request.Scheme = "https" from X-Forwarded-Proto
app.UseHttpsRedirection(); // Sees HTTPS, no redirect needed 
```

---

## Configure custom domains

Use a custom domain with Azure Front Door to present a branded URL to users while routing traffic to backend services.

### Scenario: Custom domain through Azure Front Door

**Architecture:**

- Custom domain: `https://myapp.contoso.com`
- Front Door: `https://myapp.azurefd.net` \(backend origin\)
- Azure Web App: `https://myapp-backend.azurewebsites.net`

**Front Door Configuration:**

1. Add custom domain `myapp.contoso.com` to Front Door
2. Configure SSL certificate \(Front Door managed or custom\)
3. Set backend pool to `myapp-backend.azurewebsites.net`
4. Enable HTTPS only

Configure the app to accept forwarded headers from Front Door:

```csharp
// No special configuration needed if headers are forwarded correctly
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});
```

Register both the sign-in and sign-out callback URIs in the Microsoft Entra app registration:

```
https://myapp.contoso.com/signin-oidc
https://myapp.contoso.com/signout-callback-oidc
```

Use the following diagnostic endpoint to verify the redirect URI the app generates:

```csharp
// In a controller or page
public IActionResult TestRedirectUri()
{
    var request = HttpContext.Request;
    var scheme = request.Scheme; // Should be "https"
    var host = request.Host.Value; // Should be "myapp.contoso.com"
    var pathBase = request.PathBase.Value; // Should be "" or your path base
    var path = "/signin-oidc";

    var redirectUri = $"{scheme}://{host}{pathBase}{path}";
    // Expected: https://myapp.contoso.com/signin-oidc

    return Content($"Redirect URI would be: {redirectUri}");
}
```

---

## Register multiple redirect URIs

When your app runs behind different gateways across environments, register a redirect URI for each one.

### Problem: Same app, multiple gateways

**Scenario:**

- Production: `https://app.contoso.com` \(Front Door\)
- Staging: `https://app-staging.azurewebsites.net` \(Direct\)
- Development: `https://localhost:5001` \(Local\)

### Solution: Register all redirect URIs

Add every environment-specific redirect URI to the Microsoft Entra app registration:

```
https://app.contoso.com/signin-oidc
https://app-staging.azurewebsites.net/signin-oidc
https://localhost:5001/signin-oidc
```

The application code requires no environment-specific changes:

```csharp
var app = builder.Build();

app.UseForwardedHeaders(); // Handles proxy scenarios
app.UseAuthentication(); // Builds correct redirect URI based on request context
```

**How it works:**

- Application dynamically builds redirect URI based on incoming request
- `HttpContext.Request.Scheme`, `Host`, and `PathBase` determine the URI
- As long as it's registered in Microsoft Entra ID, authentication succeeds

---

## Configure Azure Application Gateway

This section provides a complete configuration example for deploying a web app behind Azure Application Gateway with path-based routing.

### Complete example with path-based routing

**Application Gateway Settings:**

**Backend Pool:**

- Target: `backend.azurewebsites.net` or IP address

**HTTP Settings:**

- Protocol: HTTPS \(recommended\) or HTTP
- Port: 443 or 80
- Override backend path: No
- Custom probe: Yes

**Health Probe:**

- Protocol: HTTPS or HTTP
- Host: Leave blank \(uses backend pool hostname\)
- Path: `/health` \(must be anonymous endpoint\)
- Interval: 30 seconds

**Routing Rule:**

- Name: `webapp-rule`
- Listener: HTTPS listener on port 443
- Backend pool: Your backend pool
- HTTP settings: Your HTTP settings

Configure the application to handle forwarded headers, authentication, and health probes:

```csharp
using Microsoft.AspNetCore.HttpOverrides;

var builder = WebApplication.CreateBuilder(args);

// Forwarded headers for Application Gateway
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

// Authentication
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"));

// Health checks (for Application Gateway probe)
builder.Services.AddHealthChecks();

builder.Services.AddRazorPages();

var app = builder.Build();

// Health endpoint BEFORE authentication (critical for gateway probes)
app.MapHealthChecks("/health").AllowAnonymous();

// Middleware order
app.UseForwardedHeaders();
app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.MapRazorPages();

app.Run();
```

Add the authentication settings to `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientSecret": "your-client-secret",
    "CallbackPath": "/signin-oidc"
  }
}
```

Register the gateway-facing redirect URIs in the Microsoft Entra app registration:

```
https://gateway.contoso.com/signin-oidc
https://gateway.contoso.com/signout-callback-oidc
```

---

## Configure Azure Front Door

This section shows how to deploy a multi-region web app behind Azure Front Door with consistent authentication.

### Multi-region web app deployment

**Scenario:**

- Front Door: `https://app.azurefd.net` \(global endpoint\)
- East US: `https://app-eastus.azurewebsites.net`
- West US: `https://app-westus.azurewebsites.net`
- Users routed to nearest region

**Front Door Configuration:**

**Origin Group:**

- Name: `webapp-origins`
- Health probe: `/health`
- Load balancing: Latency-based

**Origins:**

1. `app-eastus.azurewebsites.net` \(priority 1\)
2. `app-westus.azurewebsites.net` \(priority 1\)

**Route:**

- Path: `/*`
- Forwarding protocol: HTTPS only
- Origin group: `webapp-origins`

Deploy the same application code to both regions:

```csharp
using Microsoft.AspNetCore.HttpOverrides;

var builder = WebApplication.CreateBuilder(args);

// Forwarded headers for Front Door
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddHealthChecks();
builder.Services.AddRazorPages();

var app = builder.Build();

// Health check for Front Door probe
app.MapHealthChecks("/health").AllowAnonymous();

app.UseForwardedHeaders();
app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.MapRazorPages();

app.Run();
```

Both regions share the **same Microsoft Entra app registration** with the **same redirect URI**:

```
https://app.azurefd.net/signin-oidc
https://app.azurefd.net/signout-callback-oidc
```

**Why it works:**

- Front Door URL is consistent across regions
- Forwarded headers ensure backend builds correct redirect URI
- Token acquisition happens at regional backend
- Distributed token cache \(Redis\) shares tokens across regions

---

## Troubleshoot common issues

This section covers the most common authentication failures in proxy deployments and how to resolve them.

### Problem: "Redirect URI mismatch" error

**Symptoms:**

```
AADSTS50011: The redirect URI 'http://localhost:5000/signin-oidc'
specified in the request does not match the redirect URIs configured
for the application 'your-app-id'.
```

**Possible causes:**

1. **Missing forwarded headers middleware**

   ```csharp
   // Fix: Add BEFORE authentication
   app.UseForwardedHeaders();
   app.UseAuthentication();
   ```

2. **Wrong redirect URI registered in Microsoft Entra ID**

   - Check registered URIs in Azure portal
   - Ensure HTTPS \(not HTTP\) for production
   - Ensure host matches \(including port if non-standard\)
   - Ensure path includes PathBase if applicable

3. **Proxy not forwarding headers**

   - Check proxy configuration
   - Verify `X-Forwarded-Proto`, `X-Forwarded-Host` are set
   - Test with curl: `curl -H "X-Forwarded-Proto: https" -H "X-Forwarded-Host: gateway.com" http://backend:5000/`

4. **PathBase not configured**

   ```csharp
   // If proxy adds /myapp prefix, add this:
   app.UsePathBase("/myapp");
   ```

Add the following diagnostic middleware to log the redirect URI the app builds:

```csharp
// Add this middleware to log the redirect URI being built
app.Use(async (context, next) =>
{
    var logger = context.RequestServices.GetRequiredService<ILogger<Program>>();
    logger.LogInformation(
        "Request: Scheme={Scheme}, Host={Host}, PathBase={PathBase}, Path={Path}",
        context.Request.Scheme,
        context.Request.Host,
        context.Request.PathBase,
        context.Request.Path);

    await next();
});
```

### Problem: Authentication works locally but not behind proxy

**Symptoms:**

- Sign-in works on `localhost:5001`
- Sign-in fails on `gateway.contoso.com`
- Error: Redirect URI mismatch or correlation failed

**Solution checklist:**

1. **Forwarded headers configured and used first**

```csharp
app.UseForwardedHeaders(); // Must be first!
```

2. **Proxy forwards required headers**

- `X-Forwarded-Proto: https`
- `X-Forwarded-Host: gateway.contoso.com`
- Optional: `X-Forwarded-Prefix` for path base

3. **Redirect URI registered in Microsoft Entra ID**

- `https://gateway.contoso.com/signin-oidc`

4. **PathBase configured if needed**

```csharp
app.UsePathBase("/myapp"); // If proxy adds prefix
```

5. **HTTPS enforced correctly**

```csharp
app.UseForwardedHeaders(); // Reads X-Forwarded-Proto first
app.UseHttpsRedirection(); // Then enforces HTTPS
```

### Problem: Sign-Out fails or redirects to wrong URL

**Symptoms:**

- Sign-in works
- Sign-out redirects to wrong URL \(localhost, http://, wrong host\)

Set the `PostLogoutRedirectUri` using the forwarded request context:

```csharp
// Ensure PostLogoutRedirectUri uses correct base URL
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
    {
        options.Events.OnRedirectToIdentityProviderForSignOut = context =>
        {
            // Build correct post-logout redirect URI
            var request = context.HttpContext.Request;
            var postLogoutUri = $"{request.Scheme}://{request.Host}{request.PathBase}/signout-callback-oidc";

            context.ProtocolMessage.PostLogoutRedirectUri = postLogoutUri;
            return Task.CompletedTask;
        };
    });
```

Register the sign-out callback URI in the Microsoft Entra app registration:

```
https://gateway.contoso.com/signout-callback-oidc
```

### Problem: Infinite redirect loop

**Symptoms:**

- Browser keeps redirecting between app and Microsoft Entra ID
- Login never completes

**Possible causes:**

1. **HTTPS redirection before forwarded headers**

   ```csharp
   // WRONG ORDER:
   app.UseHttpsRedirection(); // Sees HTTP, redirects to HTTPS
   app.UseForwardedHeaders(); // Too late!

   // CORRECT ORDER:
   app.UseForwardedHeaders(); // Sets scheme to HTTPS
   app.UseHttpsRedirection(); // Sees HTTPS, no redirect
   ```

2. **Cookie settings not compatible with proxy**

   ```csharp
   builder.Services.Configure<CookiePolicyOptions>(options =>
   {
       options.MinimumSameSitePolicy = SameSiteMode.None; // For cross-site scenarios
       options.Secure = CookieSecurePolicy.Always; // Requires HTTPS
   });
   ```

3. **Cookie domain mismatch**

   ```csharp
   // If subdomain issues, may need to set cookie domain
   builder.Services.ConfigureApplicationCookie(options =>
   {
       options.Cookie.Domain = ".contoso.com"; // Allows cookies across subdomains
   });
   ```

---

## Follow best practices

Apply these practices to every proxy deployment to avoid common pitfalls.

### 1. Always use forwarded headers middleware

```csharp
// For ANY deployment behind proxy/gateway/load balancer
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

var app = builder.Build();
app.UseForwardedHeaders(); // FIRST middleware!
```

### 2. Register all redirect URIs

Register redirect URIs for every environment in the Microsoft Entra app registration:

```text
Production:  https://app.contoso.com/signin-oidc
Staging:     https://app-staging.azurewebsites.net/signin-oidc
Development: https://localhost:5001/signin-oidc
```

### 3. Test redirect URI generation

Add a development-only diagnostics endpoint to verify the redirect URI:

```csharp
// Add diagnostics endpoint (development only!)
if (app.Environment.IsDevelopment())
{
    app.MapGet("/debug/redirect-uri", (HttpContext context) =>
    {
        var redirectUri = $"{context.Request.Scheme}://{context.Request.Host}{context.Request.PathBase}/signin-oidc";
        return Results.Ok(new { redirectUri });
    }).AllowAnonymous();
}
```

### 4. Health endpoint for gateway probes

Map the health endpoint before authentication middleware so gateway probes don't require sign-in:

```csharp
// Must be BEFORE authentication middleware
app.MapHealthChecks("/health").AllowAnonymous();

app.UseAuthentication(); // Health endpoint bypasses this
```

### 5. Distributed token cache for multi-region

Use a distributed cache like Redis to share tokens across regions:

```csharp
// Use Redis for token cache across regions
builder.Services.AddStackExchangeRedisCache(options =>
{
    options.Configuration = builder.Configuration["Redis:ConnectionString"];
    options.InstanceName = "TokenCache_";
});

builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDistributedTokenCaches();
```

### 6. Configure logging for troubleshooting

Enable debug logging for Microsoft.Identity.Web and forwarded headers to diagnose issues:

```csharp
builder.Logging.AddConfiguration(builder.Configuration.GetSection("Logging"));

// In appsettings.json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "Microsoft.Identity.Web": "Debug",
      "Microsoft.AspNetCore.HttpOverrides": "Debug"
    }
  }
}
```

---

## Review a complete example

This end-to-end example deploys a web app behind Azure Application Gateway with Microsoft Graph integration.

### Application code

The following `Program.cs` configures forwarded headers, authentication with Microsoft Graph, and health checks:

```csharp
using Microsoft.AspNetCore.Authentication.OpenIdConnect;
using Microsoft.AspNetCore.HttpOverrides;
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.UI;

var builder = WebApplication.CreateBuilder(args);

// Forwarded headers for Application Gateway
builder.Services.Configure<ForwardedHeadersOptions>(options =>
{
    options.ForwardedHeaders = ForwardedHeaders.XForwardedFor |
                                ForwardedHeaders.XForwardedProto |
                                ForwardedHeaders.XForwardedHost;
    options.KnownNetworks.Clear();
    options.KnownProxies.Clear();
});

// Authentication
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddMicrosoftGraph()
    .AddInMemoryTokenCaches();

// Health checks
builder.Services.AddHealthChecks();

// Add Microsoft Identity UI for sign-in/sign-out
builder.Services.AddRazorPages()
    .AddMicrosoftIdentityUI();

var app = builder.Build();

// Health endpoint (before authentication)
app.MapHealthChecks("/health").AllowAnonymous();

// Middleware order is critical
app.UseForwardedHeaders();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();
app.UseAuthentication();
app.UseAuthorization();
app.MapRazorPages();
app.MapControllers();

app.Run();
```

Add the authentication and logging configuration to `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientSecret": "your-client-secret",
    "CallbackPath": "/signin-oidc",
    "SignedOutCallbackPath": "/signout-callback-oidc"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "Microsoft.Identity.Web": "Information",
      "Microsoft.AspNetCore.HttpOverrides": "Debug"
    }
  }
}
```

Register the following URIs in the Microsoft Entra app registration:

**Redirect URIs:**

```
https://gateway.contoso.com/signin-oidc
https://gateway.contoso.com/signout-callback-oidc
```

**Front-channel logout URL:**

```
https://gateway.contoso.com/signout-oidc
```

### Application Gateway configuration

Configure the following Application Gateway resources:

**Backend Pool:**

- Name: `webapp-backend`
- Target: `webapp.azurewebsites.net` or IP addresses

**HTTP Settings:**

- Name: `webapp-https-settings`
- Protocol: HTTPS
- Port: 443
- Override backend path: No
- Pick host name from backend target: Yes
- Custom probe: Yes → `webapp-health-probe`

**Health Probe:**

- Name: `webapp-health-probe`
- Protocol: HTTPS
- Pick host name from backend HTTP settings: Yes
- Path: `/health`
- Interval: 30 seconds
- Unhealthy threshold: 3

**Listener:**

- Name: `webapp-listener`
- Frontend IP: Public
- Protocol: HTTPS
- Port: 443
- SSL certificate: Your certificate

**Routing Rule:**

- Name: `webapp-rule`
- Rule type: Basic
- Listener: `webapp-listener`
- Backend target: `webapp-backend`
- HTTP settings: `webapp-https-settings`

## Related content

- [Quickstart: Web app](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp)
- [Deploying Protected APIs Behind Gateways](https://learn.microsoft.com/en-us/entra/msidweb/advanced/api-gateways)
- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Logging and Diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging)
