<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Implement authorization in web APIs with Microsoft.Identity.Web

In this article, you implement authorization in ASP.NET Core web APIs using Microsoft.Identity.Web. You'll validate **scopes** \(delegated permissions\) and **app permissions** \(application permissions\) to control access to protected resources. The examples use Microsoft Entra ID as the identity provider.

## Understand authorization concepts

This section covers the key differences between authentication and authorization, and describes what Microsoft.Identity.Web validates in access tokens.

### Authentication vs authorization

| Concept | Purpose | Result |
| --- | --- | --- |
| **Authentication** | Verify identity | 401 Unauthorized if fails |
| **Authorization** | Verify permissions | 403 Forbidden if insufficient |

### What gets validated

When a web API receives an access token, Microsoft.Identity.Web validates:

1. **Token signature** - Is it from a trusted authority?
2. **Token audience** - Is it intended for this API?
3. **Token expiration** - Is it still valid?
4. **Scopes/Roles** - Does the client app and the subject \(user\) have the right permissions?

This guide focuses on **#4 - validating scopes and app permissions**.

### Scopes \(delegated permissions\)

Scopes apply when a user delegates permission to an app to act on their behalf \(for example, a web API called on behalf of a signed-in user\).

| Detail | Value |
| --- | --- |
| **Token claim** | `scp` or `scope` \(client app\); `roles` \(user\) |
| **Example values** | `"access_as_user"`, `"User.Read"`, `"Files.ReadWrite"` |

### App permissions \(application permissions\)

App permissions apply when an app calls the web API as itself with no user context, such as a daemon or background service using client credentials.

| Detail | Value |
| --- | --- |
| **Token claim** | `roles` |
| **Example values** | `"Mail.Read.All"`, `"User.Read.All"` |

---

## Validate scopes with RequiredScope

The `RequiredScope` attribute checks that the access token contains at least one of the specified scopes. Use this attribute when your API serves only user-delegated requests.

### Set up scope validation

Follow these steps to enable scope validation in your API.

**1. Enable authorization in your API:**

Add authentication and authorization services to your application pipeline:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddAuthorization(); // Required for authorization

var app = builder.Build();

app.UseAuthentication();
app.UseAuthorization(); // Must be after UseAuthentication
app.MapControllers();

app.Run();
```

**2. Protect controllers or actions:**

Apply the `[Authorize]` and `[RequiredScope]` attributes to your controller or individual actions:

```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.Identity.Web.Resource;

[Authorize]
[RequiredScope("access_as_user")]
public class TodoListController : ControllerBase
{
    [HttpGet]
    public IActionResult GetTodos()
    {
        // Only accessible if token has "access_as_user" scope
        return Ok(new[] { "Todo 1", "Todo 2" });
    }
}
```

### Apply scope patterns

Choose the pattern that best fits how you manage scopes in your application.

#### Pattern 1: Hardcoded scopes

Use this pattern when scopes are fixed and known at development time.

```csharp
[Authorize]
[RequiredScope("access_as_user")]
public class TodoListController : ControllerBase
{
    // All actions require "access_as_user" scope
}
```

To accept any one of multiple scopes, list them as parameters:

```csharp
[Authorize]
[RequiredScope("read", "write", "admin")]
public class TodoListController : ControllerBase
{
    // Token must have "read" OR "write" OR "admin"
}
```

#### Pattern 2: Scopes from configuration

Use this pattern when scopes should be configurable per environment. Define the scopes in your configuration file:

**appsettings.json:**

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-api-client-id",
    "Scopes": "access_as_user read write"
  }
}
```

Reference the configuration key in your controller:

```csharp
[Authorize]
[RequiredScope(RequiredScopesConfigurationKey = "AzureAd:Scopes")]
public class TodoListController : ControllerBase
{
    // Scopes read from configuration
}
```

This approach lets you change scopes without recompiling.

#### Pattern 3: Action-level scopes

Use this pattern when different actions require different permissions. Apply `[RequiredScope]` to individual action methods:

