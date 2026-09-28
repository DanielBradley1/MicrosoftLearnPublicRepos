<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/microsoft-graph -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Call Microsoft Graph

Call Microsoft Graph from your ASP.NET Core and OWIN applications by using Microsoft.Identity.Web and the Microsoft Graph SDK to access Microsoft 365 data and services.

## Understand Microsoft Graph integration

Microsoft Graph provides a unified API endpoint for accessing data across Microsoft 365, Windows, and Enterprise Mobility + Security. Microsoft.Identity.Web simplifies authentication and token acquisition for Microsoft Graph, while the Microsoft Graph SDK provides a fluent, typed API for calling Graph endpoints.

### Choose Microsoft.Identity.Web.GraphServiceClient

The following benefits make Microsoft.Identity.Web.GraphServiceClient the recommended approach for calling Microsoft Graph.

- **Automatic token acquisition**: Handles user and app tokens seamlessly
- **Token caching**: Built-in caching for performance
- **Fluent API**: Type-safe, IntelliSense-friendly Graph calls
- **Incremental consent**: Request additional scopes on demand
- **Multiple authentication schemes**: Support for web apps and web APIs
- **Both v1.0 and Beta**: Use stable and preview endpoints together

## Install required packages

Install the Microsoft Graph SDK integration package:

```bash
dotnet add package Microsoft.Identity.Web.GraphServiceClient
```

For Microsoft Graph Beta APIs:

```bash
dotnet add package Microsoft.Identity.Web.GraphServiceClientBeta
```

## Set up ASP.NET Core

### 1. Configure services

Add Microsoft Graph support to your application:

```csharp
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// Add authentication (web app or web API)
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();

// Add Microsoft Graph support
builder.Services.AddMicrosoftGraph();

builder.Services.AddControllersWithViews();

var app = builder.Build();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();
app.Run();
```

### 2. Configure appsettings.json

Configure Graph options in your configuration file:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientSecret": "your-client-secret",
    "CallbackPath": "/signin-oidc"
  },
  "DownstreamApis": {
    "MicrosoftGraph": {
      "BaseUrl": "https://graph.microsoft.com/v1.0",
      "Scopes": ["User.Read", "User.ReadBasic.All"]
    }
  }
}
```

**Configuration with Code:**

```csharp
builder.Services.AddMicrosoftGraph(options =>
{
    builder.Configuration.GetSection("DownstreamApis:MicrosoftGraph").Bind(options);
});
```

Or configure directly in code:

```csharp
builder.Services.AddMicrosoftGraph();
builder.Services.Configure<MicrosoftGraphOptions>(options =>
{
    options.BaseUrl = "https://graph.microsoft.com/v1.0";
    options.Scopes = new[] { "User.Read", "Mail.Read" };
});
```

### 3. Configure national cloud support

To use Microsoft Graph in national clouds, specify the BaseUrl in your configuration:

```json
{
  "DownstreamApis": {
    "MicrosoftGraph": {
      "BaseUrl": "https://graph.microsoft.us/v1.0",
      "Scopes": ["User.Read"]
    }
  }
}
```

See [Microsoft Graph deployments](https://learn.microsoft.com/en-us/graph/deployments#microsoft-graph-and-graph-explorer-service-root-endpoints) for endpoint URLs.

## Use GraphServiceClient

### Inject GraphServiceClient

Inject `GraphServiceClient` from the constructor:

```csharp
using Microsoft.Graph;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;

[Authorize]
public class ProfileController : Controller
{
    private readonly GraphServiceClient _graphClient;
    
    public ProfileController(GraphServiceClient graphClient)
    {
        _graphClient = graphClient;
    }
    
    public async Task<IActionResult> Index()
    {
        // Call Microsoft Graph
        var user = await _graphClient.Me.GetAsync();
        return View(user);
    }
}
```

## Use delegated permissions \(user tokens\)

Call Graph on behalf of the signed-in user with delegated permissions.

### Retrieve basic user profile

Retrieve the current user's profile information from Microsoft Graph.

```csharp
[Authorize]
public class ProfileController : Controller
{
    private readonly GraphServiceClient _graphClient;
    
    public ProfileController(GraphServiceClient graphClient)
    {
        _graphClient = graphClient;
    }
    
    public async Task<IActionResult> Me()
    {
        // Get current user's profile
        var user = await _graphClient.Me.GetAsync();
        
        return View(new UserViewModel
        {
            DisplayName = user.DisplayName,
            Mail = user.Mail,
            JobTitle = user.JobTitle
        });
    }
}
```

### Request incremental consent

Request additional scopes dynamically when your application needs them:

```csharp
[Authorize]
[AuthorizeForScopes("Mail.Read")]
public class MailController : Controller
{
    private readonly GraphServiceClient _graphClient;
    
