<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/custom-apis -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Call custom APIs

Microsoft.Identity.Web provides three approaches for calling your own protected APIs: IDownstreamApi, IAuthorizationHeaderProvider, and MicrosoftIdentityMessageHandler.

## Choose an approach

When you call custom REST APIs, you have three main options depending on your needs:

| Approach | Complexity | Flexibility | Use Case |
| --- | --- | --- | --- |
| **IDownstreamApi** | Low | Medium | Standard REST APIs with configuration |
| **MicrosoftIdentityMessageHandler** | Medium | High | HttpClient with DI and composable pipeline |
| **IAuthorizationHeaderProvider** | High | Very High | Complete control over HTTP requests |

## Use IDownstreamApi for standard scenarios

`IDownstreamApi` provides a simple, configuration-driven approach for calling REST APIs with automatic token acquisition.

### Install the package

Add the DownstreamApi NuGet package to your project.

```bash
dotnet add package Microsoft.Identity.Web.DownstreamApi
```

### Configure the API settings

Define your API in appsettings.json:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientCredentials": [
      {
        "SourceType": "ClientSecret",
        "ClientSecret": "your-client-secret"
      }
    ]
  },
  "DownstreamApis": {
    "MyApi": {
      "BaseUrl": "https://api.example.com",
      "Scopes": ["api://my-api-client-id/read", "api://my-api-client-id/write"],
      "RelativePath": "api/v1",
      "RequestAppToken": false
    },
    "PartnerApi": {
      "BaseUrl": "https://partner.example.com",
      "Scopes": ["api://partner-api-id/.default"],
      "RequestAppToken": true
    }
  }
}
```

### Set up ASP.NET Core

Register authentication and downstream API services in your `Program.cs` file.

```csharp
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// Add authentication
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();

// Register downstream APIs
builder.Services.AddDownstreamApis(
    builder.Configuration.GetSection("DownstreamApis"));

builder.Services.AddControllersWithViews();

var app = builder.Build();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();
app.Run();
```

### Perform basic API operations

The following controller demonstrates GET, POST, PUT, and DELETE operations against a configured downstream API.

```csharp
using Microsoft.Identity.Abstractions;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;

[Authorize]
public class ProductsController : Controller
{
    private readonly IDownstreamApi _api;
    
    public ProductsController(IDownstreamApi api)
    {
        _api = api;
    }
    
    // GET request
    public async Task<IActionResult> Index()
    {
        var products = await _api.GetForUserAsync<List<Product>>(
            "MyApi",
            "products");
        
        return View(products);
    }
    
    // Call downstream API with GET request with query parameters
    public async Task<IActionResult> Details(int id)
    {
        var product = await _api.GetForUserAsync<Product>(
            "MyApi",
            $"products/{id}");
        
        return View(product);
    }
    
    // Call downstream API with POST request
    [HttpPost]
    public async Task<IActionResult> Create([FromBody] Product product)
    {
        var created = await _api.PostForUserAsync<Product, Product>(
            "MyApi",
            "products",
            product);
        
        return CreatedAtAction(nameof(Details), new { id = created.Id }, created);
    }
    
    // Call downstream API with PUT request
    [HttpPut("{id}")]
    public async Task<IActionResult> Update(int id, [FromBody] Product product)
    {
        var updated = await _api.PutForUserAsync<Product, Product>(
            "MyApi",
            $"products/{id}",
            product);
        
        return Ok(updated);
    }
    