```csharp
[Authorize]
public class TodoListController : ControllerBase
{
    [HttpGet]
    [RequiredScope("read")]
    public IActionResult GetTodos()
    {
        return Ok(todos);
    }

    [HttpPost]
    [RequiredScope("write")]
    public IActionResult CreateTodo([FromBody] Todo todo)
    {
        // Only tokens with "write" scope can create
        return CreatedAtAction(nameof(GetTodos), todo);
    }

    [HttpDelete("{id}")]
    [RequiredScope("admin")]
    public IActionResult DeleteTodo(int id)
    {
        // Only tokens with "admin" scope can delete
        return NoContent();
    }
}
```

### Understand the validation flow

When a request arrives, the middleware processes it in the following order:

1. ASP.NET Core authentication middleware validates the token
2. `RequiredScope` attribute checks for the `scp` or `scope` claim
3. If the token contains at least one matching scope, the request proceeds.
4. If no matching scope is found, the API returns a 403 Forbidden response.

The following example shows a typical error response:

```json
{
  "error": "insufficient_scope",
  "error_description": "The token does not have the required scope 'access_as_user'."
}
```

---

## Validate app permissions with RequiredScopeOrAppPermission

The `RequiredScopeOrAppPermission` attribute validates either **scopes** \(delegated\) or **app permissions** \(application\). Use this attribute when your API serves both user-delegated apps and daemon/service apps from the same endpoint.

If your API only serves user-delegated requests, use `RequiredScope` instead.

### Set up scope or app permission validation

Apply the attribute to accept either token type:

```csharp
using Microsoft.Identity.Web.Resource;

[Authorize]
[RequiredScopeOrAppPermission(
    AcceptedScope = new[] { "access_as_user" },
    AcceptedAppPermission = new[] { "TodoList.ReadWrite.All" }
)]
public class TodoListController : ControllerBase
{
    [HttpGet]
    public IActionResult GetTodos()
    {
        // Accessible with EITHER:
        // - User-delegated token with "access_as_user" scope, OR
        // - App-only token with "TodoList.ReadWrite.All" app permission
        return Ok(todos);
    }
}
```

### Configure app permissions from settings

Store scopes and app permissions in configuration to change them without recompiling.

**appsettings.json:**

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-api-client-id",
    "Scopes": "access_as_user",
    "AppPermissions": "TodoList.ReadWrite.All TodoList.Admin"
  }
}
```

Reference the configuration keys in your controller:

```csharp
[Authorize]
[RequiredScopeOrAppPermission(
    RequiredScopesConfigurationKey = "AzureAd:Scopes",
    RequiredAppPermissionsConfigurationKey = "AzureAd:AppPermissions"
)]
public class TodoListController : ControllerBase
{
    // Scopes and app permissions from configuration
}
```

### Compare token claim differences

The following table shows how claims differ between user-delegated and app-only tokens:

| Token Type | Claim | Example Value |
| --- | --- | --- |
| **User-delegated** | `scp` or `scope` | `"access_as_user User.Read"` |
| **App-only** | `roles` | `["TodoList.ReadWrite.All"]` |

The following example shows a user-delegated token:

```json
{
  "aud": "api://your-api-client-id",
  "iss": "https://login.microsoftonline.com/.../v2.0",
  "scp": "access_as_user",
  "sub": "user-object-id",
  ...
}
```

The following example shows an app-only token:

```json
{
  "aud": "api://your-api-client-id",
  "iss": "https://login.microsoftonline.com/.../v2.0",
  "roles": ["TodoList.ReadWrite.All"],
  "sub": "app-object-id",
  ...
}
```

---

## Create authorization policies

For complex authorization scenarios, use ASP.NET Core authorization policies. Policies let you centralize rules, combine multiple requirements, and write testable authorization logic.

| Benefit | Description |
| --- | --- |
| **Centralized logic** | Define authorization rules once, reuse everywhere |
| **Composable** | Combine multiple requirements \(scopes + claims + custom logic\) |
| **Testable** | Easier to unit test authorization logic |
| **Flexible** | Custom requirements beyond scope validation |

### Pattern 1: Define a policy with RequireScope

Define named policies that require specific scopes, then reference them on your controllers:

```csharp
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("TodoReadPolicy", policyBuilder =>
    {
        policyBuilder.RequireScope("read", "access_as_user");
    });

    options.AddPolicy("TodoWritePolicy", policyBuilder =>
    {
        policyBuilder.RequireScope("write", "admin");
    });
});

