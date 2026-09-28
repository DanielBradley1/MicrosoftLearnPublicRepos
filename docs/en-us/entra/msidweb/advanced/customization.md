<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/advanced/customization -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Customize authentication with Microsoft.Identity.Web

Microsoft.Identity.Web provides secure defaults for authentication and authorization in ASP.NET Core applications that integrate with Microsoft Entra ID. You can customize many aspects of authentication behavior while preserving the library's built-in security features.

## Identify customizable areas

| Area | Customization Options |
| --- | --- |
| **Configuration** | All `MicrosoftIdentityOptions`, `OpenIdConnectOptions`, `JwtBearerOptions` properties |
| **Events** | OpenID Connect events \(`OnTokenValidated`, `OnRedirectToIdentityProvider`, etc.\) |
| **Token Acquisition** | Correlation IDs, extra query parameters |
| **Claims** | Add custom claims to `ClaimsPrincipal` |
| **UI** | Sign-out pages, redirect behavior |
| **Sign-In** | Login hints, domain hints |

## Choose a customization method

The following table summarizes the areas you can customize and what each area supports.

Use one of two approaches to customize options:

1. **`Configure<TOptions>`** - Configures options before they're used
2. **`PostConfigure<TOptions>`** - Configures options after all `Configure` calls

**Order of execution:**

```
Configure → Configure → ... → PostConfigure → PostConfigure → ... → Options used
```

---

## Configure authentication options

This section shows how to configure the various authentication option classes that Microsoft.Identity.Web uses.

### Understand configuration mapping

The `"AzureAd"` section in `appsettings.json` maps to multiple classes:

- [`MicrosoftIdentityOptions`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.web.microsoftidentityoptions)
- [`ConfidentialClientApplicationOptions`](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.confidentialclientapplicationoptions)

You can use any property from these classes in your configuration.

### Pattern 1: Configure MicrosoftIdentityOptions

The following code customizes `MicrosoftIdentityOptions` to enable PII logging, set client capabilities, and adjust token validation parameters:

```csharp
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"));

// Customize Microsoft Identity options
builder.Services.Configure<MicrosoftIdentityOptions>(options =>
{
    // Enable PII logging (development only!)
    options.EnablePiiLogging = true;

    // Custom client capabilities
    options.ClientCapabilities = new[] { "CP1", "CP2" };

    // Override token validation parameters
    options.TokenValidationParameters.ValidateLifetime = true;
    options.TokenValidationParameters.ClockSkew = TimeSpan.FromMinutes(5);
});

var app = builder.Build();
```

### Pattern 2: Configure OpenIdConnectOptions \(Web apps\)

The following code customizes `OpenIdConnectOptions` for a web app to set the response type, add scopes, and configure cookie and token validation settings:

```csharp
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"));

// Customize OpenIdConnect options
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    // Override response type
    options.ResponseType = "code id_token";

    // Add extra scopes
    options.Scope.Add("offline_access");
    options.Scope.Add("profile");

    // Customize token validation
    options.TokenValidationParameters.NameClaimType = "preferred_username";
    options.TokenValidationParameters.RoleClaimType = "roles";

    // Set redirect URI
    options.CallbackPath = "/signin-oidc";

    // Configure cookie options
    options.Cookie.HttpOnly = true;
    options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    options.Cookie.SameSite = SameSiteMode.Lax;
});
```

### Pattern 3: Configure JwtBearerOptions \(Web APIs\)

The following code customizes `JwtBearerOptions` for a web API to set valid audiences, claim mappings, and token lifetime validation:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

// Customize JWT Bearer options
builder.Services.Configure<JwtBearerOptions>(
    JwtBearerDefaults.AuthenticationScheme,
    options =>
{
    // Customize audience validation
    options.TokenValidationParameters.ValidAudiences = new[]
    {
        "api://your-api-client-id",
        "https://your-api.com"
    };

    // Set custom claim mappings
    options.TokenValidationParameters.NameClaimType = "name";
    options.TokenValidationParameters.RoleClaimType = "roles";

    // Customize token validation
    options.TokenValidationParameters.ValidateLifetime = true;
    options.TokenValidationParameters.ClockSkew = TimeSpan.Zero; // No tolerance
});
```

### Pattern 4: Configure Cookie options

The following code configures the cookie policy and cookie authentication options for your app, including security settings and expiration behavior:

```csharp
using Microsoft.AspNetCore.Authentication.Cookies;

