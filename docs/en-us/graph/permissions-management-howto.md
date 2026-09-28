<!-- Source: https://learn.microsoft.com/en-us/graph/permissions-management-howto -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Permissions Management API operations for Azure, AWS, and GCP authorization systems

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

The permissions management APIs enable you to discover permissions assigned to all identities across multiple clouds; request permissions; approve, reject, and cancel permissions requests. This article provides a quick reference guide for [Microsoft Graph API operations](https://learn.microsoft.com/en-us/graph/api/resources/permissions-management-api-overview?view=graph-rest-beta&preserve-view=true) on the supported authorization systems.

## Get all authorization systems

List all authorization systems onboarded to Permissions Management.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems
```

Filter authorization systems by name.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=contains(authorizationSystemName, 'cloud')
```

## Get an authorization system

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}
```

---

## List Azure authorization systems

List Azure authorization systems onboarded to Permissions Management by filtering by the **authorizationSystemType** property.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=authorizationSystemType eq 'azure'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "authorizationSystemType eq 'azure'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-beta-sdk-go/external"
	  //other-imports
)


requestFilter := "authorizationSystemType eq 'azure'"

requestParameters := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystemCollectionResponse result = graphClient.external().authorizationSystems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "authorizationSystemType eq 'azure'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystems = await client.api('/external/authorizationSystems')
	.version('beta')
	.filter('authorizationSystemType eq \'azure\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\External\AuthorizationSystems\AuthorizationSystemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthorizationSystemsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthorizationSystemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "authorizationSystemType eq 'azure'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->external()->authorizationSystems()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -Filter "authorizationSystemType eq 'azure'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.external.authorization_systems.authorization_systems_request_builder import AuthorizationSystemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthorizationSystemsRequestBuilder.AuthorizationSystemsRequestBuilderGetQueryParameters(
		filter = "authorizationSystemType eq 'azure'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.external.authorization_systems.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List Azure authorization systems onboarded to Permissions Management.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/microsoft.graph.azureAuthorizationSystem
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems["{authorizationSystem-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().ByAuthorizationSystemId("authorizationSystem-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystem result = graphClient.external().authorizationSystems().byAuthorizationSystemId("{authorizationSystem-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureAuthorizationSystem = await client.api('/external/authorizationSystems/microsoft.graph.azureAuthorizationSystem')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->external()->authorizationSystems()->byAuthorizationSystemId('authorizationSystem-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -AuthorizationSystemId $authorizationSystemId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.external.authorization_systems.by_authorization_system_id('authorizationSystem-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Identify all Azure authorization systems that are online and have permissions modification capability enabled.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-beta-sdk-go/external"
	  //other-imports
)


requestFilter := "authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'"

requestParameters := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystemCollectionResponse result = graphClient.external().authorizationSystems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystems = await client.api('/external/authorizationSystems')
	.version('beta')
	.filter('authorizationSystemType eq \'azure\' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq \'enabled\' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq \'online\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\External\AuthorizationSystems\AuthorizationSystemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthorizationSystemsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthorizationSystemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->external()->authorizationSystems()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -Filter "authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.external.authorization_systems.authorization_systems_request_builder import AuthorizationSystemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthorizationSystemsRequestBuilder.AuthorizationSystemsRequestBuilderGetQueryParameters(
		filter = "authorizationSystemType eq 'azure' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.external.authorization_systems.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get identities in an Azure authorization system

### List all identities

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let all = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one identity

By primary key ID.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureIdentity = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/all(externalId='{externalId}')
```

## Get Azure managed identities

### List all Azure managed identities

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/managedIdentities
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let managedIdentities = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/managedIdentities')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one Azure managed identity

By primary key managed identity ID.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/managedIdentities/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureManagedIdentity = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/managedIdentities/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/managedIdentities(externalId='{externalId}')
```

## Get Azure users

### List all Azure users

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/users
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/users')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one Azure user

By primary key user ID.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/users/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureUser = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/users/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/users(externalId='{externalId}')
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureUser = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/users/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get Azure service principals

### List all Azure service principals

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/servicePrincipals
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let servicePrincipals = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/servicePrincipals')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one Azure service principal

By primary key user ID.

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/servicePrincipals/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureServicePrincipal = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/servicePrincipals/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

- [HTTP](#tabpanel_13_http)
- [C#](#tabpanel_13_csharp)
- [Go](#tabpanel_13_go)
- [Java](#tabpanel_13_java)
- [JavaScript](#tabpanel_13_javascript)
- [PHP](#tabpanel_13_php)
- [PowerShell](#tabpanel_13_powershell)
- [Python](#tabpanel_13_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/servicePrincipals(externalId='{externalId}')
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureServicePrincipal = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/associatedIdentities/servicePrincipals/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get actions

### List all actions

List all actions.

- [HTTP](#tabpanel_14_http)
- [C#](#tabpanel_14_csharp)
- [Go](#tabpanel_14_go)
- [Java](#tabpanel_14_java)
- [JavaScript](#tabpanel_14_javascript)
- [PHP](#tabpanel_14_php)
- [PowerShell](#tabpanel_14_powershell)
- [Python](#tabpanel_14_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List actions for a specific service in an Azure authorization system.

- [HTTP](#tabpanel_15_http)
- [C#](#tabpanel_15_csharp)
- [Go](#tabpanel_15_go)
- [Java](#tabpanel_15_java)
- [JavaScript](#tabpanel_15_javascript)
- [PHP](#tabpanel_15_php)
- [PowerShell](#tabpanel_15_powershell)
- [Python](#tabpanel_15_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions?$filter=service/id eq 'Microsoft.Storage'
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions')
	.version('beta')
	.filter('service/id eq \'Microsoft.Storage\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List high-risk delete actions for a specific service in the Azure authorization system

- [HTTP](#tabpanel_16_http)
- [C#](#tabpanel_16_csharp)
- [Go](#tabpanel_16_go)
- [Java](#tabpanel_16_java)
- [JavaScript](#tabpanel_16_javascript)
- [PHP](#tabpanel_16_php)
- [PowerShell](#tabpanel_16_powershell)
- [Python](#tabpanel_16_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions?$filter=service/id eq 'Microsoft.Storage' and severity eq 'high' and actionType eq 'delete'
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions')
	.version('beta')
	.filter('service/id eq \'Microsoft.Storage\' and severity eq \'high\' and actionType eq \'delete\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get an action

By primary key action ID.

- [HTTP](#tabpanel_17_http)
- [C#](#tabpanel_17_csharp)
- [Go](#tabpanel_17_go)
- [Java](#tabpanel_17_java)
- [JavaScript](#tabpanel_17_javascript)
- [PHP](#tabpanel_17_php)
- [PowerShell](#tabpanel_17_powershell)
- [Python](#tabpanel_17_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureAuthorizationSystemTypeAction = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/actions(externalId={externalId})
```

## Get resources

### List all resources