    public MailController(GraphServiceClient graphClient)
    {
        _graphClient = graphClient;
    }
    
    public async Task<IActionResult> Inbox()
    {
        try
        {
            // Request Mail.Read scope dynamically
            var messages = await _graphClient.Me.Messages
                .GetAsync(r => r.Options.WithScopes("Mail.Read"));
            
            return View(messages);
        }
        catch (MicrosoftIdentityWebChallengeUserException)
        {
            // ASP.NET Core will redirect user to consent
            // thansk to the AuthorizeForScopes attribute.
            throw;
        }
    }
}
```

### Apply query options

Use Graph SDK query options to filter, select, and order results:

```csharp
public async Task<IActionResult> UnreadMessages()
{
    var messages = await _graphClient.Me.Messages
        .GetAsync(requestConfiguration =>
        {
            requestConfiguration.QueryParameters.Filter = "isRead eq false";
            requestConfiguration.QueryParameters.Select = new[] { "subject", "from", "receivedDateTime" };
            requestConfiguration.QueryParameters.Orderby = new[] { "receivedDateTime desc" };
            requestConfiguration.QueryParameters.Top = 10;
            
            // Request specific scope
            requestConfiguration.Options.WithScopes("Mail.Read");
        });
    
    return View(messages);
}
```

### Page through results

Handle paged results from Microsoft Graph by iterating through each page:

```csharp
public async Task<IActionResult> AllUsers()
{
    var allUsers = new List<User>();
    
    // Get first page
    var users = await _graphClient.Users
        .GetAsync(r => r.Options.WithScopes("User.ReadBasic.All"));
    
    // Add first page
    allUsers.AddRange(users.Value);
    
    // Iterate through remaining pages
    var pageIterator = PageIterator<User, UserCollectionResponse>
        .CreatePageIterator(
            _graphClient,
            users,
            user =>
            {
                allUsers.Add(user);
                return true; // Continue iteration
            });
    
    await pageIterator.IterateAsync();
    
    return View(allUsers);
}
```

## Use application permissions \(app-only tokens\)

Call Graph with application permissions when no user context is required.

### Call Graph with WithAppOnly\(\)

Use the `WithAppOnly()` method to make Graph calls with application permissions.

```csharp
[Authorize]
[ApiController]
[Route("api/[controller]")]
public class AdminController : ControllerBase
{
    private readonly GraphServiceClient _graphClient;
    
    public AdminController(GraphServiceClient graphClient)
    {
        _graphClient = graphClient;
    }
    
    [HttpGet("users/count")]
    public async Task<ActionResult<int>> GetUserCount()
    {
        // Get count using app permissions
        var count = await _graphClient.Users.Count
            .GetAsync(r => r.Options.WithAppOnly());
        
        return Ok(count);
    }
    
    [HttpGet("applications")]
    public async Task<ActionResult> GetApplications()
    {
        // List applications using app permissions
        var apps = await _graphClient.Applications
            .GetAsync(r => r.Options.WithAppOnly());
        
        return Ok(apps.Value);
    }
}
```

### Configure app permissions

Specify an app token request in appsettings.json:

```json
{
  "DownstreamApis": {
    "MicrosoftGraph": {
      "BaseUrl": "https://graph.microsoft.com/v1.0",
      "RequestAppToken": true
    }
  }
}
```

The scopes will automatically be set to `["https://graph.microsoft.com/.default"]`.

### Configure detailed app-only options

Set explicit app-only authentication options in code.

```csharp
public async Task<IActionResult> GetApplicationsDetailed()
{
    var apps = await _graphClient.Applications
        .GetAsync(r =>
        {
            r.Options.WithAuthenticationOptions(options =>
            {
                // Request app token explicitly
                options.RequestAppToken = true;
                
                // Scopes automatically become [.default]
                // No need to specify: options.Scopes = new[] { "https://graph.microsoft.com/.default" };
            });
        });
    
    return Ok(apps);
}
```

## Handle multiple authentication schemes

If your app uses multiple authentication schemes \(for example, web app + API\), specify which scheme to use:

```csharp
using Microsoft.AspNetCore.Authentication.JwtBearer;

[Authorize]
public class ApiDataController : ControllerBase
{
    private readonly GraphServiceClient _graphClient;
    
    public ApiDataController(GraphServiceClient graphClient)
    {
        _graphClient = graphClient;
    }
    