    // Call downstream API with DELETE request
    [HttpDelete("{id}")]
    public async Task<IActionResult> Delete(int id)
    {
        await _api.DeleteForUserAsync<Product>(
            "MyApi",
            $"products/{id}");
        
        return NoContent();
    }
}
```

### Configure advanced IDownstreamApi options

Use these options to customize request headers, override configuration, add query parameters, and read response headers.

#### Add custom headers and options

The following example adds custom HTTP headers to the outgoing request.

```csharp
public async Task<IActionResult> GetDataWithHeaders()
{
    var options = new DownstreamApiOptions
    {
        CustomizeHttpRequestMessage = message =>
        {
            message.Headers.Add("X-Custom-Header", "MyValue");
            message.Headers.Add("X-Request-Id", Guid.NewGuid().ToString());
            message.Headers.Add("X-Correlation-Id", HttpContext.TraceIdentifier);
        }
    };
    
    var data = await _api.CallApiForUserAsync<MyData>(
        "MyApi",
        options,
        content: null);
    
    return Ok(data);
}
```

#### Override configuration per request

The following example overrides the base URL, scopes, and token type for a single request.

```csharp
public async Task<IActionResult> CallDifferentEndpoint()
{
    var options = new DownstreamApiOptions
    {
        BaseUrl = "https://alternative-api.example.com",
        RelativePath = "v2/data",
        Scopes = new[] { "api://alternative/.default" },
        RequestAppToken = true
    };
    
    var data = await _api.CallApiForAppAsync<MyData>(
        "MyApi",
        options);
    
    return Ok(data);
}
```

#### Add query parameters

The following example builds a search request with query parameters in the relative path.

```csharp
public async Task<IActionResult> Search(string query, int page, int pageSize)
{
    var options = new DownstreamApiOptions
    {
        RelativePath = $"search?q={Uri.EscapeDataString(query)}&page={page}&pageSize={pageSize}"
    };
    
    var results = await _api.GetForUserAsync<SearchResults>(
        "MyApi",
        options);
    
    return Ok(results);
}
```

You can also use the options.ExtraQueryParameters dictionary.

#### Handle response headers

The following example reads rate-limit information from response headers.

```csharp
public async Task<IActionResult> GetWithHeaders()
{
    var response = await _api.CallApiAsync<MyData>(
        "MyApi",
        options =>
        {
            options.RelativePath = "data";
        });
    
    // Access response headers
    if (response.Headers.TryGetValues("X-RateLimit-Remaining", out var values))
    {
        var remaining = values.FirstOrDefault();
        _logger.LogInformation("Rate limit remaining: {Remaining}", remaining);
    }
    
    return Ok(response.Content);
}
```

### Acquire app-only tokens with IDownstreamApi

Use `GetForAppAsync` to call an API with application permissions instead of delegated user permissions.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DataController : ControllerBase
{
    private readonly IDownstreamApi _api;
    
    public DataController(IDownstreamApi api)
    {
        _api = api;
    }
    
    [HttpGet("batch")]
    public async Task<ActionResult> GetBatchData()
    {
        // Call with application permissions
        var data = await _api.GetForAppAsync<BatchData>(
            "MyApi",
            "batch/process");
        
        return Ok(data);
    }
}
```

## Use MicrosoftIdentityMessageHandler for HttpClient integration

`MicrosoftIdentityMessageHandler` adds Microsoft Entra authentication to your HttpClient pipeline automatically.

### Identify when to use MicrosoftIdentityMessageHandler

- You need fine-grained control over HTTP requests
- You want to compose multiple message handlers
- You're integrating with existing HttpClient-based code
- You need access to raw HttpResponseMessage

## Configure MicrosoftIdentityMessageHandler overloads

`MicrosoftIdentityMessageHandler` is a `DelegatingHandler` that adds authentication to HttpClient requests. Use this handler when you need full HttpClient capabilities with automatic token acquisition. The `AddMicrosoftIdentityMessageHandler` extension methods provide a flexible way to configure HttpClient with automatic Microsoft Entra ID authentication:

- **Parameterless**: For per-request configuration flexibility
- **Options instance**: For pre-configured options objects
- **Action delegate**: For inline configuration \(most common\)
- **IConfiguration**: For configuration from appsettings.json

Choose the overload that best fits your scenario and enjoy automatic authentication for your downstream API calls.

### Use the parameterless overload for per-request configuration

Configure authentication options on a per-request basis with this overload.

```csharp
services.AddHttpClient("FlexibleClient")
    .AddMicrosoftIdentityMessageHandler();

// Later, in a service:
var request = new HttpRequestMessage(HttpMethod.Get, "/api/data")
    .WithAuthenticationOptions(options =>
    {
        options.Scopes.Add("https://api.example.com/.default");
    });

var response = await httpClient.SendAsync(request);
```

### Pass a pre-configured options instance

Use this overload when you have a pre-configured options object.

```csharp
var options = new MicrosoftIdentityMessageHandlerOptions
{
    Scopes = { "https://graph.microsoft.com/.default" }
};
options.WithAgentIdentity("agent-application-id");

services.AddHttpClient("GraphClient", client =>
{
    client.BaseAddress = new Uri("https://graph.microsoft.com");
})
.AddMicrosoftIdentityMessageHandler(options);
```

### Configure inline with an action delegate

Use this overload for inline configuration, the most common scenario.

