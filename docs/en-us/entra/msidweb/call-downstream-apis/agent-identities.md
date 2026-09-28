<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Authenticate agent identities with Microsoft.Identity.Web

Not .NET? See the [Entra SDK container sidecar](https://github.com/AzureAD/microsoft-identity-web/blob/feature/doc-modernization/docs/sidecar/agent-identities.md) for the Entra SDK container documentation. The container sidecar supports agent identities in any language and platform.

## Understand agent identities

The Microsoft.Identity.Web.AgentIdentities NuGet package provides support for agent identities in Microsoft Entra ID. It enables applications to securely authenticate and acquire tokens for agent applications, agent identities, and agent user identities, which is useful for autonomous agents, interactive agents acting on behalf of their user, and agents having their own user identity.

This package is part of the [Microsoft.Identity.Web](https://github.com/AzureAD/microsoft-identity-web) suite of libraries and was introduced in version 3.10.0.

## Review key concepts

The following concepts are essential for working with agent identities.

### Define an agent identity blueprint

An agent identity blueprint has a special application registration in Microsoft Entra that has permissions to act on behalf of Agent identities or Agent User identities. It's represented by its application ID \(Agent identity blueprint Client ID\). The agent identity blueprint is configured with credentials \(typically FIC+MSI or client certificates\) and permissions to acquire tokens for itself to call graph. This is the app that you develop. It's a confidential client application, usually a web API. The only permissions it can have are maintain \(create / delete\) Agent Identities \(using the Microsoft Graph\)

### Create an agent identity

An agent identity is a special service principal in Microsoft Entra. It represents an identity that the agent identity blueprint created and is authorized to impersonate. It doesn't have credentials on its own. The agent identity blueprint can acquire tokens on behalf of the agent identity provided the user or tenant admin consented for the agent identity to the corresponding scopes. Autonomous agents acquire app tokens on behalf of the agent identity. Interactive agents called with a user token acquire user tokens on behalf of the agent identity.

### Create an agent user identity

An agent user identity is an agent identity that can also act as a user \(think of an agent identity that would have its own mailbox, or would report to you in the directory\). An agent application can acquire a token on behalf of an agent user identity.

### Understand federated identity credentials \(FIC\)

FIC is a trust mechanism in Microsoft Entra that enables applications to trust each other using OpenID Connect \(OIDC\) tokens. In the context of agent identities, FICs are used to establish trust between the agent application and agent identities, and agent identities and agent user identities.

### Find more information

For details about Microsoft Entra agent identities, see [Microsoft Entra Agent ID documentation](https://learn.microsoft.com/en-us/entra/agent-id/).

## Install the package

Run the following command to add the NuGet package to your project:

```bash
dotnet add package Microsoft.Identity.Web.AgentIdentities
```

## Implement agent identities

Follow these steps to configure and use agent identities in your application.

### 1. Configure services

First, register the required services in your application:

```csharp
// Add the core Identity Web services
services.AddTokenAcquisition();
services.AddInMemoryTokenCaches();
services.AddHttpClient();

// Add Microsoft Graph integration if needed.
// Requires the Microsoft.Identity.Web.GraphServiceClient package
services.AddMicrosoftGraph();

// Add Agent Identities support
services.AddAgentIdentities();
```

### 2. Configure the agent identity blueprint

Configure your agent identity blueprint application with the necessary credentials using appsettings.json:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "agent-application-client-id",

    "ClientCredentials": [
      {
        "SourceType": "StoreWithDistinguishedName",
        "CertificateStorePath": "LocalMachine/My",
        "CertificateDistinguishedName": "CN=YourCertificateName"
      }

      // Or for Federation Identity Credential with Managed Identity:
      // {
      //   "SourceType": "SignedAssertionFromManagedIdentity",
      //   "ManagedIdentityClientId": "managed-identity-client-id"  // Omit for system-assigned
      // }
    ]
  }
}
```

Or, if you prefer, configure programmatically:

```csharp
// Configure the information about the agent application
services.Configure<MicrosoftIdentityApplicationOptions>(
    options =>
    {
        options.Instance = "https://login.microsoftonline.com/";
        options.TenantId = "your-tenant-id";
        options.ClientId = "agent-application-client-id";
        options.ClientCredentials = [
            CertificateDescription.FromStoreWithDistinguishedName(
                "CN=YourCertificateName", StoreLocation.LocalMachine, StoreName.My)
        ];
    });
```

See [https://aka.ms/ms-id-web/credential-description](https://aka.ms/ms-id-web/credential-description) for all the ways to express credentials.

On ASP.NET Core, use the override of services.Configure taking an authentication scheme. You can also use Microsoft.Identity.Web.Owin if you have an ASP.NET Core application on OWIN \(not recommended for new apps\), or even create a daemon application.

### 3. Use agent identities

Choose the appropriate token acquisition pattern based on your agent scenario.

#### Acquire tokens for an agent identity

Use these patterns to acquire tokens for agent identities in autonomous or interactive scenarios.

##### Acquire app tokens for autonomous agents

For your autonomous agent application to acquire **app-only** tokens for an agent identity:

```csharp
// Get the required services from the DI container
IAuthorizationHeaderProvider authorizationHeaderProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

// Configure options for the agent identity
string agentIdentity = "agent-identity-guid";
var options = new AuthorizationHeaderProviderOptions()
    .WithAgentIdentity(agentIdentity);

// Acquire an access token for the agent identity
string authHeader = await authorizationHeaderProvider
    .CreateAuthorizationHeaderForAppAsync("https://resource/.default", options);

// The authHeader contains "Bearer " + the access token (or another protocol
// depending on the options)
```

##### Acquire user tokens for interactive agents

For your interactive agent application to acquire **user** tokens for an agent identity on behalf of the user calling the web API:

```csharp
// Get the required services from the DI container
IAuthorizationHeaderProvider authorizationHeaderProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

// Configure options for the agent identity
string agentIdentity = "agent-identity-guid";
var options = new AuthorizationHeaderProviderOptions()
    .WithAgentIdentity(agentIdentity);

// Acquire an access token for the agent identity
string authHeader = await authorizationHeaderProvider
    .CreateAuthorizationHeaderForAppAsync(["https://resource/.default"], options);

// The authHeader contains "Bearer " + the access token (or another protocol
// depending on the options)
```

#### Acquire tokens for an agent user identity

For your agent application to acquire tokens on behalf of an agent user identity, you can use either the user's UPN \(User Principal Name\) or OID \(Object ID\).

##### Authenticate with UPN \(User Principal Name\)

The following example acquires a user token by specifying the user's UPN:

```csharp
// Get the required services
IAuthorizationHeaderProvider authorizationHeaderProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

// Configure options for the agent user identity using UPN
string agentIdentity = "agent-identity-client-id";
string userUpn = "user@contoso.com";
var options = new AuthorizationHeaderProviderOptions()
    .WithAgentUserIdentity(agentIdentity, userUpn);

// Create a ClaimsPrincipal to enable token caching
ClaimsPrincipal user = new ClaimsPrincipal();

// Acquire a user token
string authHeader = await authorizationHeaderProvider
    .CreateAuthorizationHeaderForUserAsync(
        scopes: ["https://graph.microsoft.com/.default"],
        options: options,
        user: user);

// The user object now has claims including uid and utid. If you use it
// in another call it will use the cached token.
```

##### Authenticate with OID \(Object ID\)

The following example acquires a user token by specifying the user's OID:

```csharp
// Get the required services
IAuthorizationHeaderProvider authorizationHeaderProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

// Configure options for the agent user identity using OID
string agentIdentity = "agent-identity-client-id";
Guid userOid = Guid.Parse("e1f76997-1b35-4aa8-8a58-a5d8f1ac4636");
var options = new AuthorizationHeaderProviderOptions()
    .WithAgentUserIdentity(agentIdentity, userOid);

// Create a ClaimsPrincipal to enable token caching
ClaimsPrincipal user = new ClaimsPrincipal();

// Acquire a user token
string authHeader = await authorizationHeaderProvider
    .CreateAuthorizationHeaderForUserAsync(
        scopes: ["https://graph.microsoft.com/.default"],
        options: options,
        user: user);

// The user object now has claims including uid and utid. If you use it
// in another call it will use the cached token.
```

### 4. Integrate with Microsoft Graph

Install the Microsoft.Identity.Web.AgentIdentities package, which adds support for agent identities.

```bash
dotnet add package Microsoft.Identity.Web.AgentIdentities
```

Add support for Microsoft Graph in your service collection:

```bash
services.AddMicrosoftGraph();
```

You can now get a `GraphServiceClient` from the service provider.

#### Call Microsoft Graph with agent identity

The following example calls Microsoft Graph APIs using an agent identity:

```csharp
// Get the GraphServiceClient
GraphServiceClient graphServiceClient = serviceProvider.GetRequiredService<GraphServiceClient>();

// Call Microsoft Graph APIs with the agent identity
var applications = await graphServiceClient.Applications
    .GetAsync(r => r.Options.WithAuthenticationOptions(options =>
    {
        options.WithAgentIdentity(agentIdentity);
        options.RequestAppToken = true;
    }));
```

#### Call Microsoft Graph with agent user identity

You can use either UPN or OID with Microsoft Graph:

```csharp
// Get the GraphServiceClient
GraphServiceClient graphServiceClient = serviceProvider.GetRequiredService<GraphServiceClient>();

// Call Microsoft Graph APIs with the agent user identity using UPN
var me = await graphServiceClient.Me
    .GetAsync(r => r.Options.WithAuthenticationOptions(options =>
        options.WithAgentUserIdentity(agentIdentity, userUpn)));

// Or using OID
var me = await graphServiceClient.Me
    .GetAsync(r => r.Options.WithAuthenticationOptions(options =>
        options.WithAgentUserIdentity(agentIdentity, userOid)));
```

### 5. Integrate with downstream APIs

To call other APIs using the `IDownstreamApi` abstraction:

1. Install the Microsoft.Identity.Web.DownstreamApi package which provides the IDownstreamApi abstraction

```bash
dotnet add package Microsoft.Identity.Web.DownstreamApi
```

2. Add a `DownstreamApis` section in your configuration, specifying the parameters for your downstream API:

```json
"AzureAd":{
    // usual config
},
"DownstreamApis":{
   "MyApi":
   {
    "BaseUrl": "https://myapi.domain.com",
    "Scopes": [ "https://myapi.domain.com/read", "https://myapi.domain.com/write" ]
   }
}
```

3. Add support for downstream APIs in your service collection:

```bash
services.AddDownstreamApis(Configuration.GetSection("DownstreamApis"));
```

You can now access an `IDownstreamApi` service from the service provider and call the "MyApi" API using any HTTP verb. The following example demonstrates calling APIs with agent identity and agent user identity:

```csharp
// Get the IDownstreamApi service
IDownstreamApi downstreamApi = serviceProvider.GetRequiredService<IDownstreamApi>();

// Call API with agent identity
var response = await downstreamApi.GetForAppAsync<string>(
    "MyApi",
    options => options.WithAgentIdentity(agentIdentity));

// Call API with agent user identity using UPN
var userResponse = await downstreamApi.GetForUserAsync<string>(
    "MyApi",
    options => options.WithAgentUserIdentity(agentIdentity, userUpn));

// Or using OID
var userResponseByOid = await downstreamApi.GetForUserAsync<string>(
    "MyApi",
    options => options.WithAgentUserIdentity(agentIdentity, userOid));
```

### 6. Integrate with Azure SDKs

To call Azure SDKs, use the `MicrosoftIdentityAzureCredential` class from the Microsoft.Identity.Web.Azure NuGet package.

Install the Microsoft.Identity.Web.Azure package:

```bash
dotnet add package Microsoft.Identity.Web.Azure
```

Add support for Azure token credential in your service collection:

```bash
services.AddMicrosoftIdentityAzureTokenCredential();
```

You can now get a `MicrosoftIdentityTokenCredential` from the service provider. This class has a member Options to which you can apply the `.WithAgentIdentity()` or `.WithAgentUserIdentity()` methods.

See [Azure SDKs integration](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/azure-sdks) for more details.

### 7. Configure HttpClient with MicrosoftIdentityMessageHandler

To use HttpClient directly with flexible authentication options, use the `MicrosoftIdentityMessageHandler` from the Microsoft.Identity.Web.TokenAcquisition package.

Note: The Microsoft.Identity.Web.TokenAcquisition package is already referenced by Microsoft.Identity.Web.AgentIdentities.

#### Authenticate agent identity with MicrosoftIdentityMessageHandler

The following example configures an HttpClient with agent identity authentication:

```csharp
// Configure HttpClient with MicrosoftIdentityMessageHandler in DI
services.AddHttpClient("MyApiClient", client =>
{
    client.BaseAddress = new Uri("https://myapi.domain.com");
})
.AddMicrosoftIdentityMessageHandler(options =>
{
    options.Scopes= { "https://myapi.domain.com/.default" }
});

// Usage in your service or controller
public class MyService
{
    private readonly HttpClient _httpClient;

    public MyService(IHttpClientFactory httpClientFactory)
    {
        _httpClient = httpClientFactory.CreateClient("MyApiClient");
    }

    public async Task<string> CallApiWithAgentIdentity(string agentIdentity)
    {
        // Create request with agent identity authentication
        var request = new HttpRequestMessage(HttpMethod.Get, "/api/data")
            .WithAuthenticationOptions(options =>
            {
                options.WithAgentIdentity(agentIdentity);
                options.RequestAppToken = true;
            });

        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
        return await response.Content.ReadAsStringAsync();
    }
}
```

#### Authenticate agent user identity with MicrosoftIdentityMessageHandler

The following example sends a request authenticated with an agent user identity:

```csharp
public async Task<string> CallApiWithAgentUserIdentity(string agentIdentity, string userUpn)
{
    // Create request with agent user identity authentication
    var request = new HttpRequestMessage(HttpMethod.Get, "/api/userdata")
        .WithAuthenticationOptions(options =>
        {
            options.WithAgentUserIdentity(agentIdentity, userUpn);
            options.Scopes.Add("https://myapi.domain.com/user.read");
        });

    var response = await _httpClient.SendAsync(request);
    response.EnsureSuccessStatusCode();
    return await response.Content.ReadAsStringAsync();
}
```

#### Configure HttpClient manually

You can also configure the handler manually for more control:

```csharp
// Get the authorization header provider
IAuthorizationHeaderProvider headerProvider =
    serviceProvider.GetRequiredService<IAuthorizationHeaderProvider>();

// Create the handler with default options
var handler = new MicrosoftIdentityMessageHandler(
    headerProvider,
    new MicrosoftIdentityMessageHandlerOptions
    {
        Scopes = { "https://graph.microsoft.com/.default" }
    });

// Create HttpClient with the handler
using var httpClient = new HttpClient(handler);

// Make requests with per-request authentication options
var request = new HttpRequestMessage(HttpMethod.Get, "https://graph.microsoft.com/v1.0/applications")
    .WithAuthenticationOptions(options =>
    {
        options.WithAgentIdentity(agentIdentity);
        options.RequestAppToken = true;
    });

var response = await httpClient.SendAsync(request);
```

The `MicrosoftIdentityMessageHandler` provides a flexible, composable way to add authentication to your HttpClient-based code while maintaining full compatibility with existing Microsoft Identity Web extension methods for agent identities.

### Validate tokens from agent identities

Validate tokens acquired for agent identities or agent user identities the same way as for any web API. However, you can also:

- check if a token was issued for an agent identity and for which agent blueprint.

  ```csharp
  HttpContext.User.GetParentAgentBlueprint()
  ```


  returns the ClientId of the parent agent blueprint if the token is issued for an agent identity \(or agent user identity\)\\

- check if a token was issued for an agent user identity.

  ```csharp
  HttpContext.User.IsAgentUserIdentity()
  ```

These 2 extensions methods, apply to both ClaimsIdentity and ClaimsPrincipal.

## Review prerequisites

Ensure you complete these configuration steps before implementing agent identities.

### Configure Microsoft Entra registration

1. **Agent Application Configuration**:

   - Register an agent application with the graph SDK
   - Add client credentials for the agent application
   - Grant appropriate API permissions, such as Application.ReadWrite.All to create agent identities
   - Example configuration in JSON:

     ```json
     {
       "AzureAd": {
         "Instance": "https://login.microsoftonline.com/",
         "TenantId": "your-tenant-id",
         "ClientId": "agent-application-id",
         "ClientCredentials": [
           {
             "SourceType": "StoreWithDistinguishedName",
             "CertificateStorePath": "LocalMachine/My",
             "CertificateDistinguishedName": "CN=YourCertName"
           }
         ]
       }
     }
     ```

2. **Agent Identity Configuration**:

   - Have the agent create an agent identity
   - Grant appropriate API permissions based on what your agent identity needs to do

3. **User Permission**:

   - For agent user identity scenarios, ensure appropriate user permissions are configured.

## Understand the authentication flow

Under the hood, the Microsoft.Identity.Web.AgentIdentities package:

1. Establishes trust between the agent application and agent identity, and between the agent identity and the agent user identity, using Federated Identity Credentials \(FIC\).
2. Acquires FIC tokens using the `GetFicTokenAsync` method
3. Uses the FIC tokens to authenticate as the agent identity
4. For agent user identities, it leverages MSAL extensions to perform user token acquisition

## Troubleshoot common issues

Review these common issues and resolutions when working with agent identities.

### Resolve known issues

1. **Missing FIC Configuration**: Ensure Federated Identity Credentials are properly configured in Microsoft Entra between the agent application and agent identity.
2. **Permission Issues**: Verify the agent application has sufficient permissions to manage agent identities and that the agent identities have enough permissions to call the downstream APIs.
3. **Certificate Problems**: If you use a client certificate, verify that the certificate is registered in the app registration, properly installed, and accessible by the agent application code.
4. **Token Acquisition Failures**: Enable logging to diagnose token acquisition failures. The following code configures debug-level console logging:

   ```csharp
   services.AddLogging(builder => {
       builder.AddConsole();
       builder.SetMinimumLevel(LogLevel.Debug);
   });
   ```

## Explore additional resources

- [Microsoft Entra documentation](https://learn.microsoft.com/en-us/entra/identity/)
- [Microsoft Identity Web documentation](https://github.com/AzureAD/microsoft-identity-web/wiki)
- [Workload Identity Federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation)
- [Microsoft Graph SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview)