    [HttpGet("profile")]
    public async Task<ActionResult> GetProfile()
    {
        // Specify JWT Bearer scheme
        var user = await _graphClient.Me
            .GetAsync(r => r.Options
                .WithAuthenticationScheme(JwtBearerDefaults.AuthenticationScheme));
        
        return Ok(user);
    }
}
```

### Configure detailed scheme options

Set the authentication scheme and scopes explicitly in code.

```csharp
public async Task<ActionResult> GetMailWithScheme()
{
    var messages = await _graphClient.Me.Messages
        .GetAsync(r =>
        {
            r.Options.WithAuthenticationOptions(options =>
            {
                // Specify authentication scheme
                options.AcquireTokenOptions.AuthenticationOptionsName = 
                    JwtBearerDefaults.AuthenticationScheme;
                
                // Specify scopes
                options.Scopes = new[] { "Mail.Read" };
            });
        });
    
    return Ok(messages);
}
```

## Use both v1.0 and Beta endpoints

Register and call both Microsoft Graph v1.0 and Beta in the same application.

### 1. Install both packages

```bash
dotnet add package Microsoft.Identity.Web.GraphServiceClient
dotnet add package Microsoft.Identity.Web.GraphServiceClientBeta
```

### 2. Register both services

```csharp
using Microsoft.Identity.Web;

builder.Services.AddMicrosoftGraph();
builder.Services.AddMicrosoftGraphBeta();
```

### 3. Use both clients

```csharp
using GraphServiceClient = Microsoft.Graph.GraphServiceClient;
using GraphBetaServiceClient = Microsoft.Graph.Beta.GraphServiceClient;

public class MyController : Controller
{
    private readonly GraphServiceClient _graphClient;
    private readonly GraphBetaServiceClient _graphBetaClient;
    
    public MyController(
        GraphServiceClient graphClient,
        GraphBetaServiceClient graphBetaClient)
    {
        _graphClient = graphClient;
        _graphBetaClient = graphBetaClient;
    }
    
    public async Task<IActionResult> GetData()
    {
        // Use stable v1.0 endpoint
        var user = await _graphClient.Me.GetAsync();
        
        // Use beta endpoint for preview features
        var profile = await _graphBetaClient.Me.Profile.GetAsync();
        
        return View(new { user, profile });
    }
}
```

## Send batch requests

Combine multiple Graph calls into a single HTTP request to improve performance:

```csharp
using Microsoft.Graph.Models;