// Configure cookie policy
builder.Services.Configure<CookiePolicyOptions>(options =>
{
    options.MinimumSameSitePolicy = SameSiteMode.Lax;
    options.Secure = CookieSecurePolicy.Always;
    options.HttpOnly = Microsoft.AspNetCore.CookiePolicy.HttpOnlyPolicy.Always;
});

// Configure cookie authentication options
builder.Services.Configure<CookieAuthenticationOptions>(
    CookieAuthenticationDefaults.AuthenticationScheme,
    options =>
{
    options.Cookie.Name = "MyApp.Auth";
    options.Cookie.HttpOnly = true;
    options.Cookie.SecurePolicy = CookieSecurePolicy.Always;
    options.Cookie.SameSite = SameSiteMode.Lax;
    options.ExpireTimeSpan = TimeSpan.FromHours(1);
    options.SlidingExpiration = true;
});
```

---

## Customize event handlers

OpenID Connect and JWT Bearer authentication expose events you can hook into. Microsoft.Identity.Web sets up its own event handlers, so you must chain your custom handlers with the existing ones to preserve built-in functionality.

### Preserve existing handlers

When you add custom event handlers, always save and call the existing handler first. The following example shows the wrong and correct approaches.

The following code **incorrectly** overwrites the Microsoft.Identity.Web handler:

```csharp
services.Configure<JwtBearerOptions>(JwtBearerDefaults.AuthenticationScheme, options =>
{
    options.Events.OnTokenValidated = async context =>
    {
        // Your code - but you LOST the built-in validation!
        await Task.CompletedTask;
    };
});
```

The following code **correctly** chains with the existing handler:

```csharp
services.Configure<JwtBearerOptions>(JwtBearerDefaults.AuthenticationScheme, options =>
{
    var existingOnTokenValidatedHandler = options.Events.OnTokenValidated;

    options.Events.OnTokenValidated = async context =>
    {
        // Call Microsoft.Identity.Web's handler FIRST
        await existingOnTokenValidatedHandler(context);

        // Then your custom code
        // (executes AFTER built-in security checks)
        var identity = context.Principal.Identity as ClaimsIdentity;
        identity?.AddClaim(new Claim("custom_claim", "custom_value"));
    };
});
```

### Apply common event scenarios

#### Add custom claims after token validation

The following code adds custom claims to the `ClaimsPrincipal` after token validation in a web API. It looks up the user's department from a database and assigns an application-specific role based on the email domain:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using System.Security.Claims;

builder.Services.Configure<JwtBearerOptions>(
    JwtBearerDefaults.AuthenticationScheme,
    options =>
{
    var existingHandler = options.Events.OnTokenValidated;

    options.Events.OnTokenValidated = async context =>
    {
        // Preserve built-in validation
        await existingHandler(context);

        // Add custom claims
        var identity = context.Principal.Identity as ClaimsIdentity;

        // Example: Add department claim from database
        var userObjectId = context.Principal.FindFirst("oid")?.Value;
        if (!string.IsNullOrEmpty(userObjectId))
        {
            var department = await GetUserDepartment(userObjectId);
            identity?.AddClaim(new Claim("department", department));
        }

        // Example: Add application-specific role
        var email = context.Principal.FindFirst("email")?.Value;
        if (email?.EndsWith("@admin.com") == true)
        {
            identity?.AddClaim(new Claim(ClaimTypes.Role, "SuperAdmin"));
        }
    };
});
```

The following code adds custom claims in a web app by calling Microsoft Graph to retrieve additional user profile data after token validation:

```csharp
using Microsoft.AspNetCore.Authentication.OpenIdConnect;

builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    var existingHandler = options.Events.OnTokenValidated;

    options.Events.OnTokenValidated = async context =>
    {
        // Preserve built-in processing
        await existingHandler(context);

        // Call Microsoft Graph to get additional user data
        var graphClient = context.HttpContext.RequestServices
            .GetRequiredService<GraphServiceClient>();

        var user = await graphClient.Me.GetAsync();

        var identity = context.Principal.Identity as ClaimsIdentity;
        identity?.AddClaim(new Claim("jobTitle", user?.JobTitle ?? ""));
        identity?.AddClaim(new Claim("department", user?.Department ?? ""));
    };
});
```