```csharp
services.AddHttpClient("MyApiClient", client =>
{
    client.BaseAddress = new Uri("https://api.example.com");
})
.AddMicrosoftIdentityMessageHandler(options =>
{
    options.Scopes.Add("https://api.example.com/.default");
    options.RequestAppToken = true;
});
```

### Load configuration from appsettings.json

Use this overload to bind settings directly from your configuration file.

**appsettings.json:**

```json
{
  "DownstreamApi": {
    "Scopes": ["https://api.example.com/.default"]
  },
  "GraphApi": {
    "Scopes": ["https://graph.microsoft.com/.default", "User.Read"]
  }
}
```

**Program.cs:**

```csharp
services.AddHttpClient("DownstreamApiClient", client =>
{
    client.BaseAddress = new Uri("https://api.example.com");
})
.AddMicrosoftIdentityMessageHandler(
    configuration.GetSection("DownstreamApi"),
    "DownstreamApi");

services.AddHttpClient("GraphClient", client =>
{
    client.BaseAddress = new Uri("https://graph.microsoft.com");
})
.AddMicrosoftIdentityMessageHandler(
    configuration.GetSection("GraphApi"),
    "GraphApi");
```

### Review configuration examples

These examples demonstrate common configuration patterns for the message handler.

#### Create a simple Web API client

The following example registers and consumes a weather API client.

```csharp
// Configure in Program.cs
services.AddHttpClient("WeatherApiClient", client =>
{
    client.BaseAddress = new Uri("https://api.weather.com");
})
.AddMicrosoftIdentityMessageHandler(options =>
{
    options.Scopes.Add("https://api.weather.com/.default");
});

// Use in a controller or service
public class WeatherService
{
    private readonly HttpClient _httpClient;
    
    public WeatherService(IHttpClientFactory factory)
    {
        _httpClient = factory.CreateClient("WeatherApiClient");
    }
    
    public async Task<WeatherForecast> GetForecastAsync(string city)
    {
        var response = await _httpClient.GetAsync($"/forecast/{city}");
        response.EnsureSuccessStatusCode();
        return await response.Content.ReadFromJsonAsync<WeatherForecast>();
    }
}
```

#### Configure multiple API clients

The following example registers two separate API clients with different scopes and token types.

```csharp
// Configure multiple clients in Program.cs
services.AddHttpClient("ApiClient1")
    .AddMicrosoftIdentityMessageHandler(options =>
    {
        options.Scopes.Add("https://api1.example.com/.default");
    });

services.AddHttpClient("ApiClient2")
    .AddMicrosoftIdentityMessageHandler(options =>
    {
        options.Scopes.Add("https://api2.example.com/.default");
        options.RequestAppToken = true;
    });

// Use in a service
public class MultiApiService
{
    private readonly HttpClient _client1;
    private readonly HttpClient _client2;
    
    public MultiApiService(IHttpClientFactory factory)
    {
        _client1 = factory.CreateClient("ApiClient1");
        _client2 = factory.CreateClient("ApiClient2");
    }
    
    public async Task<string> GetFromBothApisAsync()
    {
        var data1 = await _client1.GetStringAsync("/data");
        var data2 = await _client2.GetStringAsync("/data");
        return $"{data1} | {data2}";
    }
}
```

#### Load complex options from appsettings.json

The following example binds multiple API configurations from a shared configuration section.

**appsettings.json:**

```json
{
  "DownstreamApis": {
    "CustomerApi": {
      "Scopes": ["api://customer-api/.default"]
    },
    "OrderApi": {
      "Scopes": ["api://order-api/.default"]
    },
    "InventoryApi": {
      "Scopes": ["api://inventory-api/.default"]
    }
  }
}
```

**Program.cs:**

```csharp
var downstreamApis = configuration.GetSection("DownstreamApis");

services.AddHttpClient("CustomerApiClient", client =>
{
    client.BaseAddress = new Uri("https://customer-api.example.com");
})
.AddMicrosoftIdentityMessageHandler(
    downstreamApis.GetSection("CustomerApi"),
    "CustomerApi");

services.AddHttpClient("OrderApiClient", client =>
{
    client.BaseAddress = new Uri("https://order-api.example.com");
})
.AddMicrosoftIdentityMessageHandler(
    downstreamApis.GetSection("OrderApi"),
    "OrderApi");

services.AddHttpClient("InventoryApiClient", client =>
{
    client.BaseAddress = new Uri("https://inventory-api.example.com");
})
.AddMicrosoftIdentityMessageHandler(
    downstreamApis.GetSection("InventoryApi"),
    "InventoryApi");
```

