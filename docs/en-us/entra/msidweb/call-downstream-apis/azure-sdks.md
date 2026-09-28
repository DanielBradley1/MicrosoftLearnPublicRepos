<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/azure-sdks -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Call Azure SDKs with MicrosoftIdentityTokenCredential

Use `MicrosoftIdentityTokenCredential` from Microsoft.Identity.Web.Azure to authenticate Azure SDK clients \(Storage, Key Vault, Service Bus, and more\) with Microsoft Entra ID.

## Understand MicrosoftIdentityTokenCredential

The `MicrosoftIdentityTokenCredential` class implements the Azure SDK `TokenCredential` interface. This integration lets you use the same authentication configuration and token caching infrastructure across your entire application.

### Review the benefits

`MicrosoftIdentityTokenCredential` provides the following advantages:

- **Unified Authentication**: Use the same auth configuration for web apps, APIs, and Azure services
- **Token Caching**: Automatic token caching and refresh
- **Delegated & App Permissions**: Support for both user and application tokens
- **Agent Identities**: Compatible with agent identities feature
- **Managed Identity**: Seamless integration with Azure Managed Identity

## Install the packages

Install the Azure integration package:

```bash
dotnet add package Microsoft.Identity.Web.Azure
```

Then install the Azure SDK client packages you need:

```bash
# Examples
dotnet add package Azure.Storage.Blobs
dotnet add package Azure.Security.KeyVault.Secrets
dotnet add package Azure.Messaging.ServiceBus
dotnet add package Azure.Data.Tables
```

## Set up ASP.NET Core

### 1. Configure services

The following code registers authentication and adds Azure token credential support to your application:

```csharp
using Microsoft.Identity.Web;

var builder = WebApplication.CreateBuilder(args);

// Add authentication
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();

// Add Azure token credential support
builder.Services.AddMicrosoftIdentityAzureTokenCredential();

builder.Services.AddControllersWithViews();

var app = builder.Build();
app.UseAuthentication();
app.UseAuthorization();
app.MapControllers();
app.Run();
```

### 2. Configure appsettings.json

Add the Microsoft Entra configuration to your `appsettings.json` file:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity"
      }
    ]
  }
}
```

## Use MicrosoftIdentityTokenCredential

### Inject and use with Azure SDK clients

The following example shows how to inject `MicrosoftIdentityTokenCredential` and use it with Azure Blob Storage. The same approach applies to all Azure SDK clients.

```csharp
using Azure.Storage.Blobs;
using Microsoft.Identity.Web;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;

[Authorize]
public class StorageController : Controller
{
    private readonly MicrosoftIdentityTokenCredential _credential;
    private readonly IConfiguration _configuration;
    
    public StorageController(
        MicrosoftIdentityTokenCredential credential,
        IConfiguration configuration)
    {
        _credential = credential;
        _configuration = configuration;
    }
    
    public async Task<IActionResult> ListBlobs()
    {
        // Create Azure SDK client with credential
        var blobClient = new BlobServiceClient(
            new Uri($"https://{_configuration["StorageAccountName"]}.blob.core.windows.net"),
            _credential);
        
        var container = blobClient.GetBlobContainerClient("mycontainer");
        var blobs = new List<string>();
        
        await foreach (var blob in container.GetBlobsAsync())
        {
            blobs.Add(blob.Name);
        }
        
        return View(blobs);
    }
}
```

## Use delegated permissions

Call Azure services on behalf of the signed-in user by using delegated permissions.

### Upload files with Azure Storage

The following controller demonstrates how to upload a file to Azure Blob Storage using a delegated token:

```csharp
using Azure.Storage.Blobs;
using Microsoft.Identity.Web;

[Authorize]
public class FileController : Controller
{
    private readonly MicrosoftIdentityTokenCredential _credential;
    
    public FileController(MicrosoftIdentityTokenCredential credential)
    {
        _credential = credential;
    }
    
    public async Task<IActionResult> UploadFile(IFormFile file)
    {
        // Credential will automatically acquire delegated token
        var blobClient = new BlobServiceClient(
            new Uri("https://myaccount.blob.core.windows.net"),
            _credential);
        
        var container = blobClient.GetBlobContainerClient("uploads");
        await container.CreateIfNotExistsAsync();
        
        var blob = container.GetBlobClient(file.FileName);
        await blob.UploadAsync(file.OpenReadStream(), overwrite: true);
        
        return Ok($"File {file.FileName} uploaded");
    }
}
```

## Use application permissions

Call Azure services with application permissions when no user context is available.

### Configure app-only tokens

Set `RequestAppToken` to `true` on the credential options to acquire an app-only token:

```csharp
public class AzureService
{
    private readonly MicrosoftIdentityTokenCredential _credential;
    
