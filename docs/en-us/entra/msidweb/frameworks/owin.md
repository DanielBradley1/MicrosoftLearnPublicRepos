<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/frameworks/owin -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Integrate OWIN with Microsoft.Identity.Web

Add modern authentication to your ASP.NET MVC and Web API applications on .NET Framework 4.7.2+ by using the Microsoft.Identity.Web.OWIN package.

## Understand OWIN integration

The **Microsoft.Identity.Web.OWIN** package brings the power of Microsoft.Identity.Web to ASP.NET MVC and Web API applications that use OWIN middleware with Microsoft Entra ID.

### Review key benefits

The following table summarizes the key features and benefits of the package.

| Feature | Benefit |
| --- | --- |
| **TokenAcquirerFactory** | Automatic token acquisition with caching |
| **Controller Extensions** | Easy access to `GraphServiceClient` and `IDownstreamApi` |
| **Distributed Token Cache** | Built-in support for SQL Server, Redis, Cosmos DB, PostgreSQL |
| **Automatic Token Refresh** | Handles token refresh transparently |
| **Incremental Consent** | Seamless consent flow integration |

### Review supported scenarios

Microsoft.Identity.Web.OWIN supports the following application types and scenarios.

- **ASP.NET MVC Web Applications** \(.NET Framework 4.7.2+\)
- **ASP.NET Web API** \(.NET Framework 4.7.2+\)
- **Hybrid Apps** \(MVC + Web API\)
- **Calling Microsoft Graph** from controllers
- **Calling Downstream APIs** with automatic authentication

---

## Install the package

Install the Microsoft.Identity.Web.OWIN NuGet package using your preferred method.

Run the following command in the **Package Manager Console**:

```powershell
Install-Package Microsoft.Identity.Web.OWIN
```

Alternatively, run the following command with the **.NET CLI**:

```bash
dotnet add package Microsoft.Identity.Web.OWIN
```

**Dependencies automatically included:**

- Microsoft.Identity.Web.TokenAcquisition
- Microsoft.Identity.Web.TokenCache
- Microsoft.Owin
- System.Web

---

## Configure the application

Configure your application settings to connect to Microsoft Entra and downstream APIs.

### Configure Web.config

Add the following Microsoft Entra and downstream API settings to your `Web.config` file.

```xml
<configuration>
  <appSettings>
    <!-- Microsoft Entra ID Configuration -->
    <add key="AzureAd:Instance" value="https://login.microsoftonline.com/" />
    <add key="AzureAd:TenantId" value="your-tenant-id" />
    <add key="AzureAd:ClientId" value="your-client-id" />
    <add key="AzureAd:ClientSecret" value="your-client-secret" />
    <add key="AzureAd:RedirectUri" value="https://localhost:44368/" />
    <add key="AzureAd:PostLogoutRedirectUri" value="https://localhost:44368/" />

    <!-- Microsoft Graph Configuration -->
    <add key="DownstreamApi:MicrosoftGraph:BaseUrl" value="https://graph.microsoft.com/v1.0" />
    <add key="DownstreamApi:MicrosoftGraph:Scopes" value="user.read" />

    <!-- Custom Downstream API Configuration -->
    <add key="DownstreamApi:TodoListService:BaseUrl" value="https://localhost:44351" />
    <add key="DownstreamApi:TodoListService:Scopes" value="api://todo-api-client-id/.default" />
  </appSettings>

  <connectionStrings>
    <!-- Optional: SQL Server Token Cache -->
    <add name="TokenCache"
         connectionString="Data Source=(localdb)\MSSQLLocalDB;Initial Catalog=TokenCache;Integrated Security=True;" />
  </connectionStrings>
</configuration>
```

### Configure appsettings.json \(alternative\)