### Override options per request

You can override default options on a per-request basis by using the `WithAuthenticationOptions` extension method.

```csharp
// Configure client with default options
services.AddHttpClient("ApiClient")
    .AddMicrosoftIdentityMessageHandler(options =>
    {
        options.Scopes.Add("https://api.example.com/.default");
    });

// Override for specific requests
public class MyService
{
    private readonly HttpClient _httpClient;
    
    public MyService(IHttpClientFactory factory)
    {
        _httpClient = factory.CreateClient("ApiClient");
    }
    
    public async Task<string> GetSensitiveDataAsync()
    {
        // Override scopes for this specific request
        var request = new HttpRequestMessage(HttpMethod.Get, "/api/sensitive")
            .WithAuthenticationOptions(options =>
            {
                options.Scopes.Clear();
                options.Scopes.Add("https://api.example.com/sensitive.read");
                options.RequestAppToken = true;
            });
        
        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
        return await response.Content.ReadAsStringAsync();
    }
}
```

### Implement advanced scenarios

The following sections cover agent identity, handler composition, and automatic challenge handling.

#### Configure agent identity

Use agent identity when your application needs to act on behalf of another application:

```csharp
services.AddHttpClient("AgentClient")
    .AddMicrosoftIdentityMessageHandler(options =>
    {
        options.Scopes.Add("https://graph.microsoft.com/.default");
        options.WithAgentIdentity("agent-application-id");
        options.RequestAppToken = true;
    });
```

#### Compose with other handlers

Chain multiple handlers in the pipeline to add logging, retries, or other cross-cutting concerns.

```csharp
services.AddHttpClient("ApiClient")
    .AddMicrosoftIdentityMessageHandler(options =>
    {
        options.Scopes.Add("https://api.example.com/.default");
    })
    .AddHttpMessageHandler<LoggingHandler>()
    .AddHttpMessageHandler<RetryHandler>();
```

#### Handle WWW-Authenticate challenges

The handler automatically processes WWW-Authenticate challenges for Conditional Access scenarios.

```csharp
// No additional code needed - automatic handling
services.AddHttpClient("ProtectedApiClient")
    .AddMicrosoftIdentityMessageHandler(options =>
    {
        options.Scopes.Add("https://api.example.com/.default");
    });

// The handler will automatically:
// 1. Detect 401 responses with WWW-Authenticate challenges
// 2. Extract required claims from the challenge
// 3. Acquire a new token with the additional claims
// 4. Retry the request with the new token
```

### Handle errors

The following example catches authentication and HTTP errors separately when calling an API through the message handler.

```csharp
public class MyService
{
    private readonly HttpClient _httpClient;
    private readonly ILogger<MyService> _logger;
    
    public MyService(IHttpClientFactory factory, ILogger<MyService> logger)
    {
        _httpClient = factory.CreateClient("ApiClient");
        _logger = logger;
    }
    
    public async Task<string> GetDataWithErrorHandlingAsync()
    {
        try
        {
            var response = await _httpClient.GetAsync("/api/data");
            response.EnsureSuccessStatusCode();
            return await response.Content.ReadAsStringAsync();
        }
        catch (MicrosoftIdentityAuthenticationException authEx)
        {
            _logger.LogError(authEx, "Authentication failed: {Message}", authEx.Message);
            throw;
        }
        catch (HttpRequestException httpEx)
        {
            _logger.LogError(httpEx, "HTTP request failed: {Message}", httpEx.Message);
            throw;
        }
    }
}
```

## Use IAuthorizationHeaderProvider for maximum control

`IAuthorizationHeaderProvider` gives you direct access to authorization headers for complete control over HTTP requests.

### Identify when to use IAuthorizationHeaderProvider

- You need complete control over HTTP request construction
- You're integrating with non-standard HTTP APIs
- You need to use HttpClient without DI
- You're building custom HTTP abstractions

### Perform basic operations

The following controller retrieves an authorization header and attaches it to a manual HTTP request.

