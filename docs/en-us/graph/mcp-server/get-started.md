<!-- Source: https://learn.microsoft.com/en-us/graph/mcp-server/get-started -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Get started with the Microsoft MCP Server for Enterprise

To start using the Microsoft MCP Server for Enterprise, you must enable it in your tenant. This process currently provisions both the MCP Server and Visual Studio Code. After provisioning, you can configure your MCP client to connect to the MCP Server.

This article describes how to provision the MCP server and configure both VS Code and custom MCP clients to connect to the Microsoft MCP Server for Enterprise.

## Provision the MCP Server and VS Code \(only required once per tenant\)

1. Start PowerShell in Administrator mode and install **Microsoft.Entra.Beta** PowerShell module \(version 1.0.13 or later\):

   ```powershell
   Install-Module Microsoft.Entra.Beta -Force -AllowClobber
   ```

2. Authenticate into the tenant where you'd like to register the MCP Server. You must be assigned either the *Application Administrator* or *Cloud Application Administrator* role to consent to the required permissions:

   ```powershell
   Connect-Entra -Scopes 'Application.ReadWrite.All', 'Directory.Read.All', 'DelegatedPermissionGrant.ReadWrite.All'
   ```


   Tip


   Run `Get-EntraContext` after authentication to confirm the account, tenant, and scopes currently in use.

3. Register the Microsoft MCP Server for Enterprise in your tenant and grant all permissions to Visual Studio Code:

   ```powershell
   Grant-EntraBetaMCPServerPermission -ApplicationName VisualStudioCode
   ```

## Confirm the MCP server registration

Verify that both applications exist by using Microsoft Graph, Microsoft Entra PowerShell, or the Microsoft Entra portal.

| Name | Globally unique **appId** \(client ID\) |
| --- | --- |
| Microsoft MCP Server for Enterprise | `e8c77dc2-69b3-43f4-bc51-3213c9d915b4` |
| Visual Studio Code | `aebc6443-996d-45c2-90f0-388ff96faa56` |

- [Microsoft Graph - verify registration](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals?$select=id,appId,displayName&$filter=appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","appId","displayName" };
	requestConfiguration.QueryParameters.Filter = "appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  //other-imports
)


requestFilter := "appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')"

requestParameters := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetQueryParameters{
	Select: [] string {"id","appId","displayName"},
	Filter: &requestFilter,
}
configuration := &graphserviceprincipals.ServicePrincipalsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
servicePrincipals, err := graphClient.ServicePrincipals().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ServicePrincipalCollectionResponse result = graphClient.servicePrincipals().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "appId", "displayName"};
	requestConfiguration.queryParameters.filter = "appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let servicePrincipals = await client.api('/servicePrincipals')
	.filter('appId in(\'e8c77dc2-69b3-43f4-bc51-3213c9d915b4\',\'aebc6443-996d-45c2-90f0-388ff96faa56\')')
	.select('id,appId,displayName')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\ServicePrincipalsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ServicePrincipalsRequestBuilderGetRequestConfiguration();
$queryParameters = ServicePrincipalsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","appId","displayName"];
$queryParameters->filter = "appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->servicePrincipals()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgServicePrincipal -Property "id,appId,displayName" -Filter "appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.service_principals.service_principals_request_builder import ServicePrincipalsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ServicePrincipalsRequestBuilder.ServicePrincipalsRequestBuilderGetQueryParameters(
		select = ["id","appId","displayName"],
		filter = "appId in('e8c77dc2-69b3-43f4-bc51-3213c9d915b4','aebc6443-996d-45c2-90f0-388ff96faa56')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.service_principals.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Confirm permissions granted to your MCP clients

Validate the Microsoft MCP Server permissions that were granted to each MCP client.

- [Microsoft Graph - verify permissions](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/oauth2PermissionGrants?$select=id,clientId,resourceId,scope&$filter=clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Oauth2PermissionGrants.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","clientId","resourceId","scope" };
	requestConfiguration.QueryParameters.Filter = "clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphoauth2permissiongrants "github.com/microsoftgraph/msgraph-sdk-go/oauth2permissiongrants"
	  //other-imports
)


requestFilter := "clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'"

requestParameters := &graphoauth2permissiongrants.Oauth2PermissionGrantsRequestBuilderGetQueryParameters{
	Select: [] string {"id","clientId","resourceId","scope"},
	Filter: &requestFilter,
}
configuration := &graphoauth2permissiongrants.Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oauth2PermissionGrants, err := graphClient.Oauth2PermissionGrants().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OAuth2PermissionGrantCollectionResponse result = graphClient.oauth2PermissionGrants().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "clientId", "resourceId", "scope"};
	requestConfiguration.queryParameters.filter = "clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let oauth2PermissionGrants = await client.api('/oauth2PermissionGrants')
	.filter('clientId eq \'{mcp-client-servicePrincipal}\' and resourceId eq \'{mcp-server-servicePrincipal}\'')
	.select('id,clientId,resourceId,scope')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Oauth2PermissionGrants\Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration();