You can also store settings in an `appsettings.json` file as shown in the following example.

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientSecret": "your-client-secret",
    "RedirectUri": "https://localhost:44368/",
    "PostLogoutRedirectUri": "https://localhost:44368/"
  },
  "DownstreamApi": {
    "MicrosoftGraph": {
      "BaseUrl": "https://graph.microsoft.com/v1.0",
      "Scopes": "user.read"
    },
    "TodoListService": {
      "BaseUrl": "https://localhost:44351",
      "Scopes": "api://todo-api-client-id/.default"
    }
  }
}
```

---

## Set up the startup class

Register authentication middleware, token acquisition, and downstream API services in your startup class.

### Configure App\_Start/Startup.Auth.cs

The following code shows a complete setup with Microsoft.Identity.Web.OWIN:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Configuration;
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.OWIN;
using Microsoft.Identity.Web.TokenCacheProviders.Distributed;
using Microsoft.Owin.Security;
using Microsoft.Owin.Security.Cookies;
using Microsoft.Owin.Security.OpenIdConnect;
using Owin;
using System;
using System.Configuration;
using System.Web;

namespace MyMvcApp
{
    public partial class Startup
    {
        public void ConfigureAuth(IAppBuilder app)
        {
            // Set default authentication type
            app.SetDefaultSignInAsAuthenticationType(CookieAuthenticationDefaults.AuthenticationType);

            // Configure cookie authentication
            app.UseCookieAuthentication(new CookieAuthenticationOptions
            {
                CookieName = "MyApp.Auth",
                ExpireTimeSpan = TimeSpan.FromHours(1),
                SlidingExpiration = true
            });

            // Configure OpenID Connect authentication
            app.UseOpenIdConnectAuthentication(
                new OpenIdConnectAuthenticationOptions
                {
                    ClientId = ConfigurationManager.AppSettings["AzureAd:ClientId"],
                    Authority = $"https://login.microsoftonline.com/{ConfigurationManager.AppSettings["AzureAd:TenantId"]}",
                    RedirectUri = ConfigurationManager.AppSettings["AzureAd:RedirectUri"],
                    PostLogoutRedirectUri = ConfigurationManager.AppSettings["AzureAd:PostLogoutRedirectUri"],

                    Scope = "openid profile email offline_access",
                    ResponseType = "code id_token",

                    TokenValidationParameters = new TokenValidationParameters
                    {
                        ValidateIssuer = true,
                        NameClaimType = "preferred_username"
                    },

                    Notifications = new OpenIdConnectAuthenticationNotifications
                    {
                        AuthenticationFailed = context =>
                        {
                            context.HandleResponse();
                            context.Response.Redirect("/Error?message=" + context.Exception.Message);
                            return Task.FromResult(0);
                        }
                    }
                });

            // Configure Microsoft Identity Web services
            var services = CreateOwinServiceCollection();

            // Add token acquisition
            services.AddTokenAcquisition();

            // Add Microsoft Graph support
            services.AddMicrosoftGraph();

            // Add downstream API support
            services.AddDownstreamApi("MicrosoftGraph", services.BuildServiceProvider()
                .GetRequiredService<IConfiguration>().GetSection("DownstreamApi:MicrosoftGraph"));

            services.AddDownstreamApi("TodoListService", services.BuildServiceProvider()
                .GetRequiredService<IConfiguration>().GetSection("DownstreamApi:TodoListService"));

            // Configure token cache (choose one option)
            ConfigureTokenCache(services);

            // Build service provider
            var serviceProvider = services.BuildServiceProvider();

            // Create and register token acquirer factory
            var tokenAcquirerFactory = TokenAcquirerFactory.GetDefaultInstance();
            tokenAcquirerFactory.Build(serviceProvider);

            // Add OWIN token acquisition middleware
            app.Use<OwinTokenAcquisitionMiddleware>(tokenAcquirerFactory);
        }

        private IServiceCollection CreateOwinServiceCollection()
        {
            var services = new ServiceCollection();

            // Add configuration from appsettings.json and/or Web.config
            IConfiguration configuration = new ConfigurationBuilder()
                .AddJsonFile("appsettings.json", optional: true)
                .AddInMemoryCollection(new Dictionary<string, string>
                {
                    ["AzureAd:Instance"] = ConfigurationManager.AppSettings["AzureAd:Instance"],
                    ["AzureAd:TenantId"] = ConfigurationManager.AppSettings["AzureAd:TenantId"],
                    ["AzureAd:ClientId"] = ConfigurationManager.AppSettings["AzureAd:ClientId"],
                    ["AzureAd:ClientSecret"] = ConfigurationManager.AppSettings["AzureAd:ClientSecret"],
                    ["DownstreamApi:MicrosoftGraph:BaseUrl"] = ConfigurationManager.AppSettings["DownstreamApi:MicrosoftGraph:BaseUrl"],
                    ["DownstreamApi:MicrosoftGraph:Scopes"] = ConfigurationManager.AppSettings["DownstreamApi:MicrosoftGraph:Scopes"],
                })
                .Build();

            services.AddSingleton(configuration);

            return services;
        }

        private void ConfigureTokenCache(IServiceCollection services)
        {
            // Option 1: In-memory cache (development)
            services.AddDistributedTokenCaches(cacheServices =>
            {
                cacheServices.AddDistributedMemoryCache();
            });

            // Option 2: SQL Server cache (production)
            /*
            services.AddDistributedTokenCaches(cacheServices =>
            {
                cacheServices.AddDistributedSqlServerCache(options =>
                {
                    options.ConnectionString = ConfigurationManager.ConnectionStrings["TokenCache"].ConnectionString;
                    options.SchemaName = "dbo";
                    options.TableName = "TokenCache";
                    options.DefaultSlidingExpiration = TimeSpan.FromMinutes(90);
                });
            });
            */

            // Option 3: Redis cache (production, high-scale)
            /*
            services.AddDistributedTokenCaches(cacheServices =>
            {
                cacheServices.AddStackExchangeRedisCache(options =>
                {
                    options.Configuration = ConfigurationManager.AppSettings["Redis:ConnectionString"];
                    options.InstanceName = "MyMvcApp_";
                });
            });
            */
        }
    }
}
```