```csharp
using Microsoft.Identity.Abstractions;

[Authorize]
public class CustomApiController : Controller
{
    private readonly IAuthorizationHeaderProvider _headerProvider;
    private readonly ILogger<CustomApiController> _logger;
    
    public CustomApiController(
        IAuthorizationHeaderProvider headerProvider,
        ILogger<CustomApiController> logger)
    {
        _headerProvider = headerProvider;
        _logger = logger;
    }
    
    public async Task<IActionResult> GetData()
    {
        // Get authorization header (includes "Bearer " prefix)
        var authHeader = await _headerProvider.CreateAuthorizationHeaderForUserAsync(
            scopes: new[] { "api://my-api/read" });
        
        using var client = new HttpClient();
        client.DefaultRequestHeaders.Add("Authorization", authHeader);
        client.DefaultRequestHeaders.Add("X-Custom-Header", "MyValue");
        
        var response = await client.GetAsync("https://api.example.com/data");
        response.EnsureSuccessStatusCode();
        
        var content = await response.Content.ReadAsStringAsync();
        return Content(content, "application/json");
    }
}
```

### Acquire app-only tokens

Use `CreateAuthorizationHeaderForAppAsync` to obtain an app-only token for background or daemon scenarios.

```csharp
public async Task<IActionResult> GetBackgroundData()
{
    // Get app-only authorization header
    var authHeader = await _headerProvider.CreateAuthorizationHeaderForAppAsync(
        scopes: new[] { "api://my-api/.default" });
    
    using var client = new HttpClient();
    client.DefaultRequestHeaders.Add("Authorization", authHeader);
    
    var response = await client.GetAsync("https://api.example.com/background");
    var data = await response.Content.ReadFromJsonAsync<BackgroundData>();
    
    return Ok(data);
}
```

### Integrate with custom HTTP libraries

The following example uses IAuthorizationHeaderProvider with a third-party HTTP library.

```csharp
public async Task<IActionResult> CallWithRestSharp()
{
    var authHeader = await _headerProvider.CreateAuthorizationHeaderForUserAsync(
        scopes: new[] { "api://my-api/read" });
    
    // Example with RestSharp
    var client = new RestClient("https://api.example.com");
    var request = new RestRequest("data", Method.Get);
    request.AddHeader("Authorization", authHeader);
    
    var response = await client.ExecuteAsync<MyData>(request);
    
    return Ok(response.Data);
}
```

### Configure advanced options

The following example creates an `AuthorizationHeaderProviderOptions` object with explicit scopes and token acquisition settings.

```csharp
public async Task<IActionResult> GetDataWithOptions()
{
    var options = new AuthorizationHeaderProviderOptions
    {
        Scopes = new[] { "api://my-api/read" },
        RequestAppToken = false,
        AcquireTokenOptions = new AcquireTokenOptions
        {
            AuthenticationOptionsName = JwtBearerDefaults.AuthenticationScheme,
            ForceRefresh = false,
            Claims = null
        }
    };
    
    var authHeader = await _headerProvider.CreateAuthorizationHeaderAsync(options);
    
    using var client = new HttpClient();
    client.DefaultRequestHeaders.Add("Authorization", authHeader);
    
    var response = await client.GetAsync("https://api.example.com/data");
    var data = await response.Content.ReadFromJsonAsync<MyData>();
    
    return Ok(data);
}
```

## Compare approaches

Use the following criteria to select the best approach for your scenario.

### Use IDownstreamApi when:

Calling standard REST APIs  
Want configuration-driven approach  
Need automatic serialization/deserialization  
Want minimal code  
Following Microsoft.Identity.Web patterns

**Example:**

```csharp
var product = await _api.GetForUserAsync<Product>("MyApi", "products/123");
```

### Use MicrosoftIdentityMessageHandler when:

Need full HttpClient capabilities  
Want to compose multiple handlers  
Using HttpClientFactory patterns  
Need access to HttpResponseMessage  
Integrating with existing HttpClient code

**Example:**

```csharp
var response = await _httpClient.GetAsync("api/products/123");
var product = await response.Content.ReadFromJsonAsync<Product>();
```

### Use IAuthorizationHeaderProvider when:

Need complete control over HTTP requests  
Using custom HTTP libraries  
Building custom abstractions  
Can't use HttpClientFactory  
Need to manually construct requests

**Example:**

```csharp
var authHeader = await _headerProvider.CreateAuthorizationHeaderForUserAsync(scopes);
client.DefaultRequestHeaders.Add("Authorization", authHeader);
```

## Handle errors

The following sections show error handling patterns for each approach.

### Handle IDownstreamApi errors

The following example catches consent challenges, HTTP status errors, and general exceptions.

