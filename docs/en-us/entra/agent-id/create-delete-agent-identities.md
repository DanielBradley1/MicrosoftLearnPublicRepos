<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/create-delete-agent-identities -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Create agent identities in agent identity platform

After you create an agent identity blueprint, the next step is to create one or more [agent identities](https://learn.microsoft.com/en-us/entra/agent-id/agent-identities) that represent AI agents in your tenant. Agent identity creation is typically performed when provisioning a new AI agent.

This procedure uses a multi-instance blueprint to provision child identities. If your blueprint uses single-instance mode, follow [Create a single-instance agent identity](https://learn.microsoft.com/en-us/entra/agent-id/create-single-instance-agent#provision-the-agent-identity) instead. Its identity shares the blueprint's client ID and doesn't use the blueprint principal provisioning path below.

You can create agent identities in two ways:

- **Microsoft Entra admin center** — Use the admin center wizard for quick, individual identity creation.
- **Microsoft Graph API** — Build a web service that creates agent identities programmatically, which is useful for automated provisioning at scale.

If you want to quickly create agent identities for testing purposes, consider using [this Microsoft Entra PowerShell module for creating and using agent identities](https://aka.ms/agentidpowershell).

## Prerequisites

To create agent identities, you need:

- An [agent identity blueprint](https://learn.microsoft.com/en-us/entra/agent-id/create-blueprint). Record the agent identity blueprint app ID from the creation process.
- A web service or application \(running locally or deployed to Azure\) that hosts the agent identity creation logic. This prerequisite applies only if you're creating agent identities programmatically.

Use the blueprint app ID as `client_id` in the token request. Save the agent identity `id` returned by the create call for the delete request. For identifier meanings, see [Record the identifiers for your scenario](https://learn.microsoft.com/en-us/entra/agent-id/key-concepts#record-the-identifiers-for-your-scenario).

## Use the Microsoft Entra admin center

You can create an agent identity directly in the Microsoft Entra admin center by selecting an existing blueprint and assigning owners and sponsors.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **Agents** > **Agent identities**.
3. Select **New agent identity \(Preview\)**.
4. On the **Basics** tab:

   - Under **Agent blueprint**, select a blueprint to create your agent identity from.
   - Enter a name in the **Agent identity name** field and select **Next**.

     [![Screenshot of the create agent identity wizard showing the Basics tab with blueprint selection and name fields.](https://learn.microsoft.com/en-us/entra/agent-id/media/create-delete-agent-identities/create-agent-identity-wizard.png)](https://learn.microsoft.com/en-us/entra/agent-id/media/create-delete-agent-identities/create-agent-identity-wizard.png#lightbox)

5. On the **Owners & Sponsors** tab, optionally add owners and sponsors for the identity:

   - Select the pencil icon next to the **Owners** field to change or add users who can manage this agent identity.
   - Select the pencil icon next to the **Sponsors** field to change or add users who can sponsor this agent identity.


   Note


   Sponsors can be users, dynamic membership groups, or Microsoft 365 groups. Security groups and role-assignable groups are not supported as sponsors.

6. Select **Next**.
7. Review your settings, and then select **Create**.
8. Select **Done** to exit the wizard or **Go to agent identity** to view the identity's detail page or configure more settings.

In the following steps, you'll learn how to create agent identities programmatically using Microsoft Graph API and Microsoft.Identity.Web. Get an access token first, then call the creation API.

- [Microsoft Graph API](#tabpanel_1_microsoft-graph-api)
- [Microsoft.Identity.Web](#tabpanel_1_microsoft-identity-web)

### Get an access token using agent identity blueprint

You use the agent identity blueprint to create each agent identity. Request an access token from Microsoft Entra using your agent identity blueprint:

When using a managed identity as a credential, you must first obtain an access token using your managed identity. Managed identity tokens can be requested from an IP address locally exposed in the compute environment. Refer to the [managed identity documentation for details](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/).

```
GET http://169.254.169.254/metadata/identity/oauth2/token?api-version=2019-08-01&resource=api://AzureADTokenExchange/.default
Metadata: True
```

After you obtain a token for the managed identity, request a token for the agent identity blueprint:

```
POST https://login.microsoftonline.com/<your-tenant-id>/oauth2/v2.0/token
Content-Type: application/x-www-form-urlencoded

client_id=<agent-blueprint-id>
scope=https://graph.microsoft.com/.default
client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
client_assertion=<msi-token>
grant_type=client_credentials
```

A `client_secret` parameter can also be used instead of `client_assertion` and `client_assertion_type`, when a client secret is being used in local development.

To install Microsoft.Identity.Web:

```ps
dotnet add package Microsoft.Identity.Web
```

*Microsoft.Identity.Web* includes an interface that automatically requests an access token and attaches it to outbound HTTP requests. When using *Microsoft.Identity.Web*, you can skip to the next step.

## Create an agent identity

Using the access token acquired in the previous step, you can now create agent identities in your tenant. Agent identity creation might occur in response to many different events or triggers, such as a user selecting a button to create a new agent. We recommend you create one agent identity for each agent, but you might choose a different approach based on your needs.

- [Microsoft Graph API](#tabpanel_2_microsoft-graph-api)
- [Microsoft.Identity.Web](#tabpanel_2_microsoft-identity-web)

Always include the OData-Version header when using @odata.type.

```
POST https://graph.microsoft.com/beta/servicePrincipals/microsoft.graph.agentIdentity
OData-Version: 4.0
Content-Type: application/json
Authorization: Bearer <token>
{
	"displayName": "My Agent Identity",
	"agentIdentityBlueprintId": "<my-agent-blueprint-id>",
	"sponsors@odata.bind": [
		"https://graph.microsoft.com/v1.0/users/<id>",
		"https://graph.microsoft.com/v1.0/groups/<group-id>"
	]
}
```

Note

When assigning a group as sponsor, only [supported group types](https://learn.microsoft.com/en-us/entra/agent-id/agent-owners-sponsors-managers#sponsors) are accepted. Groups aren't supported as owners.

To use *Microsoft.Identity.Web* to execute the Microsoft Graph API request to create an agent identity, add the following MISE configuration file:

Warning

Client secrets shouldn't be used as client credentials in production environments for agent identity blueprints due to security risks. Instead, use more secure authentication methods such as [federated identity credentials \(FIC\) with managed identities](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation-config-app-trust-managed-identity) or client certificates. These methods provide enhanced security by eliminating the need to store sensitive secrets directly within your application configuration.

```json
{
  "AzureAd": {
	"Instance": "https://login.microsoftonline.com/",
	"TenantId": "<your-tenant-id>",
	"ClientId": "<my-agent-blueprint-id>",
	"Scopes": "access_agent",
	"ClientCredentials": [
		{
			"SourceType": "ClientSecret",
			"ClientSecret": "your-client-secret"
		}
	]
  },

  "DownstreamApis": {
	"agent-identity": {
	  "BaseUrl": "https://graph.microsoft.com",
	  "RelativePath": "/beta/servicePrincipals/microsoft.graph.agentIdentity",
	  "Scopes": ["00000003-0000-0000-c000-000000000000/.default"],
	  "RequestAppToken": true
	}
  }
}
```

The code for the ASP.NET Core app \(*Program.cs*\) is the following example. The mutation endpoints require an authenticated caller. Configure an authorization policy that limits access to the intended administrators or owners before exposing these endpoints; the exact policy depends on your application.

```csharp
using System.Text.Json.Serialization;
using Microsoft.Identity.Abstractions;
using Microsoft.Identity.Web;
using Microsoft.Identity.Web.Resource;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddMicrosoftIdentityWebApiAuthentication(builder.Configuration)
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();
var app = builder.Build();

app.UseHttpsRedirection();
app.UseAuthentication();
app.UseAuthorization();

// Create an Agent identity
app.MapPost("/agent-identities", async (HttpContext httpContext) =>
{
    try
    {
        // Get the service to call the downstream API (preconfigured in the appsettings.json file)
        IDownstreamApi downstreamApi = httpContext.RequestServices.GetRequiredService<IDownstreamApi>();

        // Call the downstream API with a POST request to create an Agent Identity
        var jsonResult = await downstreamApi.PostForAppAsync<AgentIdentity, AgentIdentity>(
            "agent-identity",
            new AgentIdentity
            {
                displayName = "My agent identity",
                agentIdentityBlueprintId = "<my-agent-blueprint-id>",
                sponsorsOdataBind = new[] { "https://graph.microsoft.com/v1.0/users/<id>" }
            });
        return jsonResult?.id;
    }
    catch (Exception ex)
    {
        return ex.Message;
    }
}).RequireAuthorization();

app.Run();

// Type declarations must follow the top-level statements.
public class AgentIdentity
{
    [JsonPropertyName("@odata.type")]
    public string @odata_type { get; set; } = "#Microsoft.Graph.AgentIdentity";

    [JsonPropertyName("displayName")]
    public string? displayName { get; set; }

    [JsonPropertyName("agentIdentityBlueprintId")]
    public string? agentIdentityBlueprintId { get; set; }

    [JsonPropertyName("id")]
    public string? id { get; set; }

    [JsonPropertyName("sponsors@odata.bind")]
    public string[]? sponsorsOdataBind { get; set; }

    [JsonPropertyName("owners@odata.bind")]
    public string[]? ownersOdataBind { get; set; }
}
```

## Delete an agent identity

When an agent is deallocated or destroyed, your service should also delete the associated agent identity:

- [Microsoft Graph API](#tabpanel_3_microsoft-graph-api)
- [Microsoft.Identity.Web](#tabpanel_3_microsoft-identity-web)

```http
DELETE https://graph.microsoft.com/beta/servicePrincipals/<agent-identity-id>/microsoft.graph.agentIdentity
OData-Version: 4.0
Content-Type: application/json
Authorization: Bearer <token>
```

```csharp
// Delete an Agent identity
app.MapDelete("/agent-identities/{id}", async (HttpContext httpContext, string id) =>
{
	// Get the service to call the downstream API (preconfigured in the appsettings.json file)
	IDownstreamApi downstreamApi = httpContext.RequestServices.GetRequiredService<IDownstreamApi>();

	// Call the downstream API with a DELETE request to remove an Agent Identity
	var jsonResult = await downstreamApi.DeleteForAppAsync<string, string>(
		"agent-identity",
		null!,
		options =>
		{
			options.RelativePath += $"/{id}"; // Specify the ID of the agent identity to delete
		});
	return jsonResult;
}).RequireAuthorization();
```

## Related content

- [Plan an agent fleet on a shared runtime](https://learn.microsoft.com/en-us/entra/agent-id/plan-agent-fleet)
- [Configure inheritable permissions for blueprints](https://learn.microsoft.com/en-us/entra/agent-id/configure-inheritable-permissions-blueprints)
- [Call a custom API as an agent with ASP.NET Core](https://learn.microsoft.com/en-us/entra/agent-id/call-api-custom)
- [Call a custom API as a user with ASP.NET Core](https://learn.microsoft.com/en-us/entra/agent-id/aspnet-core-call-custom-api-as-user)
- [Manage owners and sponsors](https://learn.microsoft.com/en-us/entra/agent-id/manage-owners-sponsors-agents)
- [Agent identity blueprints](https://learn.microsoft.com/en-us/entra/agent-id/agent-blueprint)