public async Task<IActionResult> GetDashboard()
{
    var batchRequestContent = new BatchRequestContentCollection(_graphClient);
    
    // Add multiple requests to batch
    var userRequest = _graphClient.Me.ToGetRequestInformation();
    var messagesRequest = _graphClient.Me.Messages.ToGetRequestInformation();
    var eventsRequest = _graphClient.Me.Events.ToGetRequestInformation();
    
    var userRequestId = await batchRequestContent.AddBatchRequestStepAsync(userRequest);
    var messagesRequestId = await batchRequestContent.AddBatchRequestStepAsync(messagesRequest);
    var eventsRequestId = await batchRequestContent.AddBatchRequestStepAsync(eventsRequest);
    
    // Send batch request
    var batchResponse = await _graphClient.Batch.PostAsync(batchRequestContent);
    
    // Extract responses
    var user = await batchResponse.GetResponseByIdAsync<User>(userRequestId);
    var messages = await batchResponse.GetResponseByIdAsync<MessageCollectionResponse>(messagesRequestId);
    var events = await batchResponse.GetResponseByIdAsync<EventCollectionResponse>(eventsRequestId);
    
    return View(new DashboardViewModel 
    { 
        User = user,
        Messages = messages.Value,
        Events = events.Value
    });
}
```

## Apply common Graph patterns

Use these patterns to perform frequent Microsoft Graph operations in your application.

### Get user's manager

Retrieve the signed-in user's manager from the directory.

```csharp
public async Task<IActionResult> GetManager()
{
    var manager = await _graphClient.Me.Manager.GetAsync();
    
    // Cast to User (manager is DirectoryObject)
    if (manager is User managerUser)
    {
        return View(managerUser);
    }
    
    return NotFound("Manager not found");
}
```

### Get user's photo

Download the signed-in user's profile photo as a stream.

```csharp
public async Task<IActionResult> GetPhoto()
{
    try
    {
        var photoStream = await _graphClient.Me.Photo.Content.GetAsync();
        
        return File(photoStream, "image/jpeg");
    }
    catch (ServiceException ex) when (ex.StatusCode == System.Net.HttpStatusCode.NotFound)
    {
        return NotFound("Photo not available");
    }
}
```

### Send email

Send an email message on behalf of the signed-in user.

```csharp
public async Task<IActionResult> SendEmail([FromBody] EmailRequest request)
{
    var message = new Message
    {
        Subject = request.Subject,
        Body = new ItemBody
        {
            ContentType = BodyType.Html,
            Content = request.Body
        },
        ToRecipients = new List<Recipient>
        {
            new Recipient
            {
                EmailAddress = new EmailAddress
                {
                    Address = request.ToEmail
                }
            }
        }
    };
    
    await _graphClient.Me.SendMail
        .PostAsync(new SendMailPostRequestBody
        {
            Message = message,
            SaveToSentItems = true
        },
        requestConfiguration =>
        {
            requestConfiguration.Options.WithScopes("Mail.Send");
        });
    
    return Ok("Email sent");
}
```

### Create calendar event

Create a new calendar event with attendees for the signed-in user.

```csharp
public async Task<IActionResult> CreateEvent([FromBody] EventRequest request)
{
    var newEvent = new Event
    {
        Subject = request.Subject,
        Start = new DateTimeTimeZone
        {
            DateTime = request.StartTime.ToString("yyyy-MM-ddTHH:mm:ss"),
            TimeZone = "UTC"
        },
        End = new DateTimeTimeZone
        {
            DateTime = request.EndTime.ToString("yyyy-MM-ddTHH:mm:ss"),
            TimeZone = "UTC"
        },
        Attendees = request.Attendees.Select(email => new Attendee
        {
            EmailAddress = new EmailAddress { Address = email },
            Type = AttendeeType.Required
        }).ToList()
    };
    
    var createdEvent = await _graphClient.Me.Events
        .PostAsync(newEvent, r => r.Options.WithScopes("Calendars.ReadWrite"));
    
    return Ok(createdEvent);
}
```

### Search users

Search for users in the directory by display name or email address.

```csharp
public async Task<IActionResult> SearchUsers(string searchTerm)
{
    var users = await _graphClient.Users
        .GetAsync(requestConfiguration =>
        {
            requestConfiguration.QueryParameters.Filter = 
                $"startswith(displayName,'{searchTerm}') or startswith(mail,'{searchTerm}')";
            requestConfiguration.QueryParameters.Select = 
                new[] { "displayName", "mail", "jobTitle" };
            requestConfiguration.QueryParameters.Top = 10;
            
            requestConfiguration.Options.WithScopes("User.ReadBasic.All");
        });
    
    return Ok(users.Value);
}
```

## Implement OWIN support

For ASP.NET applications that use OWIN, configure the token acquirer factory and register Microsoft Graph services.

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.OWIN;
using Owin;

public class Startup
{
    public void Configuration(IAppBuilder app)
    {
      OwinTokenAcquirerFactory factory = TokenAcquirerFactory.GetDefaultInstance<OwinTokenAcquirerFactory>();
      app.AddMicrosoftIdentityWebApi(factory);
      factory.Services
        .AddMicrosoftGraph();
      factory.Build();
    }
}
```

### 2. Call API from controllers

Retrieve a `GraphServiceClient` instance in your controller and call Microsoft Graph.

```csharp
using Microsoft.Identity.Abstractions;
using Microsoft.Identity.Web;
using System.Web.Http;

[Authorize]
public class DataController : ApiController
{
    public DataController()
    {
    }

    public async Task<IHttpActionResult> GetMyProfile()
    {
        GraphServiceClient graphServiceClient = this.GetGraphServiceClient();
        var me = await graphServiceClient.Me.GetAsync();
        return Ok(me);
    }
}
```

## Migrate from Microsoft.Identity.Web.MicrosoftGraph 2.x

If you're migrating from the older Microsoft.Identity.Web.MicrosoftGraph package \(SDK 4.x\), review the following key changes:

### 1. Remove old package and add new

```bash
dotnet remove package Microsoft.Identity.Web.MicrosoftGraph
dotnet add package Microsoft.Identity.Web.GraphServiceClient
```

### 2. Update method calls

The `.Request()` method has been removed in SDK 5.x:

**Before \(SDK 4.x\):**

```csharp
var user = await _graphClient.Me.Request().GetAsync();

var messages = await _graphClient.Me.Messages
    .Request()
    .WithScopes("Mail.Read")
    .GetAsync();
```

**After \(SDK 5.x\):**

```csharp
var user = await _graphClient.Me.GetAsync();

var messages = await _graphClient.Me.Messages
    .GetAsync(r => r.Options.WithScopes("Mail.Read"));
```

### 3. Update WithScopes\(\) location