- [HTTP](#tabpanel_18_http)
- [C#](#tabpanel_18_csharp)
- [Go](#tabpanel_18_go)
- [Java](#tabpanel_18_java)
- [JavaScript](#tabpanel_18_javascript)
- [PHP](#tabpanel_18_php)
- [PowerShell](#tabpanel_18_powershell)
- [Python](#tabpanel_18_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/resources
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let resources = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/resources')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a resource

By primary key resource ID.

- [HTTP](#tabpanel_19_http)
- [C#](#tabpanel_19_csharp)
- [Go](#tabpanel_19_go)
- [Java](#tabpanel_19_java)
- [JavaScript](#tabpanel_19_javascript)
- [PHP](#tabpanel_19_php)
- [PowerShell](#tabpanel_19_powershell)
- [Python](#tabpanel_19_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/resources/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureAuthorizationSystemResource = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/resources/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/resources(externalId={externalId})
```

## Get role definition

### List all role definitions

List all role definitions.

- [HTTP](#tabpanel_20_http)
- [C#](#tabpanel_20_csharp)
- [Go](#tabpanel_20_go)
- [Java](#tabpanel_20_java)
- [JavaScript](#tabpanel_20_javascript)
- [PHP](#tabpanel_20_php)
- [PowerShell](#tabpanel_20_powershell)
- [Python](#tabpanel_20_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/roleDefinitions
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleDefinitions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/roleDefinitions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List all role definitions by assignable scopes.

- [HTTP](#tabpanel_21_http)
- [C#](#tabpanel_21_csharp)
- [Go](#tabpanel_21_go)
- [Java](#tabpanel_21_java)
- [JavaScript](#tabpanel_21_javascript)
- [PHP](#tabpanel_21_php)
- [PowerShell](#tabpanel_21_powershell)
- [Python](#tabpanel_21_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{computedId}/graph.azureAuthorizationSystem/roleDefinitions?$filter=assignableScopes/any(p:p eq '/' or '/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee' or '/subscriptions/e160b34b-2a0f-41f6-aaf3-09c5a9f43768/resourceGroups/2eResourceGroup')
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleDefinitions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/roleDefinitions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a role definition

By primary key role definition ID assigned by Permissions Management.

- [HTTP](#tabpanel_22_http)
- [C#](#tabpanel_22_csharp)
- [Go](#tabpanel_22_go)
- [Java](#tabpanel_22_java)
- [JavaScript](#tabpanel_22_javascript)
- [PHP](#tabpanel_22_php)
- [PowerShell](#tabpanel_22_powershell)
- [Python](#tabpanel_22_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/roleDefinitions/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let azureRoleDefinition = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/roleDefinitions/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId which is the globally unique ID of the role in Microsoft Azure.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/policies(externalId='{externalId}')
```

## Get services

### List all services

- [HTTP](#tabpanel_23_http)
- [C#](#tabpanel_23_csharp)
- [Go](#tabpanel_23_go)
- [Java](#tabpanel_23_java)
- [JavaScript](#tabpanel_23_javascript)
- [PHP](#tabpanel_23_php)
- [PowerShell](#tabpanel_23_powershell)
- [Python](#tabpanel_23_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/services
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let services = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/services')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a service

- [HTTP](#tabpanel_24_http)
- [C#](#tabpanel_24_csharp)
- [Go](#tabpanel_24_go)
- [Java](#tabpanel_24_java)
- [JavaScript](#tabpanel_24_javascript)
- [PHP](#tabpanel_24_php)
- [PowerShell](#tabpanel_24_powershell)
- [Python](#tabpanel_24_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/services/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystemTypeService = await client.api('/external/authorizationSystems/{id}/microsoft.graph.azureAuthorizationSystem/services/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Request an Azure action

- [HTTP](#tabpanel_25_http)
- [C#](#tabpanel_25_csharp)
- [Go](#tabpanel_25_go)
- [Java](#tabpanel_25_java)
- [JavaScript](#tabpanel_25_javascript)
- [PHP](#tabpanel_25_php)
- [PowerShell](#tabpanel_25_powershell)
- [Python](#tabpanel_25_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceAzurePermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "87eefd90-95a3-480a-ba42-56ff299a05ee",
      "authorizationSystemType": "AZURE"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.azureActionPermissionsDefinitionAction",
      "actions": ["Microsoft.Authorization/roleassignments/read", "Microsoft.Authorization/roleassignments/write"]
    },
    "identityInfo": {
      "externalId": "alex@adatum.com"",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
  },
  "justification": "I need to do this because I want to access AAD resources",
  "notes": "Pretty Pleaseeeee",
  "scheduleInfo": {
    "startDateTime": null,
    "expiration": {
      "duration": "PT1H"
    },
    "recurrence": null
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.singleResourceAzurePermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: '87eefd90-95a3-480a-ba42-56ff299a05ee',
      authorizationSystemType: 'AZURE'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.azureActionPermissionsDefinitionAction',
      actions: ['Microsoft.Authorization/roleassignments/read', 'Microsoft.Authorization/roleassignments/write']
    },
    identityInfo: {
      externalId: 'alex@adatum.com'",
      source: {
        '@odata.type': 'microsoft.graph.edIdentitySource'
      },
      identityType: 'user'
    },
    resourceId: '/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee'
  },
  justification: 'I need to do this because I want to access AAD resources',
  notes: 'Pretty Pleaseeeee',
  scheduleInfo: {
    startDateTime: null,
    expiration: {
      duration: 'PT1H'
    },
    recurrence: null
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Request an Azure role

- [HTTP](#tabpanel_26_http)
- [C#](#tabpanel_26_csharp)
- [Go](#tabpanel_26_go)
- [Java](#tabpanel_26_java)
- [JavaScript](#tabpanel_26_javascript)
- [PHP](#tabpanel_26_php)
- [PowerShell](#tabpanel_26_powershell)
- [Python](#tabpanel_26_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceAzurePermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "87eefd90-95a3-480a-ba42-56ff299a05ee",
      "authorizationSystemType": "AZURE"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.azureRolePermissionsDefinitionAction",
      "roles": [
        {
          "id": "cdda3590-29a3-44f6-95f2-9f980659eb04"
        },
        {
          "id": "312a565d-c81f-4fd8-895a-4e21e48d571c"
        }
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
  },
  "justification": "I need to do this because I want to some new azure roles",
  "notes": "Pretty Pleaseeeee",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    },
    "recurrence": null
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new SingleResourceAzurePermissionsDefinition
	{
		OdataType = "microsoft.graph.singleResourceAzurePermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "87eefd90-95a3-480a-ba42-56ff299a05ee",
			AuthorizationSystemType = "AZURE",
		},
		ActionInfo = new AzureRolePermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.azureRolePermissionsDefinitionAction",
			Roles = new List<PermissionsDefinitionAzureRole>
			{
				new PermissionsDefinitionAzureRole
				{
					Id = "cdda3590-29a3-44f6-95f2-9f980659eb04",
				},
				new PermissionsDefinitionAzureRole
				{
					Id = "312a565d-c81f-4fd8-895a-4e21e48d571c",
				},
			},
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new EdIdentitySource
			{
				OdataType = "microsoft.graph.edIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
		ResourceId = "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee",
	},
	Justification = "I need to do this because I want to some new azure roles",
	Notes = "Pretty Pleaseeeee",
	ScheduleInfo = new RequestSchedule
	{
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
		Recurrence = null,
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewSingleResourceAzurePermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "87eefd90-95a3-480a-ba42-56ff299a05ee"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "AZURE"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewAzureRolePermissionsDefinitionAction()


permissionsDefinitionAzureRole := graphmodels.NewPermissionsDefinitionAzureRole()
id := "cdda3590-29a3-44f6-95f2-9f980659eb04"
permissionsDefinitionAzureRole.SetId(&id) 
permissionsDefinitionAzureRole1 := graphmodels.NewPermissionsDefinitionAzureRole()
id := "312a565d-c81f-4fd8-895a-4e21e48d571c"
permissionsDefinitionAzureRole1.SetId(&id) 

roles := []graphmodels.PermissionsDefinitionAzureRoleable {
	permissionsDefinitionAzureRole,
	permissionsDefinitionAzureRole1,
}
actionInfo.SetRoles(roles)
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewEdIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
resourceId := "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
requestedPermissions.SetResourceId(&resourceId) 
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to some new azure roles"
requestBody.SetJustification(&justification) 
notes := "Pretty Pleaseeeee"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
recurrence := null
scheduleInfo.SetRecurrence(&recurrence) 
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
SingleResourceAzurePermissionsDefinition requestedPermissions = new SingleResourceAzurePermissionsDefinition();
requestedPermissions.setOdataType("microsoft.graph.singleResourceAzurePermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("87eefd90-95a3-480a-ba42-56ff299a05ee");
authorizationSystemInfo.setAuthorizationSystemType("AZURE");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
AzureRolePermissionsDefinitionAction actionInfo = new AzureRolePermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.azureRolePermissionsDefinitionAction");
LinkedList<PermissionsDefinitionAzureRole> roles = new LinkedList<PermissionsDefinitionAzureRole>();
PermissionsDefinitionAzureRole permissionsDefinitionAzureRole = new PermissionsDefinitionAzureRole();
permissionsDefinitionAzureRole.setId("cdda3590-29a3-44f6-95f2-9f980659eb04");
roles.add(permissionsDefinitionAzureRole);
PermissionsDefinitionAzureRole permissionsDefinitionAzureRole1 = new PermissionsDefinitionAzureRole();
permissionsDefinitionAzureRole1.setId("312a565d-c81f-4fd8-895a-4e21e48d571c");
roles.add(permissionsDefinitionAzureRole1);
actionInfo.setRoles(roles);
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
EdIdentitySource source = new EdIdentitySource();
source.setOdataType("microsoft.graph.edIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
requestedPermissions.setResourceId("/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee");
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to some new azure roles");
scheduledPermissionsRequest.setNotes("Pretty Pleaseeeee");
RequestSchedule scheduleInfo = new RequestSchedule();
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduleInfo.setRecurrence(null);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.singleResourceAzurePermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: '87eefd90-95a3-480a-ba42-56ff299a05ee',
      authorizationSystemType: 'AZURE'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.azureRolePermissionsDefinitionAction',
      roles: [
        {
          id: 'cdda3590-29a3-44f6-95f2-9f980659eb04'
        },
        {
          id: '312a565d-c81f-4fd8-895a-4e21e48d571c'
        }
      ]
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.edIdentitySource'
      },
      identityType: 'user'
    },
    resourceId: '/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee'
  },
  justification: 'I need to do this because I want to some new azure roles',
  notes: 'Pretty Pleaseeeee',
  scheduleInfo: {
    expiration: {
      duration: 'PT1H'
    },
    recurrence: null
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\SingleResourceAzurePermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\AzureRolePermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAzureRole;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\EdIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new SingleResourceAzurePermissionsDefinition();
$requestedPermissions->setOdataType('microsoft.graph.singleResourceAzurePermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('87eefd90-95a3-480a-ba42-56ff299a05ee');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('AZURE');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new AzureRolePermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.azureRolePermissionsDefinitionAction');
$rolesPermissionsDefinitionAzureRole1 = new PermissionsDefinitionAzureRole();
$rolesPermissionsDefinitionAzureRole1->setId('cdda3590-29a3-44f6-95f2-9f980659eb04');
$rolesArray []= $rolesPermissionsDefinitionAzureRole1;
$rolesPermissionsDefinitionAzureRole2 = new PermissionsDefinitionAzureRole();
$rolesPermissionsDefinitionAzureRole2->setId('312a565d-c81f-4fd8-895a-4e21e48d571c');
$rolesArray []= $rolesPermissionsDefinitionAzureRole2;
$requestedPermissionsActionInfo->setRoles($rolesArray);

$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new EdIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.edIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestedPermissions->setResourceId('/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee');
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to some new azure roles');
$requestBody->setNotes('Pretty Pleaseeeee');
$scheduleInfo = new RequestSchedule();
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$scheduleInfo->setRecurrence(null);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "microsoft.graph.singleResourceAzurePermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "87eefd90-95a3-480a-ba42-56ff299a05ee"
			authorizationSystemType = "AZURE"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.azureRolePermissionsDefinitionAction"
			roles = @(
				@{
					id = "cdda3590-29a3-44f6-95f2-9f980659eb04"
				}
				@{
					id = "312a565d-c81f-4fd8-895a-4e21e48d571c"
				}
			)
		}
		identityInfo = @{
			externalId = "alex@contoso.com"
			source = @{
				"@odata.type" = "microsoft.graph.edIdentitySource"
			}
			identityType = "user"
		}
		resourceId = "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee"
	}
	justification = "I need to do this because I want to some new azure roles"
	notes = "Pretty Pleaseeeee"
	scheduleInfo = @{
		expiration = @{
			duration = "PT1H"
		}
		recurrence = $null
	}
	ticketInfo = @{
		ticketNumber = "INC1234567"
		ticketSystem = "ServiceNow"
		ticketSubmitterIdentityId = "alex@contoso.com"
		ticketApproverIdentityId = "alexmanager@contoso.com"
	}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.single_resource_azure_permissions_definition import SingleResourceAzurePermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.azure_role_permissions_definition_action import AzureRolePermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_azure_role import PermissionsDefinitionAzureRole
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.ed_identity_source import EdIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = SingleResourceAzurePermissionsDefinition(
		odata_type = "microsoft.graph.singleResourceAzurePermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "87eefd90-95a3-480a-ba42-56ff299a05ee",
			authorization_system_type = "AZURE",
		),
		action_info = AzureRolePermissionsDefinitionAction(
			odata_type = "microsoft.graph.azureRolePermissionsDefinitionAction",
			roles = [
				PermissionsDefinitionAzureRole(
					id = "cdda3590-29a3-44f6-95f2-9f980659eb04",
				),
				PermissionsDefinitionAzureRole(
					id = "312a565d-c81f-4fd8-895a-4e21e48d571c",
				),
			],
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = EdIdentitySource(
				odata_type = "microsoft.graph.edIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
		resource_id = "/subscriptions/87eefd90-95a3-480a-ba42-56ff299a05ee",
	),
	justification = "I need to do this because I want to some new azure roles",
	notes = "Pretty Pleaseeeee",
	schedule_info = RequestSchedule(
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
		recurrence = None,
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## List AWS authorization systems

List AWS authorization systems onboarded to Permissions Management by filtering by the **authorizationSystemType** property.

- [HTTP](#tabpanel_27_http)
- [C#](#tabpanel_27_csharp)
- [Go](#tabpanel_27_go)
- [Java](#tabpanel_27_java)
- [JavaScript](#tabpanel_27_javascript)
- [PHP](#tabpanel_27_php)
- [PowerShell](#tabpanel_27_powershell)
- [Python](#tabpanel_27_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=authorizationSystemType eq 'aws'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "authorizationSystemType eq 'aws'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-beta-sdk-go/external"
	  //other-imports
)


requestFilter := "authorizationSystemType eq 'aws'"

requestParameters := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystemCollectionResponse result = graphClient.external().authorizationSystems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "authorizationSystemType eq 'aws'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystems = await client.api('/external/authorizationSystems')
	.version('beta')
	.filter('authorizationSystemType eq \'aws\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\External\AuthorizationSystems\AuthorizationSystemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthorizationSystemsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthorizationSystemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "authorizationSystemType eq 'aws'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->external()->authorizationSystems()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -Filter "authorizationSystemType eq 'aws'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.external.authorization_systems.authorization_systems_request_builder import AuthorizationSystemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthorizationSystemsRequestBuilder.AuthorizationSystemsRequestBuilderGetQueryParameters(
		filter = "authorizationSystemType eq 'aws'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.external.authorization_systems.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List AWS authorization systems onboarded to Permissions Management.

- [HTTP](#tabpanel_28_http)
- [C#](#tabpanel_28_csharp)
- [Go](#tabpanel_28_go)
- [Java](#tabpanel_28_java)
- [JavaScript](#tabpanel_28_javascript)
- [PHP](#tabpanel_28_php)
- [PowerShell](#tabpanel_28_powershell)
- [Python](#tabpanel_28_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/microsoft.graph.awsAuthorizationSystem
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems["{authorizationSystem-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().ByAuthorizationSystemId("authorizationSystem-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystem result = graphClient.external().authorizationSystems().byAuthorizationSystemId("{authorizationSystem-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsAuthorizationSystem = await client.api('/external/authorizationSystems/microsoft.graph.awsAuthorizationSystem')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->external()->authorizationSystems()->byAuthorizationSystemId('authorizationSystem-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -AuthorizationSystemId $authorizationSystemId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.external.authorization_systems.by_authorization_system_id('authorizationSystem-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Identify all AWS authorization systems that are online and have permissions modification capability enabled.

- [HTTP](#tabpanel_29_http)
- [C#](#tabpanel_29_csharp)
- [Go](#tabpanel_29_go)
- [Java](#tabpanel_29_java)
- [JavaScript](#tabpanel_29_javascript)
- [PHP](#tabpanel_29_php)
- [PowerShell](#tabpanel_29_powershell)
- [Python](#tabpanel_29_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-beta-sdk-go/external"
	  //other-imports
)


requestFilter := "authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'"

requestParameters := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystemCollectionResponse result = graphClient.external().authorizationSystems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystems = await client.api('/external/authorizationSystems')
	.version('beta')
	.filter('authorizationSystemType eq \'aws\' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq \'enabled\' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq \'online\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\External\AuthorizationSystems\AuthorizationSystemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthorizationSystemsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthorizationSystemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->external()->authorizationSystems()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -Filter "authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.external.authorization_systems.authorization_systems_request_builder import AuthorizationSystemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthorizationSystemsRequestBuilder.AuthorizationSystemsRequestBuilderGetQueryParameters(
		filter = "authorizationSystemType eq 'aws' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.external.authorization_systems.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get identities in an AWS authorization system

### List all identities

- [HTTP](#tabpanel_30_http)
- [C#](#tabpanel_30_csharp)
- [Go](#tabpanel_30_go)
- [Java](#tabpanel_30_java)
- [JavaScript](#tabpanel_30_javascript)
- [PHP](#tabpanel_30_php)
- [PowerShell](#tabpanel_30_powershell)
- [Python](#tabpanel_30_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/all
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let all = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/all')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one identity

By primary key ID.

- [HTTP](#tabpanel_31_http)
- [C#](#tabpanel_31_csharp)
- [Go](#tabpanel_31_go)
- [Java](#tabpanel_31_java)
- [JavaScript](#tabpanel_31_javascript)
- [PHP](#tabpanel_31_php)
- [PowerShell](#tabpanel_31_powershell)
- [Python](#tabpanel_31_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/all/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsIdentity = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/all/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/all(externalId='{externalId}')
```

## Get AWS roles

### List all AWS roles

- [HTTP](#tabpanel_32_http)
- [C#](#tabpanel_32_csharp)
- [Go](#tabpanel_32_go)
- [Java](#tabpanel_32_java)
- [JavaScript](#tabpanel_32_javascript)
- [PHP](#tabpanel_32_php)
- [PowerShell](#tabpanel_32_powershell)
- [Python](#tabpanel_32_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/roles
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roles = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/roles')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one AWS role

By primary key role ID.

- [HTTP](#tabpanel_33_http)
- [C#](#tabpanel_33_csharp)
- [Go](#tabpanel_33_go)
- [Java](#tabpanel_33_java)
- [JavaScript](#tabpanel_33_javascript)
- [PHP](#tabpanel_33_php)
- [PowerShell](#tabpanel_33_powershell)
- [Python](#tabpanel_33_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/roles/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsRole = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/roles/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/roles(externalId='{externalId}')
```

## Get AWS users

### List all AWS users

- [HTTP](#tabpanel_34_http)
- [C#](#tabpanel_34_csharp)
- [Go](#tabpanel_34_go)
- [Java](#tabpanel_34_java)
- [JavaScript](#tabpanel_34_javascript)
- [PHP](#tabpanel_34_php)
- [PowerShell](#tabpanel_34_powershell)
- [Python](#tabpanel_34_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one AWS user

By primary key user ID.

- [HTTP](#tabpanel_35_http)
- [C#](#tabpanel_35_csharp)
- [Go](#tabpanel_35_go)
- [Java](#tabpanel_35_java)
- [JavaScript](#tabpanel_35_javascript)
- [PHP](#tabpanel_35_php)
- [PowerShell](#tabpanel_35_powershell)
- [Python](#tabpanel_35_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsUser = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

- [HTTP](#tabpanel_36_http)
- [C#](#tabpanel_36_csharp)
- [Go](#tabpanel_36_go)
- [Java](#tabpanel_36_java)
- [JavaScript](#tabpanel_36_javascript)
- [PHP](#tabpanel_36_php)
- [PowerShell](#tabpanel_36_powershell)
- [Python](#tabpanel_36_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users(externalId='{externalId}')
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsUser = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### List assumable roles for an AWS user

- [HTTP](#tabpanel_37_http)
- [C#](#tabpanel_37_csharp)
- [Go](#tabpanel_37_go)
- [Java](#tabpanel_37_java)
- [JavaScript](#tabpanel_37_javascript)
- [PHP](#tabpanel_37_php)
- [PowerShell](#tabpanel_37_powershell)
- [Python](#tabpanel_37_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users/{id}/assumableRoles
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let assumableRoles = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/associatedIdentities/users/{id}/assumableRoles')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get actions

### List all actions

List all actions.

- [HTTP](#tabpanel_38_http)
- [C#](#tabpanel_38_csharp)
- [Go](#tabpanel_38_go)
- [Java](#tabpanel_38_java)
- [JavaScript](#tabpanel_38_javascript)
- [PHP](#tabpanel_38_php)
- [PowerShell](#tabpanel_38_powershell)
- [Python](#tabpanel_38_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List actions for a specific service in an AWS authorization system.

- [HTTP](#tabpanel_39_http)
- [C#](#tabpanel_39_csharp)
- [Go](#tabpanel_39_go)
- [Java](#tabpanel_39_java)
- [JavaScript](#tabpanel_39_javascript)
- [PHP](#tabpanel_39_php)
- [PowerShell](#tabpanel_39_powershell)
- [Python](#tabpanel_39_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions?$filter=service/id eq 'ec2'
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions')
	.version('beta')
	.filter('service/id eq \'ec2\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List high-risk delete actions for a specific service in the AWS authorization system

- [HTTP](#tabpanel_40_http)
- [C#](#tabpanel_40_csharp)
- [Go](#tabpanel_40_go)
- [Java](#tabpanel_40_java)
- [JavaScript](#tabpanel_40_javascript)
- [PHP](#tabpanel_40_php)
- [PowerShell](#tabpanel_40_powershell)
- [Python](#tabpanel_40_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions?$filter=service/id eq 'ec2' and severity eq 'high' and actionType eq 'delete'
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions')
	.version('beta')
	.filter('service/id eq \'ec2\' and severity eq \'high\' and actionType eq \'delete\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get an action

By primary key action ID.

- [HTTP](#tabpanel_41_http)
- [C#](#tabpanel_41_csharp)
- [Go](#tabpanel_41_go)
- [Java](#tabpanel_41_java)
- [JavaScript](#tabpanel_41_javascript)
- [PHP](#tabpanel_41_php)
- [PowerShell](#tabpanel_41_powershell)
- [Python](#tabpanel_41_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsAuthorizationSystemTypeAction = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/actions(externalId='{externalId}')
```

## Get policies

### List all policies

List all policies.

- [HTTP](#tabpanel_42_http)
- [C#](#tabpanel_42_csharp)
- [Go](#tabpanel_42_go)
- [Java](#tabpanel_42_java)
- [JavaScript](#tabpanel_42_javascript)
- [PHP](#tabpanel_42_php)
- [PowerShell](#tabpanel_42_powershell)
- [Python](#tabpanel_42_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let policies = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List all policies matching a specific policy name.

- [HTTP](#tabpanel_43_http)
- [C#](#tabpanel_43_csharp)
- [Go](#tabpanel_43_go)
- [Java](#tabpanel_43_java)
- [JavaScript](#tabpanel_43_javascript)
- [PHP](#tabpanel_43_php)
- [PowerShell](#tabpanel_43_powershell)
- [Python](#tabpanel_43_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies?$filter=displayName eq 'AdministratorAccess'
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let policies = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies')
	.version('beta')
	.filter('displayName eq \'AdministratorAccess\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List all policies where the policy name contains a specific string.

- [HTTP](#tabpanel_44_http)
- [C#](#tabpanel_44_csharp)
- [Go](#tabpanel_44_go)
- [Java](#tabpanel_44_java)
- [JavaScript](#tabpanel_44_javascript)
- [PHP](#tabpanel_44_php)
- [PowerShell](#tabpanel_44_powershell)
- [Python](#tabpanel_44_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies?$filter=contains(displayName, 'Buckets')
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let policies = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies')
	.version('beta')
	.filter('contains(displayName, \'Buckets\')')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List all custom policies.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies?$filter=type eq 'custom'
```

### Get a policy

By primary key policy ID.

- [HTTP](#tabpanel_45_http)
- [C#](#tabpanel_45_csharp)
- [Go](#tabpanel_45_go)
- [Java](#tabpanel_45_java)
- [JavaScript](#tabpanel_45_javascript)
- [PHP](#tabpanel_45_php)
- [PowerShell](#tabpanel_45_powershell)
- [Python](#tabpanel_45_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsPolicy = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/policies(externalId='{externalId}')
```

## Get resources

### List all resources

- [HTTP](#tabpanel_46_http)
- [C#](#tabpanel_46_csharp)
- [Go](#tabpanel_46_go)
- [Java](#tabpanel_46_java)
- [JavaScript](#tabpanel_46_javascript)
- [PHP](#tabpanel_46_php)
- [PowerShell](#tabpanel_46_powershell)
- [Python](#tabpanel_46_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/resources
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let resources = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/resources')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a resource

By primary key resource ID.

- [HTTP](#tabpanel_47_http)
- [C#](#tabpanel_47_csharp)
- [Go](#tabpanel_47_go)
- [Java](#tabpanel_47_java)
- [JavaScript](#tabpanel_47_javascript)
- [PHP](#tabpanel_47_php)
- [PowerShell](#tabpanel_47_powershell)
- [Python](#tabpanel_47_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/resources/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsAuthorizationSystemResource = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/resources/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/resources(externalId='{externalId}')
```

## Get services

### List all services

- [HTTP](#tabpanel_48_http)
- [C#](#tabpanel_48_csharp)
- [Go](#tabpanel_48_go)
- [Java](#tabpanel_48_java)
- [JavaScript](#tabpanel_48_javascript)
- [PHP](#tabpanel_48_php)
- [PowerShell](#tabpanel_48_powershell)
- [Python](#tabpanel_48_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/services
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let services = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/services')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a service

- [HTTP](#tabpanel_49_http)
- [C#](#tabpanel_49_csharp)
- [Go](#tabpanel_49_go)
- [Java](#tabpanel_49_java)
- [JavaScript](#tabpanel_49_javascript)
- [PHP](#tabpanel_49_php)
- [PowerShell](#tabpanel_49_powershell)
- [Python](#tabpanel_49_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/services/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystemTypeService = await client.api('/external/authorizationSystems/{id}/microsoft.graph.awsAuthorizationSystem/services/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Request an AWS policy

- [HTTP](#tabpanel_50_http)
- [C#](#tabpanel_50_csharp)
- [Go](#tabpanel_50_go)
- [Java](#tabpanel_50_java)
- [JavaScript](#tabpanel_50_javascript)
- [PHP](#tabpanel_50_php)
- [PowerShell](#tabpanel_50_powershell)
- [Python](#tabpanel_50_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "#microsoft.graph.awsPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "956987887735",
      "authorizationSystemType": "AWS"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.awsPolicyPermissionsDefinitionAction",
      "policies": [
        {
          "id": "arn:aws:iam::956987887735:policy/AddUserToGroup"
        }
      ],
      "assignToRoleId": "arn:aws:aim::956987887735:role/saml-user"
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.samlIdentitySource"
      },
      "identityType": "user"
    }
  },
  "justification": "I need to do this because I want to add a user to a group",
  "notes": "Pretty Please",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    }
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new AwsPermissionsDefinition
	{
		OdataType = "#microsoft.graph.awsPermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "956987887735",
			AuthorizationSystemType = "AWS",
		},
		ActionInfo = new AwsPolicyPermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.awsPolicyPermissionsDefinitionAction",
			Policies = new List<PermissionsDefinitionAwsPolicy>
			{
				new PermissionsDefinitionAwsPolicy
				{
					Id = "arn:aws:iam::956987887735:policy/AddUserToGroup",
				},
			},
			AssignToRoleId = "arn:aws:aim::956987887735:role/saml-user",
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new SamlIdentitySource
			{
				OdataType = "microsoft.graph.samlIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
	},
	Justification = "I need to do this because I want to add a user to a group",
	Notes = "Pretty Please",
	ScheduleInfo = new RequestSchedule
	{
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewAwsPermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "956987887735"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "AWS"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewAwsPolicyPermissionsDefinitionAction()


permissionsDefinitionAwsPolicy := graphmodels.NewPermissionsDefinitionAwsPolicy()
id := "arn:aws:iam::956987887735:policy/AddUserToGroup"
permissionsDefinitionAwsPolicy.SetId(&id) 

policies := []graphmodels.PermissionsDefinitionAwsPolicyable {
	permissionsDefinitionAwsPolicy,
}
actionInfo.SetPolicies(policies)
assignToRoleId := "arn:aws:aim::956987887735:role/saml-user"
actionInfo.SetAssignToRoleId(&assignToRoleId) 
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewSamlIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to add a user to a group"
requestBody.SetJustification(&justification) 
notes := "Pretty Please"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
AwsPermissionsDefinition requestedPermissions = new AwsPermissionsDefinition();
requestedPermissions.setOdataType("#microsoft.graph.awsPermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("956987887735");
authorizationSystemInfo.setAuthorizationSystemType("AWS");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
AwsPolicyPermissionsDefinitionAction actionInfo = new AwsPolicyPermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.awsPolicyPermissionsDefinitionAction");
LinkedList<PermissionsDefinitionAwsPolicy> policies = new LinkedList<PermissionsDefinitionAwsPolicy>();
PermissionsDefinitionAwsPolicy permissionsDefinitionAwsPolicy = new PermissionsDefinitionAwsPolicy();
permissionsDefinitionAwsPolicy.setId("arn:aws:iam::956987887735:policy/AddUserToGroup");
policies.add(permissionsDefinitionAwsPolicy);
actionInfo.setPolicies(policies);
actionInfo.setAssignToRoleId("arn:aws:aim::956987887735:role/saml-user");
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
SamlIdentitySource source = new SamlIdentitySource();
source.setOdataType("microsoft.graph.samlIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to add a user to a group");
scheduledPermissionsRequest.setNotes("Pretty Please");
RequestSchedule scheduleInfo = new RequestSchedule();
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': '#microsoft.graph.awsPermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: '956987887735',
      authorizationSystemType: 'AWS'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.awsPolicyPermissionsDefinitionAction',
      policies: [
        {
          id: 'arn:aws:iam::956987887735:policy/AddUserToGroup'
        }
      ],
      assignToRoleId: 'arn:aws:aim::956987887735:role/saml-user'
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.samlIdentitySource'
      },
      identityType: 'user'
    }
  },
  justification: 'I need to do this because I want to add a user to a group',
  notes: 'Pretty Please',
  scheduleInfo: {
    expiration: {
      duration: 'PT1H'
    }
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\AwsPermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\AwsPolicyPermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAwsPolicy;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\SamlIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new AwsPermissionsDefinition();
$requestedPermissions->setOdataType('#microsoft.graph.awsPermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('956987887735');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('AWS');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new AwsPolicyPermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.awsPolicyPermissionsDefinitionAction');
$policiesPermissionsDefinitionAwsPolicy1 = new PermissionsDefinitionAwsPolicy();
$policiesPermissionsDefinitionAwsPolicy1->setId('arn:aws:iam::956987887735:policy/AddUserToGroup');
$policiesArray []= $policiesPermissionsDefinitionAwsPolicy1;
$requestedPermissionsActionInfo->setPolicies($policiesArray);

$requestedPermissionsActionInfo->setAssignToRoleId('arn:aws:aim::956987887735:role/saml-user');
$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new SamlIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.samlIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to add a user to a group');
$requestBody->setNotes('Pretty Please');
$scheduleInfo = new RequestSchedule();
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "#microsoft.graph.awsPermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "956987887735"
			authorizationSystemType = "AWS"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.awsPolicyPermissionsDefinitionAction"
			policies = @(
				@{
					id = "arn:aws:iam::956987887735:policy/AddUserToGroup"
				}
			)
			assignToRoleId = "arn:aws:aim::956987887735:role/saml-user"
		}
		identityInfo = @{
			externalId = "alex@contoso.com"
			source = @{
				"@odata.type" = "microsoft.graph.samlIdentitySource"
			}
			identityType = "user"
		}
	}
	justification = "I need to do this because I want to add a user to a group"
	notes = "Pretty Please"
	scheduleInfo = @{
		expiration = @{
			duration = "PT1H"
		}
	}
	ticketInfo = @{
		ticketNumber = "INC1234567"
		ticketSystem = "ServiceNow"
		ticketSubmitterIdentityId = "alex@contoso.com"
		ticketApproverIdentityId = "alexmanager@contoso.com"
	}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.aws_permissions_definition import AwsPermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.aws_policy_permissions_definition_action import AwsPolicyPermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_aws_policy import PermissionsDefinitionAwsPolicy
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.saml_identity_source import SamlIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = AwsPermissionsDefinition(
		odata_type = "#microsoft.graph.awsPermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "956987887735",
			authorization_system_type = "AWS",
		),
		action_info = AwsPolicyPermissionsDefinitionAction(
			odata_type = "microsoft.graph.awsPolicyPermissionsDefinitionAction",
			policies = [
				PermissionsDefinitionAwsPolicy(
					id = "arn:aws:iam::956987887735:policy/AddUserToGroup",
				),
			],
			assign_to_role_id = "arn:aws:aim::956987887735:role/saml-user",
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = SamlIdentitySource(
				odata_type = "microsoft.graph.samlIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
	),
	justification = "I need to do this because I want to add a user to a group",
	notes = "Pretty Please",
	schedule_info = RequestSchedule(
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Request an AWS action

- [HTTP](#tabpanel_51_http)
- [C#](#tabpanel_51_csharp)
- [Go](#tabpanel_51_go)
- [Java](#tabpanel_51_java)
- [JavaScript](#tabpanel_51_javascript)
- [PHP](#tabpanel_51_php)
- [PowerShell](#tabpanel_51_powershell)
- [Python](#tabpanel_51_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.awsPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "956987887735",
      "authorizationSystemType": "AWS"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.awsActionsPermissionsDefinitionAction",
      "statements": [
        {
          "statementId": "test1",
          "actions": ["s3:AbortMultipartUpload", "s3:CreateBucket"],
          "notActions": [],
          "resources": ["*"],
          "notResources": [],
          "effect": "allow",
          "condition": {
            "NumericLessThanEquals": { "aws:MultiFactorAuthAge": "3600" }
          }
        },
        {
          "statementId": "test2",
          "actions": ["s3:Delete:*"],
          "notActions": [],
          "resources": ["*"],
          "notResources": [],
          "effect": "allow",
          "condition": {
            "NumericLessThanEquals": { "aws:MultiFactorAuthAge": "3600" }
          }
        }
      ],
      "assignToRoleId": "arn:aws:iam::956987887735:role/ck-saml-power-user"
    },
    "identityInfo": {
      "externalId": "rsn:alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.samlIdentitySource"
      },
      "identityType": "user"
    }
  },
  "justification": "I need to do this because I want to access S3 resources",
  "notes": "Please",
  "scheduleInfo": {
    "startDateTime": "2023-02-08T12:15:00Z",
    "expiration": {
      "duration": "PT1H"
    },
    "recurrence": {
      "pattern": {
        "dayOfMonth": 5,
        "daysOfWeek": [],
        "interval": 1,
        "reccurencePatternType": "absoluteMonthly"
      },
      "range": {
        "startDate": "2023-02-08",
        "reccurenceRangeType": "noEnd"
      }
    }
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new AwsPermissionsDefinition
	{
		OdataType = "microsoft.graph.awsPermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "956987887735",
			AuthorizationSystemType = "AWS",
		},
		ActionInfo = new AwsActionsPermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.awsActionsPermissionsDefinitionAction",
			Statements = new List<AwsStatement>
			{
				new AwsStatement
				{
					StatementId = "test1",
					Actions = new List<string>
					{
						"s3:AbortMultipartUpload",
						"s3:CreateBucket",
					},
					NotActions = new List<string>
					{
					},
					Resources = new List<string>
					{
						"*",
					},
					NotResources = new List<string>
					{
					},
					Effect = AwsStatementEffect.Allow,
					Condition = new AwsCondition
					{
						AdditionalData = new Dictionary<string, object>
						{
							{
								"NumericLessThanEquals" , new UntypedObject(new Dictionary<string, UntypedNode>
								{
									{
										"aws:MultiFactorAuthAge", new UntypedString("3600")
									},
								})
							},
						},
					},
				},
				new AwsStatement
				{
					StatementId = "test2",
					Actions = new List<string>
					{
						"s3:Delete:*",
					},
					NotActions = new List<string>
					{
					},
					Resources = new List<string>
					{
						"*",
					},
					NotResources = new List<string>
					{
					},
					Effect = AwsStatementEffect.Allow,
					Condition = new AwsCondition
					{
						AdditionalData = new Dictionary<string, object>
						{
							{
								"NumericLessThanEquals" , new UntypedObject(new Dictionary<string, UntypedNode>
								{
									{
										"aws:MultiFactorAuthAge", new UntypedString("3600")
									},
								})
							},
						},
					},
				},
			},
			AssignToRoleId = "arn:aws:iam::956987887735:role/ck-saml-power-user",
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "rsn:alex@contoso.com",
			Source = new SamlIdentitySource
			{
				OdataType = "microsoft.graph.samlIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
	},
	Justification = "I need to do this because I want to access S3 resources",
	Notes = "Please",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = DateTimeOffset.Parse("2023-02-08T12:15:00Z"),
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				DayOfMonth = 5,
				DaysOfWeek = new List<DayOfWeekObject>
				{
				},
				Interval = 1,
				AdditionalData = new Dictionary<string, object>
				{
					{
						"reccurencePatternType" , "absoluteMonthly"
					},
				},
			},
			Range = new RecurrenceRange
			{
				StartDate = new Date(DateTime.Parse("2023-02-08")),
				AdditionalData = new Dictionary<string, object>
				{
					{
						"reccurenceRangeType" , "noEnd"
					},
				},
			},
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewAwsPermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "956987887735"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "AWS"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewAwsActionsPermissionsDefinitionAction()


awsStatement := graphmodels.NewAwsStatement()
statementId := "test1"
awsStatement.SetStatementId(&statementId) 
actions := []string {
	"s3:AbortMultipartUpload",
	"s3:CreateBucket",
}
awsStatement.SetActions(actions)
notActions := []string {

}
awsStatement.SetNotActions(notActions)
resources := []string {
	"*",
}
awsStatement.SetResources(resources)
notResources := []string {

}
awsStatement.SetNotResources(notResources)
effect := graphmodels.ALLOW_AWSSTATEMENTEFFECT 
awsStatement.SetEffect(&effect) 
condition := graphmodels.NewAwsCondition()
additionalData := map[string]interface{}{
numericLessThanEquals := graph.New()
aws:MultiFactorAuthAge := "3600"
numericLessThanEquals.SetAws:MultiFactorAuthAge(&aws:MultiFactorAuthAge) 
	condition.SetNumericLessThanEquals(numericLessThanEquals)
}
condition.SetAdditionalData(additionalData)
awsStatement.SetCondition(condition)
awsStatement1 := graphmodels.NewAwsStatement()
statementId := "test2"
awsStatement1.SetStatementId(&statementId) 
actions := []string {
	"s3:Delete:*",
}
awsStatement1.SetActions(actions)
notActions := []string {

}
awsStatement1.SetNotActions(notActions)
resources := []string {
	"*",
}
awsStatement1.SetResources(resources)
notResources := []string {

}
awsStatement1.SetNotResources(notResources)
effect := graphmodels.ALLOW_AWSSTATEMENTEFFECT 
awsStatement1.SetEffect(&effect) 
condition := graphmodels.NewAwsCondition()
additionalData := map[string]interface{}{
numericLessThanEquals := graph.New()
aws:MultiFactorAuthAge := "3600"
numericLessThanEquals.SetAws:MultiFactorAuthAge(&aws:MultiFactorAuthAge) 
	condition.SetNumericLessThanEquals(numericLessThanEquals)
}
condition.SetAdditionalData(additionalData)
awsStatement1.SetCondition(condition)

statements := []graphmodels.AwsStatementable {
	awsStatement,
	awsStatement1,
}
actionInfo.SetStatements(statements)
assignToRoleId := "arn:aws:iam::956987887735:role/ck-saml-power-user"
actionInfo.SetAssignToRoleId(&assignToRoleId) 
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "rsn:alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewSamlIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to access S3 resources"
requestBody.SetJustification(&justification) 
notes := "Please"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime , err := time.Parse(time.RFC3339, "2023-02-08T12:15:00Z")
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
dayOfMonth := int32(5)
pattern.SetDayOfMonth(&dayOfMonth) 
daysOfWeek := []graphmodels.DayOfWeekable {

}
pattern.SetDaysOfWeek(daysOfWeek)
interval := int32(1)
pattern.SetInterval(&interval) 
additionalData := map[string]interface{}{
	"reccurencePatternType" : "absoluteMonthly", 
}
pattern.SetAdditionalData(additionalData)
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
startDate := 2023-02-08
range.SetStartDate(&startDate) 
additionalData := map[string]interface{}{
	"reccurenceRangeType" : "noEnd", 
}
range.SetAdditionalData(additionalData)
recurrence.SetRange(range)
scheduleInfo.SetRecurrence(recurrence)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
AwsPermissionsDefinition requestedPermissions = new AwsPermissionsDefinition();
requestedPermissions.setOdataType("microsoft.graph.awsPermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("956987887735");
authorizationSystemInfo.setAuthorizationSystemType("AWS");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
AwsActionsPermissionsDefinitionAction actionInfo = new AwsActionsPermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.awsActionsPermissionsDefinitionAction");
LinkedList<AwsStatement> statements = new LinkedList<AwsStatement>();
AwsStatement awsStatement = new AwsStatement();
awsStatement.setStatementId("test1");
LinkedList<String> actions = new LinkedList<String>();
actions.add("s3:AbortMultipartUpload");
actions.add("s3:CreateBucket");
awsStatement.setActions(actions);
LinkedList<String> notActions = new LinkedList<String>();
awsStatement.setNotActions(notActions);
LinkedList<String> resources = new LinkedList<String>();
resources.add("*");
awsStatement.setResources(resources);
LinkedList<String> notResources = new LinkedList<String>();
awsStatement.setNotResources(notResources);
awsStatement.setEffect(AwsStatementEffect.Allow);
AwsCondition condition = new AwsCondition();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 numericLessThanEquals = new ();
numericLessThanEquals.setAwsMultiFactorAuthAge("3600");
additionalData.put("NumericLessThanEquals", numericLessThanEquals);
condition.setAdditionalData(additionalData);
awsStatement.setCondition(condition);
statements.add(awsStatement);
AwsStatement awsStatement1 = new AwsStatement();
awsStatement1.setStatementId("test2");
LinkedList<String> actions1 = new LinkedList<String>();
actions1.add("s3:Delete:*");
awsStatement1.setActions(actions1);
LinkedList<String> notActions1 = new LinkedList<String>();
awsStatement1.setNotActions(notActions1);
LinkedList<String> resources1 = new LinkedList<String>();
resources1.add("*");
awsStatement1.setResources(resources1);
LinkedList<String> notResources1 = new LinkedList<String>();
awsStatement1.setNotResources(notResources1);
awsStatement1.setEffect(AwsStatementEffect.Allow);
AwsCondition condition1 = new AwsCondition();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
 numericLessThanEquals1 = new ();
numericLessThanEquals1.setAwsMultiFactorAuthAge("3600");
additionalData1.put("NumericLessThanEquals", numericLessThanEquals1);
condition1.setAdditionalData(additionalData1);
awsStatement1.setCondition(condition1);
statements.add(awsStatement1);
actionInfo.setStatements(statements);
actionInfo.setAssignToRoleId("arn:aws:iam::956987887735:role/ck-saml-power-user");
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("rsn:alex@contoso.com");
SamlIdentitySource source = new SamlIdentitySource();
source.setOdataType("microsoft.graph.samlIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to access S3 resources");
scheduledPermissionsRequest.setNotes("Please");
RequestSchedule scheduleInfo = new RequestSchedule();
OffsetDateTime startDateTime = OffsetDateTime.parse("2023-02-08T12:15:00Z");
scheduleInfo.setStartDateTime(startDateTime);
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setDayOfMonth(5);
LinkedList<DayOfWeek> daysOfWeek = new LinkedList<DayOfWeek>();
pattern.setDaysOfWeek(daysOfWeek);
pattern.setInterval(1);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("reccurencePatternType", "absoluteMonthly");
pattern.setAdditionalData(additionalData2);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
LocalDate startDate = LocalDate.parse("2023-02-08");
range.setStartDate(startDate);
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("reccurenceRangeType", "noEnd");
range.setAdditionalData(additionalData3);
recurrence.setRange(range);
scheduleInfo.setRecurrence(recurrence);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.awsPermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: '956987887735',
      authorizationSystemType: 'AWS'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.awsActionsPermissionsDefinitionAction',
      statements: [
        {
          statementId: 'test1',
          actions: ['s3:AbortMultipartUpload', 's3:CreateBucket'],
          notActions: [],
          resources: ['*'],
          notResources: [],
          effect: 'allow',
          condition: {
            NumericLessThanEquals: { 'aws:MultiFactorAuthAge': '3600' }
          }
        },
        {
          statementId: 'test2',
          actions: ['s3:Delete:*'],
          notActions: [],
          resources: ['*'],
          notResources: [],
          effect: 'allow',
          condition: {
            NumericLessThanEquals: { 'aws:MultiFactorAuthAge': '3600' }
          }
        }
      ],
      assignToRoleId: 'arn:aws:iam::956987887735:role/ck-saml-power-user'
    },
    identityInfo: {
      externalId: 'rsn:alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.samlIdentitySource'
      },
      identityType: 'user'
    }
  },
  justification: 'I need to do this because I want to access S3 resources',
  notes: 'Please',
  scheduleInfo: {
    startDateTime: '2023-02-08T12:15:00Z',
    expiration: {
      duration: 'PT1H'
    },
    recurrence: {
      pattern: {
        dayOfMonth: 5,
        daysOfWeek: [],
        interval: 1,
        reccurencePatternType: 'absoluteMonthly'
      },
      range: {
        startDate: '2023-02-08',
        reccurenceRangeType: 'noEnd'
      }
    }
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\AwsPermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\AwsActionsPermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\AwsStatement;
use Microsoft\Graph\Beta\Generated\Models\AwsStatementEffect;
use Microsoft\Graph\Beta\Generated\Models\AwsCondition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\SamlIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Beta\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Beta\Generated\Models\DayOfWeek;
use Microsoft\Graph\Beta\Generated\Models\RecurrenceRange;
use Microsoft\Kiota\Abstractions\Types\Date;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new AwsPermissionsDefinition();
$requestedPermissions->setOdataType('microsoft.graph.awsPermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('956987887735');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('AWS');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new AwsActionsPermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.awsActionsPermissionsDefinitionAction');
$statementsAwsStatement1 = new AwsStatement();
$statementsAwsStatement1->setStatementId('test1');
$statementsAwsStatement1->setActions(['s3:AbortMultipartUpload', 's3:CreateBucket', 	]);
$statementsAwsStatement1->setNotActions([	]);
$statementsAwsStatement1->setResources(['*', 	]);
$statementsAwsStatement1->setNotResources([	]);
$statementsAwsStatement1->setEffect(new AwsStatementEffect('allow'));
$statementsAwsStatement1Condition = new AwsCondition();
$additionalData = [
	'NumericLessThanEquals' => [
		'aws:MultiFactorAuthAge' => '3600',
	],
];
$statementsAwsStatement1Condition->setAdditionalData($additionalData);
$statementsAwsStatement1->setCondition($statementsAwsStatement1Condition);
$statementsArray []= $statementsAwsStatement1;
$statementsAwsStatement2 = new AwsStatement();
$statementsAwsStatement2->setStatementId('test2');
$statementsAwsStatement2->setActions(['s3:Delete:*', 	]);
$statementsAwsStatement2->setNotActions([	]);
$statementsAwsStatement2->setResources(['*', 	]);
$statementsAwsStatement2->setNotResources([	]);
$statementsAwsStatement2->setEffect(new AwsStatementEffect('allow'));
$statementsAwsStatement2Condition = new AwsCondition();
$additionalData = [
	'NumericLessThanEquals' => [
		'aws:MultiFactorAuthAge' => '3600',
	],
];
$statementsAwsStatement2Condition->setAdditionalData($additionalData);
$statementsAwsStatement2->setCondition($statementsAwsStatement2Condition);
$statementsArray []= $statementsAwsStatement2;
$requestedPermissionsActionInfo->setStatements($statementsArray);

$requestedPermissionsActionInfo->setAssignToRoleId('arn:aws:iam::956987887735:role/ck-saml-power-user');
$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('rsn:alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new SamlIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.samlIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to access S3 resources');
$requestBody->setNotes('Please');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(new \DateTime('2023-02-08T12:15:00Z'));
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$scheduleInfoRecurrence = new PatternedRecurrence();
$scheduleInfoRecurrencePattern = new RecurrencePattern();
$scheduleInfoRecurrencePattern->setDayOfMonth(5);
$scheduleInfoRecurrencePattern->setDaysOfWeek([]);
$scheduleInfoRecurrencePattern->setInterval(1);
$additionalData = [
'reccurencePatternType' => 'absoluteMonthly',
];
$scheduleInfoRecurrencePattern->setAdditionalData($additionalData);
$scheduleInfoRecurrence->setPattern($scheduleInfoRecurrencePattern);
$scheduleInfoRecurrenceRange = new RecurrenceRange();
$scheduleInfoRecurrenceRange->setStartDate(new Date('2023-02-08'));
$additionalData = [
'reccurenceRangeType' => 'noEnd',
];
$scheduleInfoRecurrenceRange->setAdditionalData($additionalData);
$scheduleInfoRecurrence->setRange($scheduleInfoRecurrenceRange);
$scheduleInfo->setRecurrence($scheduleInfoRecurrence);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "microsoft.graph.awsPermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "956987887735"
			authorizationSystemType = "AWS"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.awsActionsPermissionsDefinitionAction"
			statements = @(
				@{
					statementId = "test1"
					actions = @(
					"s3:AbortMultipartUpload"
				"s3:CreateBucket"
			)
			notActions = @(
			)
			resources = @(
			"*"
		)
		notResources = @(
		)
		effect = "allow"
		condition = @{
			NumericLessThanEquals = @{
				"aws:MultiFactorAuthAge" = "3600"
			}
		}
	}
	@{
		statementId = "test2"
		actions = @(
		"s3:Delete:*"
	)
	notActions = @(
	)
	resources = @(
	"*"
)
notResources = @(
)
effect = "allow"
condition = @{
	NumericLessThanEquals = @{
		"aws:MultiFactorAuthAge" = "3600"
	}
}
}
)
assignToRoleId = "arn:aws:iam::956987887735:role/ck-saml-power-user"
}
identityInfo = @{
externalId = "rsn:alex@contoso.com"
source = @{
"@odata.type" = "microsoft.graph.samlIdentitySource"
}
identityType = "user"
}
}
justification = "I need to do this because I want to access S3 resources"
notes = "Please"
scheduleInfo = @{
startDateTime = [System.DateTime]::Parse("2023-02-08T12:15:00Z")
expiration = @{
duration = "PT1H"
}
recurrence = @{
pattern = @{
dayOfMonth = 5
daysOfWeek = @(
)
interval = 1
reccurencePatternType = "absoluteMonthly"
}
range = @{
startDate = "2023-02-08"
reccurenceRangeType = "noEnd"
}
}
}
ticketInfo = @{
ticketNumber = "INC1234567"
ticketSystem = "ServiceNow"
ticketSubmitterIdentityId = "alex@contoso.com"
ticketApproverIdentityId = "alexmanager@contoso.com"
}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.aws_permissions_definition import AwsPermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.aws_actions_permissions_definition_action import AwsActionsPermissionsDefinitionAction
from msgraph_beta.generated.models.aws_statement import AwsStatement
from msgraph_beta.generated.models.aws_statement_effect import AwsStatementEffect
from msgraph_beta.generated.models.aws_condition import AwsCondition
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.saml_identity_source import SamlIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph_beta.generated.models.recurrence_pattern import RecurrencePattern
from msgraph_beta.generated.models.day_of_week import DayOfWeek
from msgraph_beta.generated.models.recurrence_range import RecurrenceRange
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = AwsPermissionsDefinition(
		odata_type = "microsoft.graph.awsPermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "956987887735",
			authorization_system_type = "AWS",
		),
		action_info = AwsActionsPermissionsDefinitionAction(
			odata_type = "microsoft.graph.awsActionsPermissionsDefinitionAction",
			statements = [
				AwsStatement(
					statement_id = "test1",
					actions = [
						"s3:AbortMultipartUpload",
						"s3:CreateBucket",
					],
					not_actions = [
					],
					resources = [
						"*",
					],
					not_resources = [
					],
					effect = AwsStatementEffect.Allow,
					condition = AwsCondition(
						additional_data = {
								"numeric_less_than_equals" : {
										"aws:_multi_factor_auth_age" : "3600",
								},
						}
					),
				),
				AwsStatement(
					statement_id = "test2",
					actions = [
						"s3:Delete:*",
					],
					not_actions = [
					],
					resources = [
						"*",
					],
					not_resources = [
					],
					effect = AwsStatementEffect.Allow,
					condition = AwsCondition(
						additional_data = {
								"numeric_less_than_equals" : {
										"aws:_multi_factor_auth_age" : "3600",
								},
						}
					),
				),
			],
			assign_to_role_id = "arn:aws:iam::956987887735:role/ck-saml-power-user",
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "rsn:alex@contoso.com",
			source = SamlIdentitySource(
				odata_type = "microsoft.graph.samlIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
	),
	justification = "I need to do this because I want to access S3 resources",
	notes = "Please",
	schedule_info = RequestSchedule(
		start_date_time = "2023-02-08T12:15:00Z",
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				day_of_month = 5,
				days_of_week = [
				],
				interval = 1,
				additional_data = {
						"reccurence_pattern_type" : "absoluteMonthly",
				}
			),
			range = RecurrenceRange(
				start_date = "2023-02-08",
				additional_data = {
						"reccurence_range_type" : "noEnd",
				}
			),
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## List GCP authorization systems

List GCP authorization systems onboarded to Permissions Management by filtering by the **authorizationSystemType** property.

- [HTTP](#tabpanel_52_http)
- [C#](#tabpanel_52_csharp)
- [Go](#tabpanel_52_go)
- [Java](#tabpanel_52_java)
- [JavaScript](#tabpanel_52_javascript)
- [PHP](#tabpanel_52_php)
- [PowerShell](#tabpanel_52_powershell)
- [Python](#tabpanel_52_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=authorizationSystemType eq 'gcp'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "authorizationSystemType eq 'gcp'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-beta-sdk-go/external"
	  //other-imports
)


requestFilter := "authorizationSystemType eq 'gcp'"

requestParameters := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystemCollectionResponse result = graphClient.external().authorizationSystems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "authorizationSystemType eq 'gcp'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystems = await client.api('/external/authorizationSystems')
	.version('beta')
	.filter('authorizationSystemType eq \'gcp\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\External\AuthorizationSystems\AuthorizationSystemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthorizationSystemsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthorizationSystemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "authorizationSystemType eq 'gcp'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->external()->authorizationSystems()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -Filter "authorizationSystemType eq 'gcp'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.external.authorization_systems.authorization_systems_request_builder import AuthorizationSystemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthorizationSystemsRequestBuilder.AuthorizationSystemsRequestBuilderGetQueryParameters(
		filter = "authorizationSystemType eq 'gcp'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.external.authorization_systems.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List GCP authorization systems onboarded to Permissions Management.

- [HTTP](#tabpanel_53_http)
- [C#](#tabpanel_53_csharp)
- [Go](#tabpanel_53_go)
- [Java](#tabpanel_53_java)
- [JavaScript](#tabpanel_53_javascript)
- [PHP](#tabpanel_53_php)
- [PowerShell](#tabpanel_53_powershell)
- [Python](#tabpanel_53_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/microsoft.graph.gcpAuthorizationSystem
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems["{authorizationSystem-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().ByAuthorizationSystemId("authorizationSystem-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystem result = graphClient.external().authorizationSystems().byAuthorizationSystemId("{authorizationSystem-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpAuthorizationSystem = await client.api('/external/authorizationSystems/microsoft.graph.gcpAuthorizationSystem')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->external()->authorizationSystems()->byAuthorizationSystemId('authorizationSystem-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -AuthorizationSystemId $authorizationSystemId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.external.authorization_systems.by_authorization_system_id('authorizationSystem-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Identify all GCP authorization systems that are online and have permissions modification capability enabled.

- [HTTP](#tabpanel_54_http)
- [C#](#tabpanel_54_csharp)
- [Go](#tabpanel_54_go)
- [Java](#tabpanel_54_java)
- [JavaScript](#tabpanel_54_javascript)
- [PHP](#tabpanel_54_php)
- [PowerShell](#tabpanel_54_powershell)
- [Python](#tabpanel_54_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems?$filter=authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.External.AuthorizationSystems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphexternal "github.com/microsoftgraph/msgraph-beta-sdk-go/external"
	  //other-imports
)


requestFilter := "authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'"

requestParameters := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphexternal.ExternalAuthorizationSystemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authorizationSystems, err := graphClient.External().AuthorizationSystems().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthorizationSystemCollectionResponse result = graphClient.external().authorizationSystems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystems = await client.api('/external/authorizationSystems')
	.version('beta')
	.filter('authorizationSystemType eq \'gcp\' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq \'enabled\' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq \'online\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\External\AuthorizationSystems\AuthorizationSystemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AuthorizationSystemsRequestBuilderGetRequestConfiguration();
$queryParameters = AuthorizationSystemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->external()->authorizationSystems()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

Get-MgBetaExternalAuthorizationSystem -Filter "authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.external.authorization_systems.authorization_systems_request_builder import AuthorizationSystemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AuthorizationSystemsRequestBuilder.AuthorizationSystemsRequestBuilderGetQueryParameters(
		filter = "authorizationSystemType eq 'gcp' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/permissionsModificationCapability eq 'enabled' and dataCollectionInfo/entitlements/microsoft.graph.entitlementsDataCollection/status eq 'online'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.external.authorization_systems.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get identities in a GCP authorization system

### List all identities

- [HTTP](#tabpanel_55_http)
- [C#](#tabpanel_55_csharp)
- [Go](#tabpanel_55_go)
- [Java](#tabpanel_55_java)
- [JavaScript](#tabpanel_55_javascript)
- [PHP](#tabpanel_55_php)
- [PowerShell](#tabpanel_55_powershell)
- [Python](#tabpanel_55_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/all
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let all = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/all')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one identity

By primary key ID.

- [HTTP](#tabpanel_56_http)
- [C#](#tabpanel_56_csharp)
- [Go](#tabpanel_56_go)
- [Java](#tabpanel_56_java)
- [JavaScript](#tabpanel_56_javascript)
- [PHP](#tabpanel_56_php)
- [PowerShell](#tabpanel_56_powershell)
- [Python](#tabpanel_56_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/all/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpIdentity = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/all/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/all(externalId='{externalId}')
```

## Get GCP users

### List all GCP users

- [HTTP](#tabpanel_57_http)
- [C#](#tabpanel_57_csharp)
- [Go](#tabpanel_57_go)
- [Java](#tabpanel_57_java)
- [JavaScript](#tabpanel_57_javascript)
- [PHP](#tabpanel_57_php)
- [PowerShell](#tabpanel_57_powershell)
- [Python](#tabpanel_57_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/users
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/users')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one GCP user

By primary key user ID.

```http
GET /external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/users/{id}
```

By alternate key externalId.

```http
GET /external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/users(externalId='{externalId}')
```

## Get GCP service accounts

### List all GCP service accounts

- [HTTP](#tabpanel_58_http)
- [C#](#tabpanel_58_csharp)
- [Go](#tabpanel_58_go)
- [Java](#tabpanel_58_java)
- [JavaScript](#tabpanel_58_javascript)
- [PHP](#tabpanel_58_php)
- [PowerShell](#tabpanel_58_powershell)
- [Python](#tabpanel_58_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/serviceAccounts
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let serviceAccounts = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/serviceAccounts')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get one GCP service account

By primary key user ID.

- [HTTP](#tabpanel_59_http)
- [C#](#tabpanel_59_csharp)
- [Go](#tabpanel_59_go)
- [Java](#tabpanel_59_java)
- [JavaScript](#tabpanel_59_javascript)
- [PHP](#tabpanel_59_php)
- [PowerShell](#tabpanel_59_powershell)
- [Python](#tabpanel_59_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/serviceAccounts/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpServiceAccount = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/serviceAccounts/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

- [HTTP](#tabpanel_60_http)
- [C#](#tabpanel_60_csharp)
- [Go](#tabpanel_60_go)
- [Java](#tabpanel_60_java)
- [JavaScript](#tabpanel_60_javascript)
- [PHP](#tabpanel_60_php)
- [PowerShell](#tabpanel_60_powershell)
- [Python](#tabpanel_60_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/serviceAccounts(externalId='{externalId}')
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpServiceAccount = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/associatedIdentities/serviceAccounts/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Get actions

### List all actions

List all actions.

- [HTTP](#tabpanel_61_http)
- [C#](#tabpanel_61_csharp)
- [Go](#tabpanel_61_go)
- [Java](#tabpanel_61_java)
- [JavaScript](#tabpanel_61_javascript)
- [PHP](#tabpanel_61_php)
- [PowerShell](#tabpanel_61_powershell)
- [Python](#tabpanel_61_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

List actions for a specific service in a GCP authorization system.

- [HTTP](#tabpanel_62_http)
- [C#](#tabpanel_62_csharp)
- [Go](#tabpanel_62_go)
- [Java](#tabpanel_62_java)
- [JavaScript](#tabpanel_62_javascript)
- [PHP](#tabpanel_62_php)
- [PowerShell](#tabpanel_62_powershell)
- [Python](#tabpanel_62_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions?$filter=service/id eq 'compute'
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let actions = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get an action

By primary key action ID.

- [HTTP](#tabpanel_63_http)
- [C#](#tabpanel_63_csharp)
- [Go](#tabpanel_63_go)
- [Java](#tabpanel_63_java)
- [JavaScript](#tabpanel_63_javascript)
- [PHP](#tabpanel_63_php)
- [PowerShell](#tabpanel_63_powershell)
- [Python](#tabpanel_63_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpAuthorizationSystemTypeAction = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/actions(externalId={externalId})
```

## Get resources

### List all resources

- [HTTP](#tabpanel_64_http)
- [C#](#tabpanel_64_csharp)
- [Go](#tabpanel_64_go)
- [Java](#tabpanel_64_java)
- [JavaScript](#tabpanel_64_javascript)
- [PHP](#tabpanel_64_php)
- [PowerShell](#tabpanel_64_powershell)
- [Python](#tabpanel_64_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/resources
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let resources = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/resources')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a resource

By primary key resource ID.

- [HTTP](#tabpanel_65_http)
- [C#](#tabpanel_65_csharp)
- [Go](#tabpanel_65_go)
- [Java](#tabpanel_65_java)
- [JavaScript](#tabpanel_65_javascript)
- [PHP](#tabpanel_65_php)
- [PowerShell](#tabpanel_65_powershell)
- [Python](#tabpanel_65_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/resources/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpAuthorizationSystemResource = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/resources/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/resources(externalId={externalId})
```

## Get roles

### List all roles

List all roles.

- [HTTP](#tabpanel_66_http)
- [C#](#tabpanel_66_csharp)
- [Go](#tabpanel_66_go)
- [Java](#tabpanel_66_java)
- [JavaScript](#tabpanel_66_javascript)
- [PHP](#tabpanel_66_php)
- [PowerShell](#tabpanel_66_powershell)
- [Python](#tabpanel_66_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/roles
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roles = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/roles')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a role definition

By primary key role ID assigned by Permissions Management.

- [HTTP](#tabpanel_67_http)
- [C#](#tabpanel_67_csharp)
- [Go](#tabpanel_67_go)
- [Java](#tabpanel_67_java)
- [JavaScript](#tabpanel_67_javascript)
- [PHP](#tabpanel_67_php)
- [PowerShell](#tabpanel_67_powershell)
- [Python](#tabpanel_67_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/roles/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let gcpRole = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/roles/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

By alternate key externalId.

```http
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/roles(externalId='{externalId}')
```

## Get services

### List all services

- [HTTP](#tabpanel_68_http)
- [C#](#tabpanel_68_csharp)
- [Go](#tabpanel_68_go)
- [Java](#tabpanel_68_java)
- [JavaScript](#tabpanel_68_javascript)
- [PHP](#tabpanel_68_php)
- [PowerShell](#tabpanel_68_powershell)
- [Python](#tabpanel_68_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/services
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let services = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/services')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Get a service

- [HTTP](#tabpanel_69_http)
- [C#](#tabpanel_69_csharp)
- [Go](#tabpanel_69_go)
- [Java](#tabpanel_69_java)
- [JavaScript](#tabpanel_69_javascript)
- [PHP](#tabpanel_69_php)
- [PowerShell](#tabpanel_69_powershell)
- [Python](#tabpanel_69_python)

```msgraph
GET https://graph.microsoft.com/beta/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/services/{id}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authorizationSystemTypeService = await client.api('/external/authorizationSystems/{id}/microsoft.graph.gcpAuthorizationSystem/services/{id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Request a GCP action

- [HTTP](#tabpanel_70_http)
- [C#](#tabpanel_70_csharp)
- [Go](#tabpanel_70_go)
- [Java](#tabpanel_70_java)
- [JavaScript](#tabpanel_70_javascript)
- [PHP](#tabpanel_70_php)
- [PowerShell](#tabpanel_70_powershell)
- [Python](#tabpanel_70_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceGcpPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "carbide-bonsai-205017",
      "authorizationSystemType": "GCP"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.gcpActionPermissionsDefinitionAction",
      "actions": [
        "aiplatform:dataitems"
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "carbide-bonsai-205017"
  },
  "justification": "I need to do this because I want to code my own chat GPT-3 bot on GCP",
  "notes": "Pretty Pleaseeeee",
  "scheduleInfo": {
    "expiration": {
      "duration": "PT1H"
    }
  },
  "ticketInfo": {
    "ticketNumber": "INC1234567",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new SingleResourceGcpPermissionsDefinition
	{
		OdataType = "microsoft.graph.singleResourceGcpPermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "carbide-bonsai-205017",
			AuthorizationSystemType = "GCP",
		},
		ActionInfo = new GcpActionPermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.gcpActionPermissionsDefinitionAction",
			Actions = new List<string>
			{
				"aiplatform:dataitems",
			},
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new EdIdentitySource
			{
				OdataType = "microsoft.graph.edIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
		ResourceId = "carbide-bonsai-205017",
	},
	Justification = "I need to do this because I want to code my own chat GPT-3 bot on GCP",
	Notes = "Pretty Pleaseeeee",
	ScheduleInfo = new RequestSchedule
	{
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "INC1234567",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewSingleResourceGcpPermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "carbide-bonsai-205017"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "GCP"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewGcpActionPermissionsDefinitionAction()
actions := []string {
	"aiplatform:dataitems",
}
actionInfo.SetActions(actions)
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewEdIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
resourceId := "carbide-bonsai-205017"
requestedPermissions.SetResourceId(&resourceId) 
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to code my own chat GPT-3 bot on GCP"
requestBody.SetJustification(&justification) 
notes := "Pretty Pleaseeeee"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "INC1234567"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
SingleResourceGcpPermissionsDefinition requestedPermissions = new SingleResourceGcpPermissionsDefinition();
requestedPermissions.setOdataType("microsoft.graph.singleResourceGcpPermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("carbide-bonsai-205017");
authorizationSystemInfo.setAuthorizationSystemType("GCP");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
GcpActionPermissionsDefinitionAction actionInfo = new GcpActionPermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.gcpActionPermissionsDefinitionAction");
LinkedList<String> actions = new LinkedList<String>();
actions.add("aiplatform:dataitems");
actionInfo.setActions(actions);
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
EdIdentitySource source = new EdIdentitySource();
source.setOdataType("microsoft.graph.edIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
requestedPermissions.setResourceId("carbide-bonsai-205017");
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to code my own chat GPT-3 bot on GCP");
scheduledPermissionsRequest.setNotes("Pretty Pleaseeeee");
RequestSchedule scheduleInfo = new RequestSchedule();
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("INC1234567");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.singleResourceGcpPermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: 'carbide-bonsai-205017',
      authorizationSystemType: 'GCP'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.gcpActionPermissionsDefinitionAction',
      actions: [
        'aiplatform:dataitems'
      ]
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.edIdentitySource'
      },
      identityType: 'user'
    },
    resourceId: 'carbide-bonsai-205017'
  },
  justification: 'I need to do this because I want to code my own chat GPT-3 bot on GCP',
  notes: 'Pretty Pleaseeeee',
  scheduleInfo: {
    expiration: {
      duration: 'PT1H'
    }
  },
  ticketInfo: {
    ticketNumber: 'INC1234567',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\SingleResourceGcpPermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\GcpActionPermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\EdIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new SingleResourceGcpPermissionsDefinition();
$requestedPermissions->setOdataType('microsoft.graph.singleResourceGcpPermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('carbide-bonsai-205017');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('GCP');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new GcpActionPermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.gcpActionPermissionsDefinitionAction');
$requestedPermissionsActionInfo->setActions(['aiplatform:dataitems', 	]);
$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new EdIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.edIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestedPermissions->setResourceId('carbide-bonsai-205017');
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to code my own chat GPT-3 bot on GCP');
$requestBody->setNotes('Pretty Pleaseeeee');
$scheduleInfo = new RequestSchedule();
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('INC1234567');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "microsoft.graph.singleResourceGcpPermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "carbide-bonsai-205017"
			authorizationSystemType = "GCP"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.gcpActionPermissionsDefinitionAction"
			actions = @(
			"aiplatform:dataitems"
		)
	}
	identityInfo = @{
		externalId = "alex@contoso.com"
		source = @{
			"@odata.type" = "microsoft.graph.edIdentitySource"
		}
		identityType = "user"
	}
	resourceId = "carbide-bonsai-205017"
}
justification = "I need to do this because I want to code my own chat GPT-3 bot on GCP"
notes = "Pretty Pleaseeeee"
scheduleInfo = @{
	expiration = @{
		duration = "PT1H"
	}
}
ticketInfo = @{
	ticketNumber = "INC1234567"
	ticketSystem = "ServiceNow"
	ticketSubmitterIdentityId = "alex@contoso.com"
	ticketApproverIdentityId = "alexmanager@contoso.com"
}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.single_resource_gcp_permissions_definition import SingleResourceGcpPermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.gcp_action_permissions_definition_action import GcpActionPermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.ed_identity_source import EdIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = SingleResourceGcpPermissionsDefinition(
		odata_type = "microsoft.graph.singleResourceGcpPermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "carbide-bonsai-205017",
			authorization_system_type = "GCP",
		),
		action_info = GcpActionPermissionsDefinitionAction(
			odata_type = "microsoft.graph.gcpActionPermissionsDefinitionAction",
			actions = [
				"aiplatform:dataitems",
			],
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = EdIdentitySource(
				odata_type = "microsoft.graph.edIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
		resource_id = "carbide-bonsai-205017",
	),
	justification = "I need to do this because I want to code my own chat GPT-3 bot on GCP",
	notes = "Pretty Pleaseeeee",
	schedule_info = RequestSchedule(
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
	),
	ticket_info = TicketInfo(
		ticket_number = "INC1234567",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Request a GCP role

- [HTTP](#tabpanel_71_http)
- [C#](#tabpanel_71_csharp)
- [Go](#tabpanel_71_go)
- [Java](#tabpanel_71_java)
- [JavaScript](#tabpanel_71_javascript)
- [PHP](#tabpanel_71_php)
- [PowerShell](#tabpanel_71_powershell)
- [Python](#tabpanel_71_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests
Content-Type: application/json

{
  "requestedPermissions": {
    "@odata.type": "microsoft.graph.singleResourceGcpPermissionsDefinition",
    "authorizationSystemInfo": {
      "authorizationSystemId": "carbide-bonsai-205017",
      "authorizationSystemType": "GCP"
    },
    "actionInfo": {
      "@odata.type": "microsoft.graph.gcpRolePermissionsDefinitionAction",
      "roles": [
        {
          "id": "roles/dialogflow.aamAdmin"
        }
      ]
    },
    "identityInfo": {
      "externalId": "alex@contoso.com",
      "source": {
        "@odata.type": "microsoft.graph.edIdentitySource"
      },
      "identityType": "user"
    },
    "resourceId": "carbide-bonsai-205017"
  },
  "justification": "I need to do this because I want to be an administrator",
  "notes": "Pretty Pleaseeeee",
  "scheduleInfo": {
    "startDateTime": null,
    "expiration": {
      "duration": "PT1H"
    },
    "recurrence": null
  },
  "ticketInfo": {
    "ticketNumber": "123456",
    "ticketSystem": "ServiceNow",
    "ticketSubmitterIdentityId": "alex@contoso.com",
    "ticketApproverIdentityId": "alexmanager@contoso.com"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ScheduledPermissionsRequest
{
	RequestedPermissions = new SingleResourceGcpPermissionsDefinition
	{
		OdataType = "microsoft.graph.singleResourceGcpPermissionsDefinition",
		AuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem
		{
			AuthorizationSystemId = "carbide-bonsai-205017",
			AuthorizationSystemType = "GCP",
		},
		ActionInfo = new GcpRolePermissionsDefinitionAction
		{
			OdataType = "microsoft.graph.gcpRolePermissionsDefinitionAction",
			Roles = new List<PermissionsDefinitionGcpRole>
			{
				new PermissionsDefinitionGcpRole
				{
					Id = "roles/dialogflow.aamAdmin",
				},
			},
		},
		IdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity
		{
			ExternalId = "alex@contoso.com",
			Source = new EdIdentitySource
			{
				OdataType = "microsoft.graph.edIdentitySource",
			},
			IdentityType = PermissionsDefinitionIdentityType.User,
		},
		ResourceId = "carbide-bonsai-205017",
	},
	Justification = "I need to do this because I want to be an administrator",
	Notes = "Pretty Pleaseeeee",
	ScheduleInfo = new RequestSchedule
	{
		StartDateTime = null,
		Expiration = new ExpirationPattern
		{
			Duration = TimeSpan.Parse("PT1H"),
		},
		Recurrence = null,
	},
	TicketInfo = new TicketInfo
	{
		TicketNumber = "123456",
		TicketSystem = "ServiceNow",
		TicketSubmitterIdentityId = "alex@contoso.com",
		TicketApproverIdentityId = "alexmanager@contoso.com",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.PermissionsManagement.ScheduledPermissionsRequests.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewScheduledPermissionsRequest()
requestedPermissions := graphmodels.NewSingleResourceGcpPermissionsDefinition()
authorizationSystemInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystem()
authorizationSystemId := "carbide-bonsai-205017"
authorizationSystemInfo.SetAuthorizationSystemId(&authorizationSystemId) 
authorizationSystemType := "GCP"
authorizationSystemInfo.SetAuthorizationSystemType(&authorizationSystemType) 
requestedPermissions.SetAuthorizationSystemInfo(authorizationSystemInfo)
actionInfo := graphmodels.NewGcpRolePermissionsDefinitionAction()


permissionsDefinitionGcpRole := graphmodels.NewPermissionsDefinitionGcpRole()
id := "roles/dialogflow.aamAdmin"
permissionsDefinitionGcpRole.SetId(&id) 

roles := []graphmodels.PermissionsDefinitionGcpRoleable {
	permissionsDefinitionGcpRole,
}
actionInfo.SetRoles(roles)
requestedPermissions.SetActionInfo(actionInfo)
identityInfo := graphmodels.NewPermissionsDefinitionAuthorizationSystemIdentity()
externalId := "alex@contoso.com"
identityInfo.SetExternalId(&externalId) 
source := graphmodels.NewEdIdentitySource()
identityInfo.SetSource(source)
identityType := graphmodels.USER_PERMISSIONSDEFINITIONIDENTITYTYPE 
identityInfo.SetIdentityType(&identityType) 
requestedPermissions.SetIdentityInfo(identityInfo)
resourceId := "carbide-bonsai-205017"
requestedPermissions.SetResourceId(&resourceId) 
requestBody.SetRequestedPermissions(requestedPermissions)
justification := "I need to do this because I want to be an administrator"
requestBody.SetJustification(&justification) 
notes := "Pretty Pleaseeeee"
requestBody.SetNotes(&notes) 
scheduleInfo := graphmodels.NewRequestSchedule()
startDateTime := null
scheduleInfo.SetStartDateTime(&startDateTime) 
expiration := graphmodels.NewExpirationPattern()
duration , err := abstractions.ParseISODuration("PT1H")
expiration.SetDuration(&duration) 
scheduleInfo.SetExpiration(expiration)
recurrence := null
scheduleInfo.SetRecurrence(&recurrence) 
requestBody.SetScheduleInfo(scheduleInfo)
ticketInfo := graphmodels.NewTicketInfo()
ticketNumber := "123456"
ticketInfo.SetTicketNumber(&ticketNumber) 
ticketSystem := "ServiceNow"
ticketInfo.SetTicketSystem(&ticketSystem) 
ticketSubmitterIdentityId := "alex@contoso.com"
ticketInfo.SetTicketSubmitterIdentityId(&ticketSubmitterIdentityId) 
ticketApproverIdentityId := "alexmanager@contoso.com"
ticketInfo.SetTicketApproverIdentityId(&ticketApproverIdentityId) 
requestBody.SetTicketInfo(ticketInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
scheduledPermissionsRequests, err := graphClient.IdentityGovernance().PermissionsManagement().ScheduledPermissionsRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScheduledPermissionsRequest scheduledPermissionsRequest = new ScheduledPermissionsRequest();
SingleResourceGcpPermissionsDefinition requestedPermissions = new SingleResourceGcpPermissionsDefinition();
requestedPermissions.setOdataType("microsoft.graph.singleResourceGcpPermissionsDefinition");
PermissionsDefinitionAuthorizationSystem authorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
authorizationSystemInfo.setAuthorizationSystemId("carbide-bonsai-205017");
authorizationSystemInfo.setAuthorizationSystemType("GCP");
requestedPermissions.setAuthorizationSystemInfo(authorizationSystemInfo);
GcpRolePermissionsDefinitionAction actionInfo = new GcpRolePermissionsDefinitionAction();
actionInfo.setOdataType("microsoft.graph.gcpRolePermissionsDefinitionAction");
LinkedList<PermissionsDefinitionGcpRole> roles = new LinkedList<PermissionsDefinitionGcpRole>();
PermissionsDefinitionGcpRole permissionsDefinitionGcpRole = new PermissionsDefinitionGcpRole();
permissionsDefinitionGcpRole.setId("roles/dialogflow.aamAdmin");
roles.add(permissionsDefinitionGcpRole);
actionInfo.setRoles(roles);
requestedPermissions.setActionInfo(actionInfo);
PermissionsDefinitionAuthorizationSystemIdentity identityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
identityInfo.setExternalId("alex@contoso.com");
EdIdentitySource source = new EdIdentitySource();
source.setOdataType("microsoft.graph.edIdentitySource");
identityInfo.setSource(source);
identityInfo.setIdentityType(PermissionsDefinitionIdentityType.User);
requestedPermissions.setIdentityInfo(identityInfo);
requestedPermissions.setResourceId("carbide-bonsai-205017");
scheduledPermissionsRequest.setRequestedPermissions(requestedPermissions);
scheduledPermissionsRequest.setJustification("I need to do this because I want to be an administrator");
scheduledPermissionsRequest.setNotes("Pretty Pleaseeeee");
RequestSchedule scheduleInfo = new RequestSchedule();
scheduleInfo.setStartDateTime(null);
ExpirationPattern expiration = new ExpirationPattern();
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
expiration.setDuration(duration);
scheduleInfo.setExpiration(expiration);
scheduleInfo.setRecurrence(null);
scheduledPermissionsRequest.setScheduleInfo(scheduleInfo);
TicketInfo ticketInfo = new TicketInfo();
ticketInfo.setTicketNumber("123456");
ticketInfo.setTicketSystem("ServiceNow");
ticketInfo.setTicketSubmitterIdentityId("alex@contoso.com");
ticketInfo.setTicketApproverIdentityId("alexmanager@contoso.com");
scheduledPermissionsRequest.setTicketInfo(ticketInfo);
ScheduledPermissionsRequest result = graphClient.identityGovernance().permissionsManagement().scheduledPermissionsRequests().post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduledPermissionsRequest = {
  requestedPermissions: {
    '@odata.type': 'microsoft.graph.singleResourceGcpPermissionsDefinition',
    authorizationSystemInfo: {
      authorizationSystemId: 'carbide-bonsai-205017',
      authorizationSystemType: 'GCP'
    },
    actionInfo: {
      '@odata.type': 'microsoft.graph.gcpRolePermissionsDefinitionAction',
      roles: [
        {
          id: 'roles/dialogflow.aamAdmin'
        }
      ]
    },
    identityInfo: {
      externalId: 'alex@contoso.com',
      source: {
        '@odata.type': 'microsoft.graph.edIdentitySource'
      },
      identityType: 'user'
    },
    resourceId: 'carbide-bonsai-205017'
  },
  justification: 'I need to do this because I want to be an administrator',
  notes: 'Pretty Pleaseeeee',
  scheduleInfo: {
    startDateTime: null,
    expiration: {
      duration: 'PT1H'
    },
    recurrence: null
  },
  ticketInfo: {
    ticketNumber: '123456',
    ticketSystem: 'ServiceNow',
    ticketSubmitterIdentityId: 'alex@contoso.com',
    ticketApproverIdentityId: 'alexmanager@contoso.com'
  }
};

await client.api('/identityGovernance/permissionsManagement/scheduledPermissionsRequests')
	.version('beta')
	.post(scheduledPermissionsRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ScheduledPermissionsRequest;
use Microsoft\Graph\Beta\Generated\Models\SingleResourceGcpPermissionsDefinition;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystem;
use Microsoft\Graph\Beta\Generated\Models\GcpRolePermissionsDefinitionAction;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionGcpRole;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionAuthorizationSystemIdentity;
use Microsoft\Graph\Beta\Generated\Models\EdIdentitySource;
use Microsoft\Graph\Beta\Generated\Models\PermissionsDefinitionIdentityType;
use Microsoft\Graph\Beta\Generated\Models\RequestSchedule;
use Microsoft\Graph\Beta\Generated\Models\ExpirationPattern;
use Microsoft\Graph\Beta\Generated\Models\TicketInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ScheduledPermissionsRequest();
$requestedPermissions = new SingleResourceGcpPermissionsDefinition();
$requestedPermissions->setOdataType('microsoft.graph.singleResourceGcpPermissionsDefinition');
$requestedPermissionsAuthorizationSystemInfo = new PermissionsDefinitionAuthorizationSystem();
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemId('carbide-bonsai-205017');
$requestedPermissionsAuthorizationSystemInfo->setAuthorizationSystemType('GCP');
$requestedPermissions->setAuthorizationSystemInfo($requestedPermissionsAuthorizationSystemInfo);
$requestedPermissionsActionInfo = new GcpRolePermissionsDefinitionAction();
$requestedPermissionsActionInfo->setOdataType('microsoft.graph.gcpRolePermissionsDefinitionAction');
$rolesPermissionsDefinitionGcpRole1 = new PermissionsDefinitionGcpRole();
$rolesPermissionsDefinitionGcpRole1->setId('roles/dialogflow.aamAdmin');
$rolesArray []= $rolesPermissionsDefinitionGcpRole1;
$requestedPermissionsActionInfo->setRoles($rolesArray);

$requestedPermissions->setActionInfo($requestedPermissionsActionInfo);
$requestedPermissionsIdentityInfo = new PermissionsDefinitionAuthorizationSystemIdentity();
$requestedPermissionsIdentityInfo->setExternalId('alex@contoso.com');
$requestedPermissionsIdentityInfoSource = new EdIdentitySource();
$requestedPermissionsIdentityInfoSource->setOdataType('microsoft.graph.edIdentitySource');
$requestedPermissionsIdentityInfo->setSource($requestedPermissionsIdentityInfoSource);
$requestedPermissionsIdentityInfo->setIdentityType(new PermissionsDefinitionIdentityType('user'));
$requestedPermissions->setIdentityInfo($requestedPermissionsIdentityInfo);
$requestedPermissions->setResourceId('carbide-bonsai-205017');
$requestBody->setRequestedPermissions($requestedPermissions);
$requestBody->setJustification('I need to do this because I want to be an administrator');
$requestBody->setNotes('Pretty Pleaseeeee');
$scheduleInfo = new RequestSchedule();
$scheduleInfo->setStartDateTime(null);
$scheduleInfoExpiration = new ExpirationPattern();
$scheduleInfoExpiration->setDuration(new \DateInterval('PT1H'));
$scheduleInfo->setExpiration($scheduleInfoExpiration);
$scheduleInfo->setRecurrence(null);
$requestBody->setScheduleInfo($scheduleInfo);
$ticketInfo = new TicketInfo();
$ticketInfo->setTicketNumber('123456');
$ticketInfo->setTicketSystem('ServiceNow');
$ticketInfo->setTicketSubmitterIdentityId('alex@contoso.com');
$ticketInfo->setTicketApproverIdentityId('alexmanager@contoso.com');
$requestBody->setTicketInfo($ticketInfo);

$result = $graphServiceClient->identityGovernance()->permissionsManagement()->scheduledPermissionsRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestedPermissions = @{
		"@odata.type" = "microsoft.graph.singleResourceGcpPermissionsDefinition"
		authorizationSystemInfo = @{
			authorizationSystemId = "carbide-bonsai-205017"
			authorizationSystemType = "GCP"
		}
		actionInfo = @{
			"@odata.type" = "microsoft.graph.gcpRolePermissionsDefinitionAction"
			roles = @(
				@{
					id = "roles/dialogflow.aamAdmin"
				}
			)
		}
		identityInfo = @{
			externalId = "alex@contoso.com"
			source = @{
				"@odata.type" = "microsoft.graph.edIdentitySource"
			}
			identityType = "user"
		}
		resourceId = "carbide-bonsai-205017"
	}
	justification = "I need to do this because I want to be an administrator"
	notes = "Pretty Pleaseeeee"
	scheduleInfo = @{
		startDateTime = $null
		expiration = @{
			duration = "PT1H"
		}
		recurrence = $null
	}
	ticketInfo = @{
		ticketNumber = "123456"
		ticketSystem = "ServiceNow"
		ticketSubmitterIdentityId = "alex@contoso.com"
		ticketApproverIdentityId = "alexmanager@contoso.com"
	}
}

New-MgBetaIdentityGovernancePermissionManagementScheduledPermissionRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.scheduled_permissions_request import ScheduledPermissionsRequest
from msgraph_beta.generated.models.single_resource_gcp_permissions_definition import SingleResourceGcpPermissionsDefinition
from msgraph_beta.generated.models.permissions_definition_authorization_system import PermissionsDefinitionAuthorizationSystem
from msgraph_beta.generated.models.gcp_role_permissions_definition_action import GcpRolePermissionsDefinitionAction
from msgraph_beta.generated.models.permissions_definition_gcp_role import PermissionsDefinitionGcpRole
from msgraph_beta.generated.models.permissions_definition_authorization_system_identity import PermissionsDefinitionAuthorizationSystemIdentity
from msgraph_beta.generated.models.ed_identity_source import EdIdentitySource
from msgraph_beta.generated.models.permissions_definition_identity_type import PermissionsDefinitionIdentityType
from msgraph_beta.generated.models.request_schedule import RequestSchedule
from msgraph_beta.generated.models.expiration_pattern import ExpirationPattern
from msgraph_beta.generated.models.ticket_info import TicketInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ScheduledPermissionsRequest(
	requested_permissions = SingleResourceGcpPermissionsDefinition(
		odata_type = "microsoft.graph.singleResourceGcpPermissionsDefinition",
		authorization_system_info = PermissionsDefinitionAuthorizationSystem(
			authorization_system_id = "carbide-bonsai-205017",
			authorization_system_type = "GCP",
		),
		action_info = GcpRolePermissionsDefinitionAction(
			odata_type = "microsoft.graph.gcpRolePermissionsDefinitionAction",
			roles = [
				PermissionsDefinitionGcpRole(
					id = "roles/dialogflow.aamAdmin",
				),
			],
		),
		identity_info = PermissionsDefinitionAuthorizationSystemIdentity(
			external_id = "alex@contoso.com",
			source = EdIdentitySource(
				odata_type = "microsoft.graph.edIdentitySource",
			),
			identity_type = PermissionsDefinitionIdentityType.User,
		),
		resource_id = "carbide-bonsai-205017",
	),
	justification = "I need to do this because I want to be an administrator",
	notes = "Pretty Pleaseeeee",
	schedule_info = RequestSchedule(
		start_date_time = None,
		expiration = ExpirationPattern(
			duration = "PT1H",
		),
		recurrence = None,
	),
	ticket_info = TicketInfo(
		ticket_number = "123456",
		ticket_system = "ServiceNow",
		ticket_submitter_identity_id = "alex@contoso.com",
		ticket_approver_identity_id = "alexmanager@contoso.com",
	),
)

result = await graph_client.identity_governance.permissions_management.scheduled_permissions_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

---

## Cancel a permissions request by ID

Either the requestor or an administrator can cancel an approved request, while only the requestor can cancel a pending \(**statusDetail** of `submitted`\) request.

```http
POST https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/scheduledPermissionsRequests/{id}/cancelAll
```

## List details of all permissions requests

```http
GET https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/permissionsRequestChanges
```

## List details of all permissions requests filtered by the date they were modified

```http
GET https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/permissionsRequestChanges?$filter=modificationDateTime gt {t}
```

## Get details of a permissions request

```http
GET https://graph.microsoft.com/beta/identityGovernance/permissionsManagement/permissionsRequestChanges/{id}
```

## Related content

- [Discover, remediate, and monitor permissions in multicloud infrastructures using permissions management APIs \(preview\)](https://learn.microsoft.com/en-us/graph/api/resources/permissions-management-api-overview?view=graph-rest-beta&preserve-view=true)