```csharp
try
{
    var data = await _api.GetForUserAsync<MyData>("MyApi", "data");
}
catch (MicrosoftIdentityWebChallengeUserException ex)
{
    // User needs to consent
    _logger.LogWarning(ex, "Consent required for scopes: {Scopes}", string.Join(", ", ex.Scopes));
    throw; // Let ASP.NET Core handle consent flow
}
catch (HttpRequestException ex) when (ex.StatusCode == System.Net.HttpStatusCode.NotFound)
{
    return NotFound("Resource not found");
}
catch (HttpRequestException ex) when (ex.StatusCode == System.Net.HttpStatusCode.Unauthorized)
{
    return Unauthorized("API returned 401");
}
catch (Exception ex)
{
    _logger.LogError(ex, "API call failed");
    return StatusCode(500, "An error occurred");
}
```

### Handle MicrosoftIdentityMessageHandler errors

The following example inspects the response status code and logs detailed error information.

```csharp
try
{
    var response = await _httpClient.GetAsync("api/data");
    
    if (!response.IsSuccessStatusCode)
    {
        var error = await response.Content.ReadAsStringAsync();
        _logger.LogError("API returned {StatusCode}: {Error}", response.StatusCode, error);
        return StatusCode((int)response.StatusCode, error);
    }
    
    var data = await response.Content.ReadFromJsonAsync<MyData>();
    return Ok(data);
}
catch (HttpRequestException ex)
{
    _logger.LogError(ex, "HTTP request failed");
    return StatusCode(500, "Failed to call API");
}
```

## Follow best practices

Apply these patterns to build reliable, maintainable API integrations.

### 1. Configure timeout values

Set explicit timeouts to prevent requests from hanging indefinitely.

```csharp
builder.Services.AddDownstreamApi("MyApi", options =>
{
    options.BaseUrl = "https://api.example.com";
    options.HttpClientName = "MyApi";
});

builder.Services.AddHttpClient("MyApi", client =>
{
    client.Timeout = TimeSpan.FromSeconds(30);
});
```

### 2. Use typed clients

Wrap `IDownstreamApi` in a typed client interface to improve testability and encapsulation.

```csharp
public interface IProductApiClient
{
    Task<List<Product>> GetProductsAsync();
    Task<Product> GetProductAsync(int id);
    Task<Product> CreateProductAsync(Product product);
}

public class ProductApiClient : IProductApiClient
{
    private readonly IDownstreamApi _api;
    
    public ProductApiClient(IDownstreamApi api)
    {
        _api = api;
    }
    
    public Task<List<Product>> GetProductsAsync() =>
        _api.GetForUserAsync<List<Product>>("MyApi", "products");
    
    public Task<Product> GetProductAsync(int id) =>
        _api.GetForUserAsync<Product>("MyApi", $"products/{id}");
    
    public Task<Product> CreateProductAsync(Product product) =>
        _api.PostForUserAsync<Product, Product>("MyApi", "products", product);
}

// Register
builder.Services.AddScoped<IProductApiClient, ProductApiClient>();
```

### 3. Log request details

Track API call duration and outcomes to identify performance bottlenecks.

```csharp
public async Task<IActionResult> GetDataWithLogging()
{
    _logger.LogInformation("Calling MyApi for data");
    
    var stopwatch = Stopwatch.StartNew();
    
    try
    {
        var data = await _api.GetForUserAsync<MyData>("MyApi", "data");
        
        stopwatch.Stop();
        _logger.LogInformation("API call succeeded in {ElapsedMs}ms", stopwatch.ElapsedMilliseconds);
        
        return Ok(data);
    }
    catch (Exception ex)
    {
        stopwatch.Stop();
        _logger.LogError(ex, "API call failed after {ElapsedMs}ms", stopwatch.ElapsedMilliseconds);
        throw;
    }
}
```

## Implement OWIN support

Use the OWIN integration when your application runs on the classic ASP.NET pipeline instead of ASP.NET Core.

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.OWIN;
using Owin;

public class Startup
{
    public void Configuration(IAppBuilder app)
    {
      OwinTokenAcquirerFactory factory = TokenAcquirerFactory.GetDefaultInstance<OwinTokenAcquirerFactory>();

      app.AddMicrosoftIdentityWebApp(factory);
      factory.Services
        .AddDownstreamApis(factory.Configuration.GetSection("DownstreamAPI"))
        .AddInMemoryTokenCaches();
        factory.Build();
    }
}
```

## Explore related content

- [Calling from Web Apps](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apps)
- [Calling from Web APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis)
- [Microsoft Graph Integration](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/microsoft-graph)
- [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities)

---

**Next Steps**: Review the [main documentation](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview) for decision tree and comparison of all approaches.