---

## Integrate controllers

Access Microsoft Graph and downstream APIs from your controllers by using the extension methods provided by the package.

### Integrate MVC controllers

The following example shows how to use controller extension methods to access Microsoft Graph:

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.OWIN;
using Microsoft.Graph;
using System.Threading.Tasks;
using System.Web.Mvc;

namespace MyMvcApp.Controllers
{
    [Authorize]
    public class HomeController : Controller
    {
        // GET: Home/Index
        public async Task<ActionResult> Index()
        {
            try
            {
                // Access Microsoft Graph using extension method
                var graphClient = this.GetGraphServiceClient();
                var user = await graphClient.Me.GetAsync();

                ViewBag.UserName = user.DisplayName;
                ViewBag.Email = user.Mail ?? user.UserPrincipalName;
                ViewBag.JobTitle = user.JobTitle;

                return View();
            }
            catch (MsalUiRequiredException)
            {
                // Incremental consent required
                return new ChallengeResult();
            }
            catch (Exception ex)
            {
                return View("Error", new ErrorViewModel { Message = ex.Message });
            }
        }

        // GET: Home/Profile
        public async Task<ActionResult> Profile()
        {
            var graphClient = this.GetGraphServiceClient();

            // Get user profile
            var user = await graphClient.Me
                .GetAsync(requestConfig => requestConfig.QueryParameters.Select = new[] { "displayName", "mail", "jobTitle", "department" });

            return View(user);
        }

        // GET: Home/Photo
        public async Task<ActionResult> Photo()
        {
            var graphClient = this.GetGraphServiceClient();

            try
            {
                // Get user photo
                var photoStream = await graphClient.Me.Photo.Content.GetAsync();
                return File(photoStream, "image/jpeg");
            }
            catch (ServiceException ex) when (ex.StatusCode == System.Net.HttpStatusCode.NotFound)
            {
                return File(Server.MapPath("~/Content/images/default-user.png"), "image/png");
            }
        }
    }
}
```

### Integrate Web API controllers

The following example shows how to use ApiController extension methods to call a downstream API:

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.OWIN;
using Microsoft.Identity.Abstractions;
using System.Threading.Tasks;
using System.Web.Http;

namespace MyWebApi.Controllers
{
    [Authorize]
    [RoutePrefix("api/todos")]
    public class TodoController : ApiController
    {
        // GET: api/todos
        [HttpGet]
        [Route("")]
        public async Task<IHttpActionResult> GetTodos()
        {
            try
            {
                // Call downstream API using extension method
                var downstreamApi = this.GetDownstreamApi();

                var todos = await downstreamApi.GetForUserAsync<List<TodoItem>>(
                    "TodoListService",
                    options =>
                    {
                        options.RelativePath = "api/todolist";
                    });

                return Ok(todos);
            }
            catch (MsalUiRequiredException)
            {
                return Unauthorized();
            }
            catch (HttpRequestException ex)
            {
                return InternalServerError(ex);
            }
        }

        // POST: api/todos
        [HttpPost]
        [Route("")]
        public async Task<IHttpActionResult> CreateTodo([FromBody] TodoItem todo)
        {
            var downstreamApi = this.GetDownstreamApi();

            var createdTodo = await downstreamApi.PostForUserAsync<TodoItem, TodoItem>(
                "TodoListService",
                todo,
                options =>
                {
                    options.RelativePath = "api/todolist";
                });

            return Created($"api/todos/{createdTodo.Id}", createdTodo);
        }
    }
}
```

---

## Call Microsoft Graph

Use the `GraphServiceClient` to interact with Microsoft Graph data from your controllers.

