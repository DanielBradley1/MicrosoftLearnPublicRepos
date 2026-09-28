<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Quickstart: Sign in users in an ASP.NET Core web app

In this quickstart, you create an ASP.NET Core web app that signs in users with Microsoft Entra ID using Microsoft.Identity.Web. You can either scaffold a new project from a template or add authentication to an existing app.

If you don't have a Microsoft Entra tenant, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.

## Prerequisites

- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0)
- A Microsoft Entra ID tenant
- An app registration in your Microsoft Entra tenant. If you need to create one, see [Register your application](#register-your-application).

## Create a project from the template

The fastest way to get started is to scaffold a new project with authentication preconfigured.

Run the following commands to create a new web app with single-organization authentication and navigate into the project directory:

```bash
dotnet new webapp --auth SingleOrg --name MyWebApp
cd MyWebApp
```

The template generates a project with Microsoft.Identity.Web already configured. You only need to supply your app registration details.

Open `appsettings.json` and replace the placeholder values with the **Application \(client\) ID** and **Directory \(tenant\) ID** from your app registration:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "CallbackPath": "/signin-oidc"
  }
}
```

Start the application to verify that sign-in works:

```bash
dotnet run
```

Navigate to `https://localhost:5001` and select **Sign in**. If a Microsoft sign-in prompt appears, the configuration is correct.

## Add authentication to an existing web app

If you have an existing ASP.NET Core app, follow these steps to add Microsoft Entra sign-in.

### Install NuGet packages

Add the Microsoft.Identity.Web libraries. The `Microsoft.Identity.Web` package handles authentication, and `Microsoft.Identity.Web.UI` provides prebuilt sign-in and sign-out UI components:

```bash
dotnet add package Microsoft.Identity.Web
dotnet add package Microsoft.Identity.Web.UI
```

### Configure authentication services

Open `Program.cs` and add the authentication services. The following code registers OpenID Connect authentication with Microsoft Entra, enables token acquisition for downstream API calls, and adds the sign-in/sign-out UI:

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.UI;

var builder = WebApplication.CreateBuilder(args);

// Add authentication
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
                .AddMicrosoftIdentityWebApp(builder.Configuration, "AzureAd")
                .EnableTokenAcquisitionToCallDownstreamApi() // Optional: if calling APIs
                .AddInMemoryTokenCaches(); // For production, use distributed cache

// Add Razor Pages or MVC
builder.Services.AddRazorPages()
    .AddMicrosoftIdentityUI(); // Adds sign-in/sign-out UI

var app = builder.Build();

// Configure middleware
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();
app.UseRouting();

app.UseAuthentication(); //  Add authentication middleware
app.UseAuthorization();

app.MapRazorPages();
app.MapControllers();

app.Run();
```

### Add Microsoft Entra configuration

Open `appsettings.json` and add the `AzureAd` section. Replace the placeholder values with your app registration's **Application \(client\) ID**. Set `TenantId` to the appropriate audience for your app:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "common",
    "ClientId": "your-client-id-from-app-registration",
    "CallbackPath": "/signin-oidc"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.Identity.Web": "Information"
    }
  }
}
```

The `TenantId` value determines which accounts can sign in:

| Value | Accepted accounts |
| --- | --- |
| `common` | Work/school and personal Microsoft accounts |
| `organizations` | Work/school accounts only |
| `consumers` | Personal Microsoft accounts only |
| `<your-tenant-id>` | Single-tenant — your organization only |

### Protect your pages

Add the `[Authorize]` attribute to pages or controllers that require sign-in.

For Razor Pages, the `[Authorize]` attribute redirects unauthenticated users to the sign-in page. After sign-in, user claims like `Name` and `preferred_username` are available through the `User` object:

```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc.RazorPages;

[Authorize] //  Require authentication
public class IndexModel : PageModel
{
    public void OnGet()
    {
        var userName = User.Identity?.Name;
        var userEmail = User.FindFirst("preferred_username")?.Value;
    }
}
```

