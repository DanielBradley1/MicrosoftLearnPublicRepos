<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-templates?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List conditionalAccessTemplates

Namespace: microsoft.graph

Get a list of the [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.Read.All | Not available. |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator - read standard properties
- Security Reader - read standard properties
- Security Administrator - read standard properties
- Global Reader
- Conditional Access Administrator

## HTTP request

```http
GET /identity/conditionalAccess/templates
```

## Optional query parameters

This method supports the `$filter` and `$select` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: List all conditional access policy templates

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/identity/conditionalAccess/templates
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Templates.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
templates, err := graphClient.Identity().ConditionalAccess().Templates().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessTemplateCollectionResponse result = graphClient.identity().conditionalAccess().templates().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let templates = await client.api('/identity/conditionalAccess/templates')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identity()->conditionalAccess()->templates()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityConditionalAccessTemplate
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity.conditional_access.templates.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/conditionalAccess/templates",
    "value": [
        {
            "name": "Require multifactor authentication for admins",
            "description": "Require multifactor authentication for privileged administrative accounts to reduce risk of compromise. This policy will target the same roles as Security Default.",
            "id": "c7503427-338e-4c5e-902d-abe252abfb43",
            "scenarios": "secureFoundation,zeroTrust,protectAdmins",
            "details": {
                "sessionControls": null,
                "conditions": {
                    "userRiskLevels": [],
                    "signInRiskLevels": [],
                    "clientAppTypes": [
                        "all"
                    ],
                    "servicePrincipalRiskLevels": [],
                    "platforms": null,
                    "locations": null,
                    "signInRiskDetections": null,
                    "times": null,
                    "deviceStates": null,
                    "devices": null,
                    "clientApplications": null,
                    "applications": {
                        "includeApplications": [
                            "All"
                        ],
                        "excludeApplications": [],
                        "includeUserActions": [],
                        "includeAuthenticationContextClassReferences": [],
                        "applicationFilter": null,
                        "networkAccess": null
                    },
                    "users": {
                        "includeUsers": [],
                        "excludeUsers": [
                            "Current administrator will be excluded"
                        ],
                        "includeGroups": [],
                        "excludeGroups": [],
                        "includeRoles": [
                            "62e90394-69f5-4237-9190-012177145e10",
                            "194ae4cb-b126-40b2-bd5b-6091b380977d"
                        ],
                        "excludeRoles": [],
                        "includeGuestsOrExternalUsers": null,
                        "excludeGuestsOrExternalUsers": null
                    }
                },
                "grantControls": {
                    "operator": "OR",
                    "builtInControls": [
                        "mfa"
                    ],
                    "customAuthenticationFactors": [],
                    "termsOfUse": [],
                    "authenticationStrength": null
                }
            }
        }
    ]
}
```

### Example 2: List name, description, id, scenarios of templates whose scenarios contain "secureFoundation"

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/identity/conditionalAccess/templates?$select=name,description,id,scenarios&$filter=scenarios has 'secureFoundation'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Templates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "name","description","id","scenarios" };
	requestConfiguration.QueryParameters.Filter = "scenarios has 'secureFoundation'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  //other-imports
)


requestFilter := "scenarios has 'secureFoundation'"

requestParameters := &graphidentity.ConditionalAccessTemplatesRequestBuilderGetQueryParameters{
	Select: [] string {"name","description","id","scenarios"},
	Filter: &requestFilter,
}
configuration := &graphidentity.ConditionalAccessTemplatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
templates, err := graphClient.Identity().ConditionalAccess().Templates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessTemplateCollectionResponse result = graphClient.identity().conditionalAccess().templates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"name", "description", "id", "scenarios"};
	requestConfiguration.queryParameters.filter = "scenarios has 'secureFoundation'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let templates = await client.api('/identity/conditionalAccess/templates')
	.filter('scenarios has \'secureFoundation\'')
	.select('name,description,id,scenarios')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\ConditionalAccess\Templates\TemplatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TemplatesRequestBuilderGetRequestConfiguration();
$queryParameters = TemplatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["name","description","id","scenarios"];
$queryParameters->filter = "scenarios has 'secureFoundation'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identity()->conditionalAccess()->templates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityConditionalAccessTemplate -Property "name,description,id,scenarios" -Filter "scenarios has 'secureFoundation'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.conditional_access.templates.templates_request_builder import TemplatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TemplatesRequestBuilder.TemplatesRequestBuilderGetQueryParameters(
		select = ["name","description","id","scenarios"],
		filter = "scenarios has 'secureFoundation'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity.conditional_access.templates.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/conditionalAccess/templates(name,description,id,scenarios)",
    "value": [
        {
            "name": "Require multifactor authentication for admins",
            "description": "Require multifactor authentication for privileged administrative accounts to reduce risk of compromise. This policy will target the same roles as Security Default.",
            "id": "c7503427-338e-4c5e-902d-abe252abfb43",
            "scenarios": "secureFoundation,zeroTrust,protectAdmins"
        },
        {
            "name": "Securing security info registration",
            "description": "Secure when and how users register for Azure AD multifactor authentication and self-service password.",
            "id": "b8bda7f8-6584-4446-bce9-d871480e53fa",
            "scenarios": "secureFoundation,zeroTrust,remoteWork"
        },
        {
            "name": "Block legacy authentication",
            "description": "Block legacy authentication endpoints that can be used to bypass multifactor authentication.",
            "id": "0b2282f9-2862-4178-88b5-d79340b36cb8",
            "scenarios": "secureFoundation,zeroTrust,remoteWork,protectAdmins"
        },
        {
            "name": "Require multifactor authentication for all users",
            "description": "Require multifactor authentication for all user accounts to reduce risk of compromise.",
            "id": "a3d0a415-b068-4326-9251-f9cdf9feeb64",
            "scenarios": "secureFoundation,zeroTrust,remoteWork"
        }
    ]
}
```