### Set up the Microsoft Graph client

The Microsoft Graph client is already configured in `Startup.Auth.cs` with the following call:

```csharp
services.AddMicrosoftGraph();
```

### Use GraphServiceClient in controllers

The following example demonstrates common Microsoft Graph operations in an MVC controller.

```csharp
[Authorize]
public class GraphController : Controller
{
    public async Task<ActionResult> MyProfile()
    {
        var graphClient = this.GetGraphServiceClient();
        var user = await graphClient.Me.GetAsync();

        return View(user);
    }

    public async Task<ActionResult> MyManager()
    {
        var graphClient = this.GetGraphServiceClient();
        var manager = await graphClient.Me.Manager.GetAsync();

        return View(manager);
    }

    public async Task<ActionResult> MyDirectReports()
    {
        var graphClient = this.GetGraphServiceClient();
        var directReports = await graphClient.Me.DirectReports.GetAsync();

        return View(directReports.Value);
    }

    public async Task<ActionResult> SendEmail([FromBody] EmailMessage message)
    {
        var graphClient = this.GetGraphServiceClient();

        var email = new Message
        {
            Subject = message.Subject,
            Body = new ItemBody
            {
                ContentType = BodyType.Text,
                Content = message.Body
            },
            ToRecipients = new[]
            {
                new Recipient
                {
                    EmailAddress = new EmailAddress
                    {
                        Address = message.To
                    }
                }
            }
        };

        await graphClient.Me.SendMail.PostAsync(new SendMailPostRequestBody
        {
            Message = email
        });

        return RedirectToAction("Index");
    }
}
```

---

## Call downstream APIs

Register and call downstream APIs with automatic token acquisition from your controllers.

### Configure downstream API

Register the downstream API in `Startup.Auth.cs` with the following code:

```csharp
services.AddDownstreamApi("TodoListService", configuration.GetSection("DownstreamApi:TodoListService"));
```

Add the corresponding settings in `Web.config`:

```xml
<add key="DownstreamApi:TodoListService:BaseUrl" value="https://localhost:44351" />
<add key="DownstreamApi:TodoListService:Scopes" value="api://todo-api-client-id/.default" />
```

### Use IDownstreamApi in controllers

The following example shows how to perform CRUD operations against a downstream API from an MVC controller.

```csharp
[Authorize]
public class TodoController : Controller
{
    // GET all todos
    public async Task<ActionResult> Index()
    {
        var downstreamApi = this.GetDownstreamApi();

        var todos = await downstreamApi.GetForUserAsync<List<TodoItem>>(
            "TodoListService",
            options =>
            {
                options.RelativePath = "api/todolist";
            });

        return View(todos);
    }

    // GET specific todo
    public async Task<ActionResult> Details(int id)
    {
        var downstreamApi = this.GetDownstreamApi();

        var todo = await downstreamApi.GetForUserAsync<TodoItem>(
            "TodoListService",
            options =>
            {
                options.RelativePath = $"api/todolist/{id}";
            });

        return View(todo);
    }

    // POST new todo
    [HttpPost]
    public async Task<ActionResult> Create(TodoItem todo)
    {
        var downstreamApi = this.GetDownstreamApi();

        var createdTodo = await downstreamApi.PostForUserAsync<TodoItem, TodoItem>(
            "TodoListService",
            todo,
            options =>
            {
                options.RelativePath = "api/todolist";
            });

        return RedirectToAction("Index");
    }

    // PUT update todo
    [HttpPost]
    public async Task<ActionResult> Edit(int id, TodoItem todo)
    {
        var downstreamApi = this.GetDownstreamApi();

        await downstreamApi.CallApiForUserAsync(
            "TodoListService",
            options =>
            {
                options.HttpMethod = HttpMethod.Put;
                options.RelativePath = $"api/todolist/{id}";
                options.RequestBody = todo;
            });

        return RedirectToAction("Index");
    }

    // DELETE todo
    [HttpPost]
    public async Task<ActionResult> Delete(int id)
    {
        var downstreamApi = this.GetDownstreamApi();

        await downstreamApi.CallApiForUserAsync(
            "TodoListService",
            options =>
            {
                options.HttpMethod = HttpMethod.Delete;
                options.RelativePath = $"api/todolist/{id}";
            });

        return RedirectToAction("Index");
    }
}
```

---

## Explore sample applications

Use the following samples to see Microsoft.Identity.Web.OWIN in action.

### Review official Microsoft samples