var app = builder.Build();
```

Apply the policies to controller actions:

```csharp
[Authorize]
public class TodoListController : ControllerBase
{
    [HttpGet]
    [Authorize(Policy = "TodoReadPolicy")]
    public IActionResult GetTodos()
    {
        return Ok(todos);
    }

    [HttpPost]
    [Authorize(Policy = "TodoWritePolicy")]
    public IActionResult CreateTodo([FromBody] Todo todo)
    {
        return CreatedAtAction(nameof(GetTodos), todo);
    }
}
```

### Pattern 2: Define a policy with ScopeAuthorizationRequirement

Use `ScopeAuthorizationRequirement` for more explicit scope requirements:

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.Resource;

builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("CustomPolicy", policyBuilder =>
    {
        policyBuilder.AddRequirements(
            new ScopeAuthorizationRequirement(new[] { "access_as_user" })
        );
    });
});
```

### Pattern 3: Set a default policy

Set a default policy that applies to all `[Authorize]` attributes automatically:

```csharp
builder.Services.AddAuthorization(options =>
{
    var defaultPolicy = new AuthorizationPolicyBuilder()
        .RequireScope("access_as_user")
        .Build();

    options.DefaultPolicy = defaultPolicy;
});
```

Every `[Authorize]` attribute now requires the `access_as_user` scope:

```csharp
[Authorize] // Automatically requires "access_as_user" scope
public class TodoListController : ControllerBase
{
    // All actions protected by default policy
}
```

### Pattern 4: Combine multiple requirements

Combine scope, role, and authentication requirements in a single policy:

```csharp
builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("AdminPolicy", policyBuilder =>
    {
        policyBuilder.RequireScope("admin");
        policyBuilder.RequireRole("Admin"); // Also check role claim
        policyBuilder.RequireAuthenticatedUser();
    });
});
```

### Pattern 5: Build a policy from configuration

Load scopes from configuration to keep policies environment-specific:

```csharp
var requiredScopes = builder.Configuration["AzureAd:Scopes"]?.Split(' ');

builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("ApiAccessPolicy", policyBuilder =>
    {
        if (requiredScopes != null)
        {
            policyBuilder.RequireScope(requiredScopes);
        }
    });
});
```

---

## Filter requests by tenant

Restrict API access to tokens from specific Microsoft Entra tenants. This is useful when your multi-tenant API should only accept requests from approved customer tenants.

### Restrict access to allowed tenants

Define a policy that checks the tenant ID claim against an allowlist:

```csharp
builder.Services.AddAuthorization(options =>
{
    string[] allowedTenants =
    {
        "14c2f153-90a7-4689-9db7-9543bf084dad", // Contoso tenant
        "af8cc1a0-d2aa-4ca7-b829-00d361edb652", // Fabrikam tenant
        "979f4440-75dc-4664-b2e1-2cafa0ac67d1"  // Northwind tenant
    };

    options.AddPolicy("AllowedTenantsOnly", policyBuilder =>
    {
        policyBuilder.RequireClaim(
            "http://schemas.microsoft.com/identity/claims/tenantid",
            allowedTenants
        );
    });

    // Apply to all endpoints by default
    options.DefaultPolicy = options.GetPolicy("AllowedTenantsOnly");
});
```

### Configure tenant filtering from settings

Store allowed tenant IDs in configuration to manage them without code changes.

**appsettings.json:**

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "ClientId": "your-api-client-id",
    "AllowedTenants": [
      "14c2f153-90a7-4689-9db7-9543bf084dad",
      "af8cc1a0-d2aa-4ca7-b829-00d361edb652"
    ]
  }
}
```

Read the tenant list and create the policy at startup:

```csharp
var allowedTenants = builder.Configuration.GetSection("AzureAd:AllowedTenants")
    .Get<string[]>();

builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("AllowedTenantsOnly", policyBuilder =>
    {
        policyBuilder.RequireClaim(
            "http://schemas.microsoft.com/identity/claims/tenantid",
            allowedTenants ?? Array.Empty<string>()
        );
    });
});
```

### Combine scopes with tenant filtering

Create a policy that requires both a valid scope and an approved tenant:

```csharp
builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("SecureApiAccess", policyBuilder =>
    {
        // Require specific scope
        policyBuilder.RequireScope("access_as_user");

        // AND require specific tenant
        policyBuilder.RequireClaim(
            "http://schemas.microsoft.com/identity/claims/tenantid",
            allowedTenants
        );
    });
});
```

---

## Follow best practices

Apply these recommendations to build secure, maintainable authorization logic.

### Do's

**1. Always pair `[Authorize]` with scope validation:**

```csharp
[Authorize] // Authentication
[RequiredScope("access_as_user")] // Authorization
public class MyController : ControllerBase { }
```

**2. Use configuration for environment-specific scopes:**

```csharp
[RequiredScope(RequiredScopesConfigurationKey = "AzureAd:Scopes")]
```

**3. Apply least privilege:**

```csharp
[HttpGet]
[RequiredScope("read")] // Only read permission needed

[HttpPost]
[RequiredScope("write")] // Write permission for modifications
```

**4. Use policies for complex authorization:**

```csharp
builder.Services.AddAuthorization(options =>
{
    options.AddPolicy("AdminOnly", policy =>
    {
        policy.RequireScope("admin");
        policy.RequireClaim("department", "IT");
    });
});
```

**5. Enable detailed error responses in development:**

```csharp
if (builder.Environment.IsDevelopment())
{
    Microsoft.IdentityModel.Logging.IdentityModelEventSource.ShowPII = true;
}
```

### Don'ts

**1. Don't skip `[Authorize]` when using `RequiredScope`:**

```csharp
//  Wrong - RequiredScope won't work without [Authorize]
[RequiredScope("access_as_user")]
public class MyController : ControllerBase { }

//  Correct
[Authorize]
[RequiredScope("access_as_user")]
public class MyController : ControllerBase { }
```

**2. Don't hardcode tenant IDs in production:**

```csharp
//  Wrong
policyBuilder.RequireClaim("tid", "14c2f153-90a7-4689-9db7-9543bf084dad");

//  Better - use configuration
var tenants = Configuration.GetSection("AllowedTenants").Get<string[]>();
policyBuilder.RequireClaim("tid", tenants);
```

**3. Don't confuse scopes with roles:**

```csharp
//  Wrong - This checks roles claim, not scopes
[RequiredScope("Admin")] // "Admin" is typically a role, not a scope

//  Correct
[RequiredScope("access_as_user")] // Scope
[Authorize(Roles = "Admin")] // Role
```

**4. Don't expose sensitive scope information in production error messages:**

Configure appropriate logging levels and error handling for production environments.

---

## Troubleshoot authorization issues

Use the following guidance to diagnose common authorization problems.

### 403 Forbidden - missing scope

**Error:** API returns 403 even with a valid token.

**Diagnosis:**

1. Decode the token at [jwt.ms](https://jwt.ms).
2. Check the `scp` or `scope` claim.
3. Verify the value matches your `RequiredScope` attribute.

**Solution:**

- Ensure the client app requests the correct scope when acquiring the token.
- Verify the scope is exposed in the API app registration in Microsoft Entra.
- Grant admin consent if required.

### RequiredScope not working

**Symptom:** The attribute appears to be ignored.

**Check:**

1. Did you add the `[Authorize]` attribute?
2. Is `app.UseAuthorization()` called after `app.UseAuthentication()`?
3. Is `services.AddAuthorization()` registered?

### Configuration key not found

**Error:** Scope validation fails silently.

**Check:**

```json
{
  "AzureAd": {
    "Scopes": "access_as_user" // Matches RequiredScopesConfigurationKey
  }
}
```

Ensure the configuration path matches exactly.

## Related content

- [Quickstart: Web API](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi)
- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Customization](https://learn.microsoft.com/en-us/entra/msidweb/advanced/customization)
