<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Quickstart: Protect an ASP.NET Core Web API

In this quickstart, you protect an ASP.NET Core web API with Microsoft Entra ID using Microsoft.Identity.Web. You add authentication middleware that validates bearer tokens and restricts access to authorized callers.

If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.

## Prerequisites

- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- A Microsoft Entra ID tenant. If you don't have one, [create a free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- An app registration for your API

## Option 1: Create from template \(fastest\)

Use the ASP.NET Core template with built-in Microsoft Entra authentication to scaffold a protected API project.

### 1. Create the project

Run the following commands to create a new web API project with single-organization authentication and navigate into the project directory:

```bash
dotnet new webapi --auth SingleOrg --name MyWebApi
cd MyWebApi
```

### 2. Configure app registration

Replace the placeholder values in `appsettings.json` with your Microsoft Entra app registration details:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-api-client-id"
  }
}
```

### 3. Run the API

Start the application:

```bash
dotnet run
```

Your API is now protected at `https://localhost:5001`.

**Done!** Requests now require a valid access token.

---

## Option 2: Add to existing Web API

If you already have an ASP.NET Core web API, add Microsoft Entra authentication with the following steps.

### 1. Install NuGet package

Add the Microsoft.Identity.Web NuGet package to your project:

```bash
dotnet add package Microsoft.Identity.Web
```

### 2. Configure authentication in `Program.cs`

Register the authentication and authorization services in your app's startup pipeline. The following code configures JWT bearer authentication with Microsoft Entra validation:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// Add authentication
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
                .AddMicrosoftIdentityWebApi(builder.Configuration, "AzureAd");

// Add authorization
builder.Services.AddAuthorization();

builder.Services.AddControllers();

var app = builder.Build();

app.UseHttpsRedirection();

app.UseAuthentication(); //  Add authentication middleware
app.UseAuthorization();

app.MapControllers();

app.Run();
```

### 3. Add configuration to `appsettings.json`

Add the Microsoft Entra configuration section with your tenant and application details. Set the logging level for `Microsoft.Identity.Web` to `Information` to help troubleshoot token validation issues:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-api-client-id"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.Identity.Web": "Information"
    }
  }
}
```

### 4. Protect your API endpoints

Apply the `[Authorize]` attribute to controllers or actions that require a valid access token.

**Require authentication for all endpoints:**

The following controller requires a valid access token for all actions and shows how to access user claims:

```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;

[Authorize] //  Require valid access token
[ApiController]
[Route("api/[controller]")]
public class WeatherForecastController : ControllerBase
{
    [HttpGet]
    public IEnumerable<WeatherForecast> Get()
    {
        // Access user information
        var userId = User.FindFirst("oid")?.Value;
        var userName = User.Identity?.Name;

        return Enumerable.Range(1, 5).Select(index => new WeatherForecast
        {
            Date = DateOnly.FromDateTime(DateTime.Now.AddDays(index)),
            TemperatureC = Random.Shared.Next(-20, 55),
            Summary = "Protected data"
        });
    }
}
```

**Require specific scopes:**

Use the `[RequiredScope]` attribute to enforce fine-grained permissions on individual actions:

```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Identity.Web;

[Authorize]
[ApiController]
[Route("api/[controller]")]
public class TodoController : ControllerBase
{
    [HttpGet]
    [RequiredScope("access_as_user")] //  Require specific scope
    public IActionResult GetAll()
    {
        return Ok(new[] { "Todo 1", "Todo 2" });
    }

    [HttpPost]
    [RequiredScope("write")] //  Different scope for write operations
    public IActionResult Create([FromBody] string item)
    {
        return Created("", item);
    }
}
```

### 5. Run and test

Start the application and verify that unauthenticated requests are rejected:

```bash
dotnet run
```

Test with a tool like Postman or curl. An unauthenticated request returns `401 Unauthorized`:

```bash
curl -H "Authorization: Bearer YOUR_ACCESS_TOKEN" https://localhost:5001/api/weatherforecast
```

**Success!** Your API now validates bearer tokens.

---

## App registration setup

Before your API can validate tokens, you need a Microsoft Entra app registration. Follow these steps in the Azure portal.

### 1. Register your API

