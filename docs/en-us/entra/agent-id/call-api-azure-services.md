<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/call-api-azure-services -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Call Azure services from your agent using .NET Azure SDK

This article guides you on how to call Azure services from your agent. To authenticate to Azure services such as Azure Storage or Azure Key Vault using agent identities, use the `MicrosoftIdentityTokenCredential` class from *Microsoft.Identity.Web.Azure*. The `MicrosoftIdentityTokenCredential` class implements Azure SDK's `TokenCredential` interface, enabling seamless integration between *Microsoft.Identity.Web* and Azure SDK clients.

To call an API from an agent, you need to obtain an access token that the agent can use to authenticate itself to the API. We recommend using the *Microsoft.Identity.Web* SDK for .NET to call your web APIs. This SDK simplifies the process of acquiring and validating tokens. For other languages, use the [Microsoft Entra ID Auth SDK \(sidecar\)](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview).

## Prerequisites

- An agent identity with appropriate permissions to call the target API. You need a user for the on-behalf-of flow.
- An agent's user account with appropriate permissions to call the target API.

## Implementation steps

1. Install the Azure integration package and the *Microsoft.Identity.Web.AgentIdentities* package to add support for agent identities.

   ```bash
   dotnet add package Microsoft.Identity.Web.Azure
   dotnet add package Microsoft.Identity.Web.AgentIdentities
   ```

2. Install the Azure SDK package you want to use, for example, Azure Storage:

   ```bash
   dotnet add package Azure.Storage.Blobs
   ```

3. Configure your services to add Azure token credential support:

   ```csharp
   using Microsoft.AspNetCore.Authentication.OpenIdConnect;
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

4. Configure Azure token credential options in *appsettings.json*

   Warning

   Client secrets shouldn't be used as client credentials in production environments for agent identity blueprints due to security risks. Instead, use more secure authentication methods such as [federated identity credentials \(FIC\) with managed identities](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-config-app-trust-managed-identity) or client certificates. These methods provide enhanced security by eliminating the need to store sensitive secrets directly within your application configuration.

   ```json
   {
     "AzureAd": {
       "Instance": "https://login.microsoftonline.com/",
       "TenantId": "<your-tenant-id>",
       "ClientId": "<agent-blueprint-id>",

      // Other client creedentials available. See <https://aka.ms/ms-id-web/client-credentials>
       "ClientCredentials": [
         {
           "SourceType": "ClientSecret",
           "ClientSecret": "your-client-secret"
         }
       ]   
     }
   }
   ```

5. Acquire a token credential from the service provider and use it with Azure SDK clients.

   1. For agent identities, you can acquire either an app only token \(autonomous agents\) or an on-behalf of user token \(interactive agents\) by using the `WithAgentIdentity` method. For app only tokens, set the `RequestAppToken` property to `true`. For delegated on-behalf of user tokens, don't set the `RequestAppToken` property or explicitly set it to `false`.

      ```csharp
      using Microsoft.Identity.Web;

      public class AgentService
      {
          private readonly MicrosoftIdentityTokenCredential _credential;

          public AgentService(MicrosoftIdentityTokenCredential credential)
          {
              _credential = credential;
          }

          // Call Azure service with the agent identity for app only scenario
          public async Task<List<string>> ListBlobsForAgentAppOnlyAsync(string agentIdentity)
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

          // Call Azure service with the agent identity for on-behalf of user scenario
          public async Task<List<string>> ListBlobsForAgentOnBehalfOfUserAsync(string agentIdentity)
          {
              // Configure for agent identity
              _credential.Options.WithAgentIdentity(agentIdentity);
              _credential.Options.RequestAppToken = false;

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
      }
      ```

   2. You can also acquire a token for an agent's user account. To do this, you can use either User Principal Name \(UPN\) or Object Identity \(OID\) to identify the agent's user account.

      For object ID:

      ```csharp
      using Microsoft.Identity.Web;

      public class AgentService
      {
          private readonly MicrosoftIdentityTokenCredential _credential;

          public AgentService(MicrosoftIdentityTokenCredential credential)
          {
              _credential = credential;
          }

          // Use object ID to identify the agent's user account
          public async Task<List<string>> ListBlobsForAgentUserByOidAsync(string agentIdentity)
          {
              // Configure for agent identity
              string userOid = "user-object-id";
              _credential.Options.WithAgentUserIdentity(agentIdentity, userOid);

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

          // Use UPN to identify the agent's user account
          public async Task<List<string>> ListBlobsForAgentUserByUpnAsync(string agentIdentity)
          {
              // Configure for agent identity
              string userUpn = "user@contoso.com";

              _credential.Options.WithAgentUserIdentity(agentIdentity, userUpn);

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
      }
      ```

## Related content

- [Call custom APIs](https://learn.microsoft.com/en-us/entra/agent-id/call-api-custom)
- [Call Microsoft Graph](https://learn.microsoft.com/en-us/entra/agent-id/call-api-microsoft-graph)