$queryParameters = Oauth2PermissionGrantsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","clientId","resourceId","scope"];
$queryParameters->filter = "clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->oauth2PermissionGrants()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgOauth2PermissionGrant -Property "id,clientId,resourceId,scope" -Filter "clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.oauth2_permission_grants.oauth2_permission_grants_request_builder import Oauth2PermissionGrantsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = Oauth2PermissionGrantsRequestBuilder.Oauth2PermissionGrantsRequestBuilderGetQueryParameters(
		select = ["id","clientId","resourceId","scope"],
		filter = "clientId eq '{mcp-client-servicePrincipal}' and resourceId eq '{mcp-server-servicePrincipal}'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.oauth2_permission_grants.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Connect your MCP client to the MCP Server

- [VS Code](#tabpanel_3_vscode)
- [Custom MCP clients](#tabpanel_3_custom-clients)

1. Click [Install Microsoft MCP Server for Enterprise](https://vscode.dev/redirect/mcp/install?name=Microsoft%20MCP%20Server%20for%20Enterprise&config=%7b%22name%22:%22Microsoft%20MCP%20Server%20for%20Enterprise%22%2c%22type%22:%22http%22%2c%22url%22:%22https://mcp.svc.cloud.microsoft/enterprise%22%7d) to open VS Code's MCP install page.
2. Select **Install** in VS Code and authenticate with an administrator account.
3. Open Copilot Chat in **Agent** mode and ask a tenant-specific question such as "How many users are in my tenant?"

   1. Review the MCP Server response, which includes:

      1. The tools that were invoked to understand the intent.
      2. The Microsoft Graph REST API call that was executed.
      3. A natural language answer that summarizes the tenant data.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with an account that can register applications \(*Application Administrator* or *Cloud Application Administrator* roles are sufficient\).
2. Register an application and consider the following settings:

   1. Application name.
   2. Supported account types \(Single tenant\).
   3. Platform and redirect URI for your MCP client.

3. Record both the **Application \(client\) ID** and the **Directory \(tenant\) ID** for later configuration.
4. To grant permissions:

   1. Select **Delegated permissions** and add the scopes that match your scenario \(for example, add `MCP.User.Read.All` to count users in the tenant\).
   2. Grant admin consent for the delegated permissions that you added.

5. Test your MCP client to confirm it can connect to the Microsoft MCP Server for Enterprise and complete the required operations.

Manage scopes for custom MCP clients by using Microsoft Entra PowerShell:

```powershell
Grant-EntraBetaMCPServerPermission -ApplicationId "<MCP_Client_Application_Id>" -Scopes "<Scope1>", "<Scope2>", "<...>"
Revoke-EntraBetaMCPServerPermission -ApplicationId "<MCP_Client_Application_Id>" -Scopes "<Scope1>", "<Scope2>", "<...>"
```

## View supported MCP Server scopes

The MCP Server supports only delegated permissions for user-interactive scenarios. App-only permissions or app-only workflows aren't supported. Use one of the following options \(requires at least the `DelegatedPermissionGrant.Read.All` delegated permission\) to inspect the available MCP scopes, and focus on scopes where `isEnabled` is `true`.

- [Microsoft Graph - list MCP scopes](#tabpanel_4_http)

```msgraph
GET https://graph.microsoft.com/v1.0/servicePrincipals(appId='e8c77dc2-69b3-43f4-bc51-3213c9d915b4')/oauth2PermissionScopes
```

## List of MCP Server scopes

The naming of MCP scopes follows the pattern `MCP.{microsoft-graph-scope-name}`. For example, the [User.Read.All](https://learn.microsoft.com/en-us/graph/permissions-reference#userreadall) Microsoft Graph scope is exposed as `MCP.User.Read.All` on the MCP Server. To understand what each scope allows, refer back to the [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

- MCP.AccessReview.Read.All
- MCP.AdministrativeUnit.Read.All
- MCP.Application.Read.All
- MCP.AuditLog.Read.All
- MCP.AuthenticationContext.Read.All
- MCP.DelegatedPermissionGrant.Read.All
- MCP.Device.Read.All
- MCP.DirectoryRecommendations.Read.All
- MCP.Domain.Read.All
- MCP.EntitlementManagement.Read.All
- MCP.Group.Read.All
- MCP.GroupMember.Read.All
- MCP.GroupSettings.Read.All
- MCP.HealthMonitoringAlert.Read.All
- MCP.IdentityRiskEvent.Read.All
- MCP.IdentityRiskyServicePrincipal.Read.All
- MCP.IdentityRiskyUser.Read.All
- MCP.LicenseAssignment.Read.All
- MCP.LifecycleWorkflows.Read.All
- MCP.LifecycleWorkflows-CustomExt.Read.All
- MCP.LifecycleWorkflows-Reports.Read.All
- MCP.LifecycleWorkflows-Workflow.Read.All
- MCP.LifecycleWorkflows-Workflow.ReadBasic.All
- MCP.NetworkAccess.Read.All
- MCP.NetworkAccess-Reports.Read.All
- MCP.Organization.Read.All
- MCP.OrgContact.Read.All
- MCP.Policy.Read.All
- MCP.Policy.Read.ConditionalAccess
- MCP.ProvisioningLog.Read.All
- MCP.Reports.Read.All
- MCP.RoleAssignmentSchedule.Read.Directory
- MCP.RoleEligibilitySchedule.Read.Directory
- MCP.RoleManagement.Read.Directory
- MCP.SecurityAlert.Read.All
- MCP.SecurityIncident.Read.All
- MCP.ServiceHealth.Read.All
- MCP.ServiceMessage.Read.All
- MCP.Synchronization.Read.All
- MCP.User.Read.All
- MCP.UserAuthenticationMethod.Read.All

## Disable the MCP Server for Enterprise

Because the MCP Server for Enterprise is a Microsoft-owned service, you can't delete it from your tenant. However, you can disable it if needed.

- [Microsoft Graph - disable MCP server](#tabpanel_5_http)

```http
PATCH https://graph.microsoft.com/v1.0/servicePrincipals(appId='e8c77dc2-69b3-43f4-bc51-3213c9d915b4')
{
  "accountEnabled": false
}
```