#### Add query parameters to authorization request

The following code adds custom query parameters to the authorization request sent to the Microsoft Entra identity provider:

```csharp
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    var existingHandler = options.Events.OnRedirectToIdentityProvider;

    options.Events.OnRedirectToIdentityProvider = async context =>
    {
        // Preserve existing behavior
        if (existingHandler != null)
        {
            await existingHandler(context);
        }

        // Add custom query parameters
        context.ProtocolMessage.Parameters.Add("slice", "testslice");
        context.ProtocolMessage.Parameters.Add("custom_param", "custom_value");

        // Conditional parameters based on request
        if (context.HttpContext.Request.Query.ContainsKey("prompt"))
        {
            context.ProtocolMessage.Prompt = context.HttpContext.Request.Query["prompt"];
        }
    };
});
```

#### Customize authentication failure handling

The following code handles authentication failures by logging the error and returning a custom JSON error response:

```csharp
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    options.Events.OnAuthenticationFailed = async context =>
    {
        // Log the error
        var logger = context.HttpContext.RequestServices
            .GetRequiredService<ILogger<Program>>();
        logger.LogError(context.Exception, "Authentication failed");

        // Customize error response
        context.Response.StatusCode = 401;
        context.Response.ContentType = "application/json";
        await context.Response.WriteAsync($$"""
            {
                "error": "authentication_failed",
                "error_description": "{{context.Exception.Message}}"
            }
            """);

        context.HandleResponse(); // Suppress default error handling
    };
});
```

#### Handle access denied

The following code redirects users to a custom page when they deny consent:

```csharp
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    options.Events.OnAccessDenied = async context =>
    {
        // User denied consent
        context.Response.Redirect("/Home/AccessDenied");
        context.HandleResponse();
        await Task.CompletedTask;
    };
});
```

---

## Customize token acquisition

You can customize how tokens are acquired when calling downstream APIs by passing options to `IDownstreamApi`.

### Use IDownstreamApi with custom options

The following code passes a correlation ID and extra query parameters when acquiring a token through `IDownstreamApi`:

```csharp
using Microsoft.Identity.Abstractions;

public class TodoListController : ControllerBase
{
    private readonly IDownstreamApi _downstreamApi;

    public TodoListController(IDownstreamApi downstreamApi)
    {
        _downstreamApi = downstreamApi;
    }

    [HttpGet("{id}")]
    public async Task<ActionResult> GetTodo(int id, Guid correlationId)
    {
        var result = await _downstreamApi.GetForUserAsync<Todo>(
            "TodoListService",
            options =>
            {
                options.RelativePath = $"api/todolist/{id}";

                // Customize token acquisition
                options.TokenAcquisitionOptions = new TokenAcquisitionOptions
                {
                    CorrelationId = correlationId,
                    ExtraQueryParameters = new Dictionary<string, string>
                    {
                        { "slice", "test_slice" }
                    }
                };
            });

        return Ok(result);
    }
}
```

---

## Customize the UI

You can control where users land after sign-in and sign-out, and customize the signed-out experience.

### Redirect to a specific page after sign-in

Use the `redirectUri` parameter to send users to a specific page after they sign in:

```html
<!-- Razor view -->
<a href="/MicrosoftIdentity/Account/SignIn?redirectUri=/Dashboard">Sign In</a>

<!-- Or in controller -->
[HttpGet]
public IActionResult SignInToDashboard()
{
    return RedirectToAction("SignIn", "Account", new
    {
        area = "MicrosoftIdentity",
        redirectUri = "/Dashboard"
    });
}
```

### Customize the signed-out page

**Option 1: Override the Razor Page**

Create a file at `Areas/MicrosoftIdentity/Pages/Account/SignedOut.cshtml` with your custom content:

```cshtml
@page
@model Microsoft.Identity.Web.UI.Areas.MicrosoftIdentity.Pages.Account.SignedOutModel
@{
    ViewData["Title"] = "Signed out";
}

<div class="container text-center mt-5">
    <h1>You have been signed out</h1>
    <p>Thank you for using our application.</p>
    <a asp-area="" asp-controller="Home" asp-action="Index" class="btn btn-primary">
        Return to Home
    </a>
</div>
```

