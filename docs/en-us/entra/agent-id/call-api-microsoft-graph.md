<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/call-api-microsoft-graph -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# Call Microsoft Graph as an agent with ASP.NET Core

List directory users with the agent's application permissions, not the inbound caller's delegated access.

In this article, you configure `GraphServiceClient` to obtain a Microsoft Graph token for the agent while the agent API separately authorizes the caller.

## Prerequisites

- The Microsoft Graph application permissions required by the operation.
- Application permissions granted to the agent identity with admin consent. See [Grant Microsoft Graph application permissions to an agent identity](https://learn.microsoft.com/en-us/entra/agent-id/grant-application-permissions-agent-identity).
- The [blueprint credential and ASP.NET Core services](https://learn.microsoft.com/en-us/entra/agent-id/call-api-custom#configure-the-blueprint-credential), including token acquisition and the `AgentUser` inbound authorization policy. Reuse its local certificate configuration for workstation testing. You don't need that walkthrough's custom API app role or consent grant for this Microsoft Graph example.

## Add Microsoft Graph

Install the integration package:

```dotnetcli
dotnet add package Microsoft.Identity.Web.GraphServiceClient
```

Register `GraphServiceClient` with the services configured in the parent article. For app-only access, call `builder.Services.AddMicrosoftGraph` with `options.BaseUrl` set to `https://graph.microsoft.com/v1.0` and `options.Scopes` set to `["https://graph.microsoft.com/.default"]`. Use the configured client ID directly; don't add `WithAgentIdentity`.

Place this registration before `builder.Build()` in the agent API's `Program.cs`.

```csharp
builder.Services.AddMicrosoftGraph(options =>
{
    options.BaseUrl = "https://graph.microsoft.com/v1.0";
    options.Scopes = ["https://graph.microsoft.com/.default"];
});
```

## Call Microsoft Graph

Set `RequestAppToken` to `true` so `GraphServiceClient` acquires an app-only token for the agent identity:

Merge the following `using` directives with those at the top of `Program.cs`, and insert the endpoint before its single `app.Run()`. You can omit the custom API endpoint.

```csharp
using Microsoft.Graph;
using Microsoft.Identity.Web;

app.MapGet("/graph-users", async (GraphServiceClient graphClient) =>
{
    var users = await graphClient.Users.GetAsync(request =>
        request.Options.WithAuthenticationOptions(options =>
        {
            options.RequestAppToken = true;
        }));

    return Results.Ok(users?.Value);
})
.RequireAuthorization("AgentUser");
```

The client uses the shared client ID and blueprint credential configured in the parent article. Don't add an Agent ID override. The example requires an application permission that can list users, such as `User.Read.All`. Grant only the permissions required by your calls.

## Verify the Graph call

Follow the parent journey's [API access test](https://learn.microsoft.com/en-us/entra/agent-id/call-api-custom#verify-api-access), replacing `/custom-api` with `/graph-users`. Expect `200` and a JSON collection of users when the agent has the required Graph application permission. This endpoint returns the first response page, not necessarily every user in the directory.

Without an inbound token, expect `401`. With an otherwise valid token missing `Agent.User`, expect `403` if the tenant issues that token. A downstream Graph failure causes the sample to throw rather than returning that same status from the agent. Verify Graph consent on the agent identity separately from the caller's role assignment.

## Next step

[Authenticate users to the agent API](https://learn.microsoft.com/en-us/entra/agent-id/aspnet-core-authenticate-users)

## Related content

- [Call a custom API as an agent](https://learn.microsoft.com/en-us/entra/agent-id/call-api-custom)
- [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference)
- [Call Microsoft Graph as a user](https://learn.microsoft.com/en-us/entra/agent-id/aspnet-core-call-graph-as-user)