1. Sign in to the [Azure portal](https://portal.azure.com)
2. Navigate to **Microsoft Entra ID** > **App registrations** > **New registration**
3. Enter a name \(e.g., "My Web API"\)
4. Select **Single tenant** \(most common for APIs\)
5. No redirect URI needed for APIs
6. Click **Register**

### 2. Expose an API scope

Define the permissions \(scopes\) that client apps can request when calling your API.

1. In your API app registration, go to **Expose an API**
2. Click **Add a scope**
3. Accept the default Application ID URI or customize it \(e.g., `api://your-api-client-id`\)
4. Add a scope:

   - **Scope name:** `access_as_user`
   - **Who can consent:** Admins and users
   - **Admin consent display name:** "Access My Web API"
   - **Admin consent description:** "Allows the app to access the web API on behalf of the signed-in user"

5. Click **Add scope**

### 3. Note the application ID

Copy the **Application \(client\) ID** from the app registration overview page. This value is your `ClientId` in `appsettings.json`.

---

## Create a client app registration \(for testing\)

To test your protected API, register a separate client application that acquires tokens and calls the API.

### 1. Register a client application

1. In **Microsoft Entra ID** > **App registrations**, create another registration
2. Name it \(e.g., "My API Client"\)
3. Select account types
4. Add redirect URI: `https://localhost:7000/signin-oidc` \(if it's a web app\)
5. Click **Register**

### 2. Grant API permissions

Grant the client application permission to call your API with the scopes you defined.

1. In the client app registration, go to **API permissions**
2. Click **Add a permission** > **My APIs**
3. Select your API registration
4. Check the `access_as_user` scope
5. Click **Add permissions**
6. Click **Grant admin consent** \(if required\)

### 3. Create a client secret \(for confidential clients\)

If your client app runs on a server \(not a browser or mobile device\), create a client secret for authentication.

1. Go to **Certificates & secrets**
2. Click **New client secret**
3. Add a description and expiration
4. Click **Add**
5. **Copy the secret value immediately** - you won't be able to see it again

---

## Test your protected API

Verify that your API correctly validates tokens by sending authenticated requests.

### Using Postman

Set up OAuth 2.0 authentication in Postman to acquire a token and call your API.

1. Create a new request in Postman
2. Set up OAuth 2.0 authentication:

   - **Grant Type:** Authorization Code \(for user context\) or Client Credentials \(for app context\)
   - **Auth URL:** `https://login.microsoftonline.com/{tenant-id}/oauth2/v2.0/authorize`
   - **Access Token URL:** `https://login.microsoftonline.com/{tenant-id}/oauth2/v2.0/token`
   - **Client ID:** Your client app's client ID
   - **Client Secret:** Your client app's secret
   - **Scope:** `api://your-api-client-id/access_as_user`

3. Click **Get New Access Token**
4. Use the token to call your API

### Using code \(C# example\)

The following example uses MSAL.NET to acquire a token with the client credentials flow and call the protected API:

```csharp
// In a console app or client application
using Microsoft.Identity.Client;

var app = ConfidentialClientApplicationBuilder
    .Create("client-app-id")
    .WithClientSecret("client-secret")
    .WithAuthority("https://login.microsoftonline.com/{tenant-id}")
    .Build();

var result = await app.AcquireTokenForClient(
    new[] { "api://your-api-client-id/.default" }
).ExecuteAsync();

var accessToken = result.AccessToken;

// Use the token to call your API
using var client = new HttpClient();
client.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", accessToken);

var response = await client.GetAsync("https://localhost:5001/api/weatherforecast");
```

---

## Common configuration options

Microsoft.Identity.Web supports several configuration patterns for different scenarios.

### Require specific scopes in configuration

Instead of using the `[RequiredScope]` attribute, you can configure required scopes globally in `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-api-client-id",
    "Scopes": "access_as_user"
  }
}
```

### Accept tokens from multiple tenants

To accept tokens from any Microsoft Entra tenant, set `TenantId` to `common`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "common",
    "ClientId": "your-api-client-id"
  }
}
```

### Configure token validation

If your API calls downstream APIs \(such as Microsoft Graph\), enable token acquisition and configure a token cache:

```csharp
builder.Services.AddMicrosoftIdentityWebApiAuthentication(builder.Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi() // If your API calls other APIs
    .AddInMemoryTokenCaches();
```

---

## Next steps

Now that you have a protected API, explore these topics:

- [Call downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis) - Call Microsoft Graph or other APIs on behalf of users.
- [Configure token cache](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview) - Production cache strategies for OBO scenarios.
- [Long-running processes](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis#handle-long-running-processes-with-obo) - Handle background jobs with OBO tokens.
- [Deploy behind an API gateway](https://learn.microsoft.com/en-us/entra/msidweb/advanced/api-gateways) - Azure API Management, Azure Front Door, Application Gateway.

## Troubleshooting

### 401 Unauthorized

**Problem:** API returns 401 even with a token.

**Possible causes:**

- Token audience \(`aud` claim\) doesn't match your API's `ClientId`
- Token is expired
- Token is for the wrong tenant
- Required scope is missing

**Solution:** Decode the token at [jwt.ms](https://jwt.ms) and verify the claims. See [Logging & Diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging) for detailed troubleshooting.

### AADSTS50013: Invalid signature

**Problem:** Token signature validation fails.

**Solution:** Ensure your `TenantId` and `ClientId` are correct. The token must be issued by the expected authority. Enable detailed logging to see validation errors.

### Scopes not found in token

**Problem:** `[RequiredScope]` attribute fails.

**Solution:**

1. Verify the client app has permission to the scope
2. Ensure admin consent was granted \(if required\)
3. See [Authorization Guide](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization) for complete scope validation patterns
4. Check that the scope is requested when acquiring the token \(e.g., `api://your-api/.default` or specific scopes\)

**See more:** [Web API Troubleshooting Guide](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis#troubleshoot-common-errors)

---

## Related content

- [Authorization guide](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization) - RequiredScope attribute, authorization policies, tenant filtering
- [Customization guide](https://learn.microsoft.com/en-us/entra/msidweb/advanced/customization) - Configure JWT bearer options and validation parameters
- [Logging and diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging) - Troubleshoot authentication issues with correlation IDs
- [Protected web API tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-api-aspnet-core-protect-api)
- [API samples](https://github.com/Azure-Samples/active-directory-dotnet-native-aspnetcore-v2)