**Option 2: Redirect to a custom page**

The following code redirects users to a custom signed-out page instead of the default:

```csharp
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    options.Events.OnSignedOutCallbackRedirect = context =>
    {
        context.Response.Redirect("/Home/SignedOut");
        context.HandleResponse();
        return Task.CompletedTask;
    };
});
```

---

## Customize the sign-in experience

### Use login hints and domain hints

Streamline the sign-in experience by pre-populating usernames and directing users to specific Microsoft Entra tenants.

#### Understand hints

| Hint | Purpose | Example |
| --- | --- | --- |
| **loginHint** | Pre-populate username/email field | `"user@contoso.com"` |
| **domainHint** | Direct to specific tenant login page | `"contoso.com"` |

#### Apply hint patterns

**Pattern 1: Controller-based**

The following code shows controller actions for standard sign-in, sign-in with a login hint, domain hint, or both:

```csharp
using Microsoft.AspNetCore.Mvc;

public class AuthController : Controller
{
    [HttpGet]
    public IActionResult SignIn()
    {
        // Standard sign-in
        return RedirectToAction("SignIn", "Account", new
        {
            area = "MicrosoftIdentity",
            redirectUri = "/Dashboard"
        });
    }

    [HttpGet]
    public IActionResult SignInWithLoginHint()
    {
        // Pre-populate username
        return RedirectToAction("SignIn", "Account", new
        {
            area = "MicrosoftIdentity",
            redirectUri = "/Dashboard",
            loginHint = "user@contoso.com"
        });
    }

    [HttpGet]
    public IActionResult SignInWithDomainHint()
    {
        // Direct to Contoso tenant
        return RedirectToAction("SignIn", "Account", new
        {
            area = "MicrosoftIdentity",
            redirectUri = "/Dashboard",
            domainHint = "contoso.com"
        });
    }

    [HttpGet]
    public IActionResult SignInWithBothHints()
    {
        // Pre-populate AND direct to tenant
        return RedirectToAction("SignIn", "Account", new
        {
            area = "MicrosoftIdentity",
            redirectUri = "/Dashboard",
            loginHint = "user@contoso.com",
            domainHint = "contoso.com"
        });
    }
}
```

**Pattern 2: View-based**

The following HTML shows sign-in links with different hint configurations:

```html
<div class="sign-in-options">
    <h2>Sign In Options</h2>

    <!-- Standard sign-in -->
    <a href="/MicrosoftIdentity/Account/SignIn?redirectUri=/Dashboard"
       class="btn btn-primary">
        Sign In
    </a>

    <!-- With login hint -->
    <a href="/MicrosoftIdentity/Account/SignIn?redirectUri=/Dashboard&loginHint=user@contoso.com"
       class="btn btn-secondary">
        Sign In as user@contoso.com
    </a>

    <!-- With domain hint -->
    <a href="/MicrosoftIdentity/Account/SignIn?redirectUri=/Dashboard&domainHint=contoso.com"
       class="btn btn-secondary">
        Sign In (Contoso)
    </a>
</div>
```

**Pattern 3: Programmatic with OnRedirectToIdentityProvider**

The following code dynamically sets hints based on query parameters and cookies during the redirect to the identity provider:

```csharp
builder.Services.Configure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options =>
{
    var existingHandler = options.Events.OnRedirectToIdentityProvider;

    options.Events.OnRedirectToIdentityProvider = async context =>
    {
        if (existingHandler != null)
        {
            await existingHandler(context);
        }

        // Add hints based on application logic
        if (context.HttpContext.Request.Query.TryGetValue("tenant", out var tenant))
        {
            context.ProtocolMessage.DomainHint = tenant;
        }

        // Get suggested user from cookie or session
        var suggestedUser = context.HttpContext.Request.Cookies["LastSignedInUser"];
        if (!string.IsNullOrEmpty(suggestedUser))
        {
            context.ProtocolMessage.LoginHint = suggestedUser;
        }
    };
});
```

#### Use cases

**E-commerce Platform:**

```csharp
// Pre-fill returning customer email
loginHint = customerEmail
```

**B2B Application:**

```csharp
// Direct to customer's tenant
domainHint = customerDomain
```

**Multi-Tenant SaaS:**