For MVC controllers, the same `[Authorize]` attribute applies at the controller or action level:

```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;

[Authorize] //  Require authentication
public class HomeController : Controller
{
    public IActionResult Index()
    {
        var userName = User.Identity?.Name;
        return View();
    }
}
```

### Add sign-in and sign-out links

Add navigation links to your layout so users can sign in and out. The `MicrosoftIdentity` area routes are provided by the `Microsoft.Identity.Web.UI` package. The following Razor markup conditionally renders **Sign out** or **Sign in** based on the user's authentication state:

```html
<ul class="navbar-nav">
    @if (User.Identity?.IsAuthenticated == true)
    {
        <li class="nav-item">
            <span class="nav-link">Hello @User.Identity.Name!</span>
        </li>
        <li class="nav-item">
            <a class="nav-link" asp-area="MicrosoftIdentity" asp-controller="Account" asp-action="SignOut">Sign out</a>
        </li>
    }
    else
    {
        <li class="nav-item">
            <a class="nav-link" asp-area="MicrosoftIdentity" asp-controller="Account" asp-action="SignIn">Sign in</a>
        </li>
    }
</ul>
```

### Run and test

Start the application to verify that authentication works:

```bash
dotnet run
```

Navigate to `https://localhost:5001`. You should see a **Sign in** link. Select it to confirm the Microsoft sign-in flow completes successfully.

## Register your application

If you don't already have an app registration, follow these steps to create one in the Azure portal.

1. Sign in to the Azure portal.
2. Navigate to **Microsoft Entra ID** > **App registrations** > **New registration**.
3. Enter a display name \(for example, "My Web App"\).
4. Select supported account types:

   - **Single tenant** — Users in your organization only
   - **Multi-tenant** — Users in any organization
   - **Multi-tenant + personal** — All Microsoft accounts

5. Under **Redirect URI**, set the platform to **Web** and enter `https://localhost:5001/signin-oidc`.
6. Select **Register**.
7. On the overview page, copy the **Application \(client\) ID** and the **Directory \(tenant\) ID**. You need these values for the `ClientId` and `TenantId` fields in `appsettings.json`.

### Configure optional settings

Your scenario might require these additional settings.

**Enable ID token issuance** — Some hybrid authentication scenarios require ID tokens to be issued directly from the authorization endpoint. The authorization code flow \(used by Microsoft.Identity.Web\) is the recommended approach. Only enable this setting if your scenario specifically requires it:

1. In your app registration, go to **Authentication**.
2. Under **Implicit grant and hybrid flows**, select **ID tokens**.
3. Select **Save**.

Note

The implicit grant flow is a legacy flow. Microsoft recommends the authorization code flow with PKCE for all new applications. For more information, see the [Microsoft identity platform documentation](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow).

**Configure front-channel logout URL** — Ensures users are signed out of your app when they sign out of Microsoft Entra:

1. In your app registration, go to **Authentication**.
2. Under **Front-channel logout URL**, enter `https://localhost:5001/signout-oidc`.
3. Select **Save**.

## Troubleshoot common errors

If you encounter issues during sign-in, check for these common errors.

| Error | Cause | Solution |
| --- | --- | --- |
| AADSTS50011: No reply address registered | Redirect URI mismatch between code and app registration | Verify that the redirect URI in your app registration matches `CallbackPath` \(`/signin-oidc` by default\) |
| AADSTS700016: Application not found | Incorrect `ClientId` in configuration | Confirm that the **Application \(client\) ID** in `appsettings.json` matches your app registration |
| Authority configuration error | Missing or invalid `Instance` or `TenantId` | Set `Instance` to `https://login.microsoftonline.com/` and confirm `TenantId` is valid |

## Related content

- [Calling downstream APIs from web apps](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apps)
- [Authorization](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)
- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Quickstart: Web API](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi)