**Before:**

```csharp
var users = await _graphClient.Users
    .Request()
    .WithScopes("User.Read.All")
    .GetAsync();
```

**After:**

```csharp
var users = await _graphClient.Users
    .GetAsync(r => r.Options.WithScopes("User.Read.All"));
```

### 4. Update WithAppOnly\(\) location

**Before:**

```csharp
var apps = await _graphClient.Applications
    .Request()
    .WithAppOnly()
    .GetAsync();
```

**After:**

```csharp
var apps = await _graphClient.Applications
    .GetAsync(r => r.Options.WithAppOnly());
```

### 5. Update WithAuthenticationScheme\(\) location

**Before:**

```csharp
var user = await _graphClient.Me
    .Request()
    .WithAuthenticationScheme(JwtBearerDefaults.AuthenticationScheme)
    .GetAsync();
```

**After:**

```csharp
var user = await _graphClient.Me
    .GetAsync(r => r.Options
        .WithAuthenticationScheme(JwtBearerDefaults.AuthenticationScheme));
```

See [Microsoft Graph .NET SDK v5 changelog](https://github.com/microsoftgraph/msgraph-sdk-dotnet/blob/dev/docs/upgrade-to-v5.md) for complete migration details.

## Handle errors

### Handle ServiceException

Catch `ODataError` and `MicrosoftIdentityWebChallengeUserException` to handle Graph API failures gracefully.

```csharp
using Microsoft.Graph.Models.ODataErrors;

public async Task<IActionResult> GetData()
{
    try
    {
        var user = await _graphClient.Me.GetAsync();
        return Ok(user);
    }
    catch (ODataError ex) when (ex.ResponseStatusCode == 404)
    {
        return NotFound("Resource not found");
    }
    catch (ODataError ex) when (ex.ResponseStatusCode == 403)
    {
        return Forbid("Insufficient permissions");
    }
    catch (MicrosoftIdentityWebChallengeUserException)
    {
        // User needs to consent
        throw;
    }
    catch (Exception ex)
    {
        _logger.LogError(ex, "Graph API call failed");
        return StatusCode(500, "An error occurred");
    }
}
```

## Follow best practices

### 1. Request minimum scopes

Only request scopes you need:

```csharp
//  Bad: Requesting too many scopes
options.Scopes = new[] { "User.Read", "Mail.ReadWrite", "Calendars.ReadWrite", "Files.ReadWrite.All" };

//  Good: Request only what you need
options.Scopes = new[] { "User.Read" };
```

### 2. Use incremental consent

Request additional scopes only when needed:

```csharp
// Sign-in: Only User.Read
// Later, when accessing mail:
var messages = await _graphClient.Me.Messages
    .GetAsync(r => r.Options.WithScopes("Mail.Read"));
```

### 3. Cache GraphServiceClient

GraphServiceClient is safe to reuse. Register as singleton or inject from DI.

### 4. Use select to reduce response size

```csharp
//  Bad: Getting all properties
var users = await _graphClient.Users.GetAsync();

//  Good: Select only needed properties
var users = await _graphClient.Users
    .GetAsync(r => r.QueryParameters.Select = 
        new[] { "displayName", "mail", "id" });
```

## Troubleshoot common issues

### Resolve "Insufficient privileges to complete the operation"

**Cause**: App doesn't have required Graph permissions.

**Solution**:

- Add required API permissions in app registration
- Admin consent required for app permissions
- User consent required for delegated permissions

### Resolve "AADSTS65001: The user or administrator has not consented"

**Cause**: User hasn't consented to requested scopes.

**Solution**: Use incremental consent with `.WithScopes()` to trigger consent flow.

### Resolve photo 404 errors

**Cause**: User doesn't have a profile photo.

**Solution**: Handle 404 gracefully and provide default avatar.

### Resolve batch request failures

**Cause**: Individual requests in batch may fail independently.

**Solution**: Check each response in batch for errors:

```csharp
var userResponse = await batchResponse.GetResponseByIdAsync<User>(userRequestId);
if (userResponse == null)
{
    // Handle individual request failure
}
```

## Related content

- [Microsoft Graph Documentation](https://learn.microsoft.com/en-us/graph/)
- [Graph SDK v5 Migration Guide](https://github.com/microsoftgraph/msgraph-sdk-dotnet/blob/dev/docs/upgrade-to-v5.md)
- [Calling Downstream APIs Overview](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)
- [Calling from Web Apps](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apps)
- [Calling from Web APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis)

---

**Next Steps**: Learn about [calling Azure SDKs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/azure-sdks) or [custom APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/custom-apis).