    public AzureService(MicrosoftIdentityTokenCredential credential)
    {
        _credential = credential;
    }
    
    public async Task<List<string>> ListBlobsAsync()
    {
        // Configure credential for app-only token
        _credential.Options.RequestAppToken = true;
        
        var blobClient = new BlobServiceClient(
            new Uri("https://myaccount.blob.core.windows.net"),
            _credential);
        
        var container = blobClient.GetBlobContainerClient("data");
        var blobs = new List<string>();
        
        await foreach (var blob in container.GetBlobsAsync())
        {
            blobs.Add(blob.Name);
        }
        
        return blobs;
    }
}
```

### Create a daemon application

The following example shows how to build a standalone daemon application that accesses Azure Blob Storage with app-only permissions:

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Identity.Abstractions;
using Microsoft.Identity.Web;
using Azure.Storage.Blobs;

class Program
{
    static async Task Main(string[] args)
    {
        // Build service provider
        var tokenAcquirerFactory = TokenAcquirerFactory.GetDefaultInstance();
        tokenAcquirerFactory.Services.AddMicrosoftIdentityAzureTokenCredential();
        var sp = tokenAcquirerFactory.Build();
        
        // Get credential
        var credential = sp.GetRequiredService<MicrosoftIdentityTokenCredential>();
        credential.Options.RequestAppToken = true;
        
        // Use with Azure SDK
        var blobClient = new BlobServiceClient(
            new Uri("https://myaccount.blob.core.windows.net"),
            credential);
        
        var container = blobClient.GetBlobContainerClient("data");
        
        await foreach (var blob in container.GetBlobsAsync())
        {
            Console.WriteLine($"Blob: {blob.Name}");
        }
    }
}
```

## Integrate agent identities

`MicrosoftIdentityTokenCredential` supports agent identities through the `Options` property. The following service class shows how to configure agent and agent-user identities:

```csharp
using Microsoft.Identity.Web;

public class AgentService
{
    private readonly MicrosoftIdentityTokenCredential _credential;
    
    public AgentService(MicrosoftIdentityTokenCredential credential)
    {
        _credential = credential;
    }
    
    public async Task<List<string>> ListBlobsForAgentAsync(string agentIdentity)
    {
        // Configure for agent identity
        _credential.Options.WithAgentIdentity(agentIdentity);
        _credential.Options.RequestAppToken = true;
        
        var blobClient = new BlobServiceClient(
            new Uri("https://myaccount.blob.core.windows.net"),
            _credential);
        
        var container = blobClient.GetBlobContainerClient("agent-data");
        var blobs = new List<string>();
        
        await foreach (var blob in container.GetBlobsAsync())
        {
            blobs.Add(blob.Name);
        }
        
        return blobs;
    }
    
    public async Task<string> GetSecretForAgentUserAsync(string agentIdentity, Guid userOid, string secretName)
    {
        // Configure for agent user identity
        _credential.Options.WithAgentUserIdentity(agentIdentity, userOid);
        
        var secretClient = new SecretClient(
            new Uri("https://myvault.vault.azure.net"),
            _credential);
        
        var secret = await secretClient.GetSecretAsync(secretName);
        return secret.Value.Value;
    }
}
```

See [Agent Identities documentation](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities) for more details.

## Configure FIC and Managed Identity

`MicrosoftIdentityTokenCredential` works with FIC and Azure Managed Identity.

### Configure Managed Identity credentials

Add the following configuration to use Managed Identity as a credential source:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity"
      }
    ]
  }
}
```

### Use system-assigned Managed Identity

When you deploy to Azure, the credential automatically uses the system-assigned managed identity. The following service class demonstrates this pattern:

```csharp
// No additional code needed!
// When deployed to Azure, the credential automatically uses managed identity

public class StorageService
{
    private readonly MicrosoftIdentityTokenCredential _credential;
    
    public StorageService(MicrosoftIdentityTokenCredential credential)
    {
        _credential = credential;
        _credential.Options.RequestAppToken = true;
    }
    