```csharp
// Route based on subdomain
domainHint = GetTenantFromSubdomain(Request.Host)
```

---

## Follow best practices

### Do's

**1. Always preserve existing event handlers.** Save and call the existing handler before running your custom logic:

```csharp
var existingHandler = options.Events.OnTokenValidated;
options.Events.OnTokenValidated = async context =>
{
    await existingHandler(context); // Call Microsoft.Identity.Web's handler
    // Your custom code
};
```

**2. Use correlation IDs for tracing.** Attach a correlation ID to token acquisition requests for diagnostics:

```csharp
var tokenOptions = new TokenAcquisitionOptions
{
    CorrelationId = Activity.Current?.Id ?? Guid.NewGuid()
};
```

**3. Validate custom claims.** Verify that custom claims contain expected values before granting access:

```csharp
var department = context.Principal.FindFirst("department")?.Value;
if (!IsValidDepartment(department))
{
    throw new UnauthorizedAccessException("Invalid department");
}
```

**4. Log customization errors.** Wrap custom logic in try-catch blocks and log errors:

```csharp
try
{
    // Custom logic
}
catch (Exception ex)
{
    logger.LogError(ex, "Custom authentication logic failed");
    throw;
}
```

**5. Test both success and failure paths.** Cover all authentication scenarios in your tests:

```csharp
// Test with valid tokens
// Test with missing claims
// Test with expired tokens
// Test with wrong audience
```

### Don'ts

**1. Don't skip Microsoft.Identity.Web's event handlers:**

```csharp
//  Wrong - loses built-in security checks
options.Events.OnTokenValidated = async context => { /* your code */ };

//  Correct - preserves security
var existing = options.Events.OnTokenValidated;
options.Events.OnTokenValidated = async context =>
{
    await existing(context);
    /* your code */
};
```

**2. Don't enable PII logging in production:**

```csharp
//  Wrong
options.EnablePiiLogging = true; // In production!

//  Correct
if (builder.Environment.IsDevelopment())
{
    options.EnablePiiLogging = true;
}
```

**3. Don't bypass token validation:**

```csharp
//  Wrong - insecure!
options.TokenValidationParameters.ValidateLifetime = false;
options.TokenValidationParameters.ValidateAudience = false;

//  Correct - maintain security
options.TokenValidationParameters.ValidateLifetime = true;
options.TokenValidationParameters.ClockSkew = TimeSpan.FromMinutes(5);
```

**4. Don't hardcode sensitive values:**

```csharp
//  Wrong
options.ClientSecret = "mysecret123";

//  Correct
options.ClientSecret = builder.Configuration["AzureAd:ClientSecret"];
```

**5. Don't modify authentication in middleware:**

```csharp
//  Wrong - configure in Startup, not middleware
app.Use(async (context, next) =>
{
    // Modifying auth options here is too late!
});
```

---

## Troubleshoot common issues

### Resolve customization not taking effect

**Check execution order:**

1. `AddMicrosoftIdentityWebApp` / `AddMicrosoftIdentityWebApi` sets defaults
2. Your `Configure` calls run
3. `PostConfigure` calls run \(if any\)
4. Options are used

**Solution:** Use `PostConfigure` if your `Configure` call isn't taking effect, because `PostConfigure` runs after all `Configure` calls:

```csharp
services.PostConfigure<OpenIdConnectOptions>(
    OpenIdConnectDefaults.AuthenticationScheme,
    options => { /* your changes */ }
);
```

### Fix missing custom claims

Verify the following if custom claims don't appear:

1. The `OnTokenValidated` handler is chained correctly with the existing handler.
2. Authentication succeeds before your code adds claims.
3. Claims are added to the correct `ClaimsIdentity`.

The following code logs all claims for debugging:

```csharp
var claims = context.Principal.Claims.ToList();
logger.LogInformation($"Claims count: {claims.Count}");
foreach (var claim in claims)
{
    logger.LogInformation($"{claim.Type}: {claim.Value}");
}
```

### Fix events not firing

If events aren't firing, verify that the authentication and authorization middleware are registered in the correct order:

```csharp
app.UseAuthentication(); // Must be first
app.UseAuthorization();  // Must be second
app.MapControllers();    // Then endpoints
```

## Related content

- [Authorization](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)
- [Logging and Diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging)
- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Quickstart: Web app](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp)
