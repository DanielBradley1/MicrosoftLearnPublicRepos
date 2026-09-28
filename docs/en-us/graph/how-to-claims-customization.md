<!-- Source: https://learn.microsoft.com/en-us/graph/how-to-claims-customization -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Customize claims with the claims mapping policy in Microsoft Graph

You can add extra user attributes to access tokens to help your app make better authorization decisions. This article shows how to use Microsoft Graph APIs to create and assign a claims mapping policy, add custom claims to access tokens, and verify the custom claim in the token.

## Prerequisites

To complete this tutorial, you need:

- Access to an API client such as [Graph Explorer](https://aka.ms/ge), signed in with a Microsoft Entra account that has the Application Administrator role and grant the following delegated permissions: *Policy.Read.All*, *Policy.ReadWrite.ApplicationConfiguration*, and *Application.ReadWrite.All*.
- A client service principal to assign the claims mapping policy to.
- A resource service principal that exposes APIs.

## Create a claims mapping policy

This policy adds the `department` claim from the user object to the token.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/policies/claimsMappingPolicies
Content-type: application/json

{
 "definition": [
   "{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}"
 ],
 "displayName": "ExtraClaimsTest"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new ClaimsMappingPolicy
{
	Definition = new List<string>
	{
		"{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}",
	},
	DisplayName = "ExtraClaimsTest",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.ClaimsMappingPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewClaimsMappingPolicy()
definition := []string {
	"{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}",
}
requestBody.SetDefinition(definition)
displayName := "ExtraClaimsTest"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
claimsMappingPolicies, err := graphClient.Policies().ClaimsMappingPolicies().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ClaimsMappingPolicy claimsMappingPolicy = new ClaimsMappingPolicy();
LinkedList<String> definition = new LinkedList<String>();
definition.add("{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}");
claimsMappingPolicy.setDefinition(definition);
claimsMappingPolicy.setDisplayName("ExtraClaimsTest");
ClaimsMappingPolicy result = graphClient.policies().claimsMappingPolicies().post(claimsMappingPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const claimsMappingPolicy = {
 definition: [
   '{\"ClaimsMappingPolicy\':{\'Version\':1,\'IncludeBasicClaimSet\':\'true\",\"ClaimsSchema\':[{\'Source\':\'user\",\"ID\':\'department\",\"JwtClaimType\':\"department\"}]}}"
 ],
 displayName: 'ExtraClaimsTest'
};

await client.api('/policies/claimsMappingPolicies')
	.version('beta')
	.post(claimsMappingPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\ClaimsMappingPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ClaimsMappingPolicy();
$requestBody->setDefinition(['{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}', 	]);
$requestBody->setDisplayName('ExtraClaimsTest');

$result = $graphServiceClient->policies()->claimsMappingPolicies()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	definition = @(
	'{"ClaimsMappingPolicy":{"Version":1,"IncludeBasicClaimSet":"true","ClaimsSchema":[{"Source":"user","ID":"department","JwtClaimType":"department"}]}}'
)
displayName = "ExtraClaimsTest"
}

New-MgBetaPolicyClaimMappingPolicy -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.claims_mapping_policy import ClaimsMappingPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ClaimsMappingPolicy(
	definition = [
		"{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}",
	],
	display_name = "ExtraClaimsTest",
)

result = await graph_client.policies.claims_mapping_policies.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

Record the ID from the response to use later in this article.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/claimsMappingPolicies/$entity",
  "id": "06d5d20d-2955-45f8-a15d-cf2f434b8116",
  "deletedDateTime": null,
  "definition": [
      "{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"}]}}"
  ],
  "displayName": "ExtraClaimsTest",
  "isOrganizationDefault": false
}
```

You can also add more than one attribute to the policy. The following sample adds both the `department` and `companyname` claims to the token.

```json
{
  "definition": [
        "{\"ClaimsMappingPolicy\":{\"Version\":1,\"IncludeBasicClaimSet\":\"true\",\"ClaimsSchema\":[{\"Source\":\"user\",\"ID\":\"department\",\"JwtClaimType\":\"department\"},{\"Source\":\"user\",\"ID\":\"companyname\",\"JwtClaimType\":\"companyname\"}]}}"
    ],
 "displayName": "ExtraClaimsTest"
}
```

## Assign the policy to a resource service principal

The following request assigns the claims mapping policy to a service principal. A successful response returns `204 No Content`.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/servicePrincipals/3bdbbc1a-5e94-4c2b-895f-231d8af4beee/claimsMappingPolicies/$ref
Content-type: application/json

{
 "@odata.id": "https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ReferenceCreate
{
	OdataId = "https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.ServicePrincipals["{servicePrincipal-id}"].ClaimsMappingPolicies.Ref.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewReferenceCreate()
odataId := "https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116"
requestBody.SetOdataId(&odataId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").ClaimsMappingPolicies().Ref().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.ReferenceCreate referenceCreate = new com.microsoft.graph.models.ReferenceCreate();
referenceCreate.setOdataId("https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116");
graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").claimsMappingPolicies().ref().post(referenceCreate);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const claimsMappingPolicy = {
 '@odata.id': 'https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116'
};

await client.api('/servicePrincipals/3bdbbc1a-5e94-4c2b-895f-231d8af4beee/claimsMappingPolicies/$ref')
	.post(claimsMappingPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ReferenceCreate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReferenceCreate();
$requestBody->setOdataId('https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116');

$graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->claimsMappingPolicies()->ref()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	"@odata.id" = "https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116"
}

New-MgServicePrincipalClaimMappingPolicyByRef -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.reference_create import ReferenceCreate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReferenceCreate(
	odata_id = "https://graph.microsoft.com/v1.0/policies/claimsMappingPolicies/06d5d20d-2955-45f8-a15d-cf2f434b8116",
)

await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').claims_mapping_policies.ref.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Enable mapped claims in the resource application object

Update the application object to accept mapped claims and use access token version 2. A successful response returns `204 No Content`.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/applications/3dfbe85f-2d14-4660-b1a2-cb9c633ceebb
Content-type: application/json

{
  "api": {
    "acceptMappedClaims": true,
    "requestedAccessTokenVersion": 2
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Application
{
	Api = new ApiApplication
	{
		AcceptMappedClaims = true,
		RequestedAccessTokenVersion = 2,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Applications["{application-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewApplication()
api := graphmodels.NewApiApplication()
acceptMappedClaims := true
api.SetAcceptMappedClaims(&acceptMappedClaims) 
requestedAccessTokenVersion := int32(2)
api.SetRequestedAccessTokenVersion(&requestedAccessTokenVersion) 
requestBody.SetApi(api)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applications, err := graphClient.Applications().ByApplicationId("application-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Application application = new Application();
ApiApplication api = new ApiApplication();
api.setAcceptMappedClaims(true);
api.setRequestedAccessTokenVersion(2);
application.setApi(api);
Application result = graphClient.applications().byApplicationId("{application-id}").patch(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const application = {
  api: {
    acceptMappedClaims: true,
    requestedAccessTokenVersion: 2
  }
};

await client.api('/applications/3dfbe85f-2d14-4660-b1a2-cb9c633ceebb')
	.update(application);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Application;
use Microsoft\Graph\Generated\Models\ApiApplication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Application();
$api = new ApiApplication();
$api->setAcceptMappedClaims(true);
$api->setRequestedAccessTokenVersion(2);
$requestBody->setApi($api);

$result = $graphServiceClient->applications()->byApplicationId('application-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	api = @{
		acceptMappedClaims = $true
		requestedAccessTokenVersion = 2
	}
}

Update-MgApplication -ApplicationId $applicationId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.application import Application
from msgraph.generated.models.api_application import ApiApplication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Application(
	api = ApiApplication(
		accept_mapped_claims = True,
		requested_access_token_version = 2,
	),
)

result = await graph_client.applications.by_application_id('application-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Test the access token

In an API client that allows you to follow the [Microsoft identity platform and OAuth 2.0 authorization code flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow), obtain an access token. In the **scope** parameter, include one of the scopes exposed by your resource service principal, such as `openid profile email scope-defined-by-your-api` where `scope-defined-by-your-api` might be `api://00001111-aaaa-2222-bbbb-3333cccc4444/test`.

Use [jwt.ms](https://jwt.ms) to decode the access token. The `department` claim should appear in the token.

## Clean up resources

To unassign the claims mapping policy from the service principal, use the following request. A successful response returns `204 No Content`.

```http
DELETE https://graph.microsoft.com/v1.0/servicePrincipals/3bdbbc1a-5e94-4c2b-895f-231d8af4beee/claimsMappingPolicies//06d5d20d-2955-45f8-a15d-cf2f434b8116/$ref
```

## Related content

- [Claims customization using PowerShell and Claims Mapping Policy](https://learn.microsoft.com/en-us/entra/identity-platform/claims-customization-powershell)
- [claimsMappingPolicy resource type](https://learn.microsoft.com/en-us/graph/api/resources/claimsMappingPolicy)