    public async Task<List<string>> ListContainersAsync()
    {
        // Uses managed identity when running in Azure
        var blobClient = new BlobServiceClient(
            new Uri("https://myaccount.blob.core.windows.net"),
            _credential);
        
        var containers = new List<string>();
        await foreach (var container in blobClient.GetBlobContainersAsync())
        {
            containers.Add(container.Name);
        }
        
        return containers;
    }
}
```

### Use user-assigned Managed Identity

Specify the `ManagedIdentityClientId` in your configuration to use a user-assigned managed identity:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "user-assigned-identity-client-id"
      }
    ]
  }
}
```

## Implement OWIN authentication

For ASP.NET applications that use OWIN, register the Azure token credential in the startup class:

```csharp
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.OWIN;
using Owin;

public class Startup
{
    public void Configuration(IAppBuilder app)
    {
     app.SetDefaultSignInAsAuthenticationType(CookieAuthenticationDefaults.AuthenticationType);
     app.UseCookieAuthentication(new CookieAuthenticationOptions());

     OwinTokenAcquirerFactory factory = TokenAcquirerFactory.GetDefaultInstance<OwinTokenAcquirerFactory>();

     app.AddMicrosoftIdentityWebApp(factory);
     factory.Services
        .AddMicrosoftIdentityAzureTokenCredential();
      factory.Build();
    }
}
```

## Follow best practices

### 1. Reuse Azure SDK clients

Azure SDK clients are thread-safe, so reuse them across requests. However, `MicrosoftIdentityTokenCredential` is a scoped service, so you can't use it with `AddAzureServices()`, which creates singletons.

### 2. Use Managed Identity in production

Prefer certificateless authentication with managed identity in production environments:

```csharp
//  Good: Certificateless auth with managed identity
{
  "ClientCredentials": [
    {
      "SourceType": "SignedAssertionFromManagedIdentity"
    }
  ]
}
```

### 3. Handle Azure SDK exceptions

Wrap Azure SDK calls in try-catch blocks to handle common failure scenarios:

```csharp
using Azure;

try
{
    var blob = await blobClient.DownloadAsync();
}
catch (RequestFailedException ex) when (ex.Status == 404)
{
    // Blob not found
}
catch (RequestFailedException ex) when (ex.Status == 403)
{
    // Insufficient permissions
}
catch (RequestFailedException ex)
{
    _logger.LogError(ex, "Azure SDK call failed with status {Status}", ex.Status);
}
```

### 5. Use configuration for URIs

Store Azure resource URIs in configuration instead of hardcoding them:

```csharp
//  Bad: Hardcoded URIs
var blobClient = new BlobServiceClient(new Uri("https://myaccount.blob.core.windows.net"), credential);

//  Good: Configuration-driven
var storageUri = _configuration["Azure:Storage:Uri"];
var blobClient = new BlobServiceClient(new Uri(storageUri), credential);
```

## Troubleshoot common errors

### Resolve "ManagedIdentityCredential authentication failed"

**Cause**: Managed identity not enabled or misconfigured.

**Solution**:

- Enable managed identity on Azure resource \(App Service, VM, etc.\)
- For user-assigned identity, specify `ManagedIdentityClientId`
- Verify identity has required role assignments

### Resolve "This request is not authorized to perform this operation"

**Cause**: Missing Azure RBAC role assignment.

**Solution**:

- Assign appropriate role to managed identity or user
- Example: "Storage Blob Data Contributor" for blob operations
- Wait up to 5 minutes for role assignments to propagate

### Fix local token acquisition failures

**Cause**: Managed identity only works in Azure.

**Solution**: Use different credential source locally:

```json
{
  "ClientCredentials": [
    {
      "SourceType": "ClientSecret",
      "ClientSecret": "secret-for-local-dev"
    }
  ]
}
```

### Fix scope errors with Azure resources

**Cause**: Incorrect scope format.

**Solution**: Use Azure resource-specific scopes:

- Storage: `https://storage.azure.com/user_impersonation` or `.default`
- KeyVault: `https://vault.azure.net/user_impersonation` or `.default`
- Service Bus: `https://servicebus.azure.net/user_impersonation` or `.default`

## Explore related content

- [Azure SDK for .NET Documentation](https://learn.microsoft.com/en-us/dotnet/azure/sdk/azure-sdk-for-dotnet)
- [Managed Identity Documentation](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
- [Credentials Configuration](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
- [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities)
- [Calling Downstream APIs Overview](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)

---

**Next Steps**: Learn about [calling custom APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/custom-apis) with IDownstreamApi and IAuthorizationHeaderProvider.