The following table lists official samples that demonstrate Microsoft.Identity.Web.OWIN integration.

| Sample | Description |
| --- | --- |
| [ms-identity-aspnet-webapp-openidconnect](https://github.com/Azure-Samples/ms-identity-aspnet-webapp-openidconnect) | ASP.NET MVC app with Microsoft.Identity.Web.OWIN |
| Key Files | `App_Start/Startup.Auth.cs`, `Controllers/HomeController.cs` |

Clone and run the sample with the following commands:

```bash
git clone https://github.com/Azure-Samples/ms-identity-aspnet-webapp-openidconnect
cd ms-identity-aspnet-webapp-openidconnect
# Update Web.config with your Microsoft Entra app registration
# Run in Visual Studio
```

---

## Follow best practices

Apply these recommended patterns and avoid common mistakes when building with Microsoft.Identity.Web.OWIN.

### Apply recommended patterns

**1. Use distributed cache in production:**

```csharp
//  Production
services.AddDistributedTokenCaches(cacheServices =>
{
    cacheServices.AddDistributedSqlServerCache(options =>
    {
        options.ConnectionString = ConfigurationManager.ConnectionStrings["TokenCache"].ConnectionString;
        options.SchemaName = "dbo";
        options.TableName = "TokenCache";
        options.DefaultSlidingExpiration = TimeSpan.FromMinutes(90);
    });
});
```

**2. Handle incremental consent gracefully:**

```csharp
try
{
    var graphClient = this.GetGraphServiceClient();
    var user = await graphClient.Me.GetAsync();
}
catch (MsalUiRequiredException)
{
    // User needs to consent to additional scopes
    return new ChallengeResult();
}
```

**3. Use correlation IDs for troubleshooting:**

```csharp
var downstreamApi = this.GetDownstreamApi();
var correlationId = Guid.NewGuid();

var result = await downstreamApi.GetForUserAsync<Todo>(
    "TodoListService",
    options =>
    {
        options.RelativePath = $"api/todolist/{id}";
        options.TokenAcquisitionOptions = new TokenAcquisitionOptions
        {
            CorrelationId = correlationId
        };
    });
```

**4. Implement proper error handling:**

```csharp
try
{
    // Call API
}
catch (MsalUiRequiredException)
{
    return new ChallengeResult();
}
catch (HttpRequestException ex)
{
    logger.Error($"API call failed: {ex.Message}");
    return View("Error");
}
```

### Avoid common mistakes

**1. Don't use in-memory cache for web farms:**

```csharp
//  Wrong for load-balanced scenarios
services.AddDistributedTokenCaches(cacheServices =>
{
    cacheServices.AddDistributedMemoryCache();
});

//  Correct
services.AddDistributedTokenCaches(cacheServices =>
{
    cacheServices.AddDistributedSqlServerCache(/* ... */);
});
```

**2. Don't hardcode configuration:**

```csharp
//  Wrong
ClientId = "your-client-id-here"

//  Correct
ClientId = ConfigurationManager.AppSettings["AzureAd:ClientId"]
```

**3. Don't ignore token expiration:**

```csharp
//  Microsoft.Identity.Web.OWIN handles this automatically
// No manual token refresh needed!
```

---

## Troubleshoot common issues

Review the following solutions for common problems that occur during setup and runtime.

### Resolve common issues

**Issue 1: "Cannot find IAuthorizationHeaderProvider"**

**Solution:** Ensure `OwinTokenAcquirerFactory` is registered in `Startup.Auth.cs`:

```csharp
var tokenAcquirerFactory = TokenAcquirerFactory.GetDefaultInstance();
tokenAcquirerFactory.Build(serviceProvider);
app.Use<OwinTokenAcquisitionMiddleware>(tokenAcquirerFactory);
```

**Issue 2: "Cannot find GraphServiceClient"**

**Solution:** Add `AddMicrosoftGraph()` in `Startup.Auth.cs`:

```csharp
services.AddMicrosoftGraph();
```

**Issue 3: Token cache not persisting**

**Solution:** Verify distributed cache configuration:

```csharp
services.AddDistributedTokenCaches(cacheServices =>
{
    cacheServices.AddDistributedSqlServerCache(options =>
    {
        // Ensure connection string is correct
        options.ConnectionString = ConfigurationManager.ConnectionStrings["TokenCache"].ConnectionString;
    });
});
```

## Explore related content

Learn more about related features and scenarios.

- [MSAL.NET with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework)
- [ASP.NET Framework overview](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/aspnet-framework)
- [Authorization](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)
- [Calling downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)
