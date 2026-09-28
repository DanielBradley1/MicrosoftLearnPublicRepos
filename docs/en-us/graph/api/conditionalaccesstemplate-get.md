<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccesstemplate-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get conditionalAccessTemplate

Namespace: microsoft.graph

Read the properties and relationships of a [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) object.

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
GET /identity/conditionalAccess/templates/{id}
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get the properties a template by ID

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
GET https://graph.microsoft.com/v1.0/identity/conditionalAccess/templates/c7503427-338e-4c5e-902d-abe252abfb43
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Templates["{conditionalAccessTemplate-id}"].GetAsync();
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
templates, err := graphClient.Identity().ConditionalAccess().Templates().ByConditionalAccessTemplateId("conditionalAccessTemplate-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessTemplate result = graphClient.identity().conditionalAccess().templates().byConditionalAccessTemplateId("{conditionalAccessTemplate-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let conditionalAccessTemplate = await client.api('/identity/conditionalAccess/templates/c7503427-338e-4c5e-902d-abe252abfb43')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identity()->conditionalAccess()->templates()->byConditionalAccessTemplateId('conditionalAccessTemplate-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityConditionalAccessTemplate -ConditionalAccessTemplateId $conditionalAccessTemplateId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity.conditional_access.templates.by_conditional_access_template_id('conditionalAccessTemplate-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/conditionalAccess/templates/$entity",
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
```

### Example 2: Select details of a template

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
GET https://graph.microsoft.com/v1.0/identity/conditionalAccess/templates/c7503427-338e-4c5e-902d-abe252abfb43?$select=details
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Templates["{conditionalAccessTemplate-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "details" };
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

requestParameters := &graphidentity.ConditionalAccessTemplatesItemRequestBuilderGetQueryParameters{
	Select: [] string {"details"},
}
configuration := &graphidentity.ConditionalAccessTemplatesItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
templates, err := graphClient.Identity().ConditionalAccess().Templates().ByConditionalAccessTemplateId("conditionalAccessTemplate-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessTemplate result = graphClient.identity().conditionalAccess().templates().byConditionalAccessTemplateId("{conditionalAccessTemplate-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"details"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let conditionalAccessTemplate = await client.api('/identity/conditionalAccess/templates/c7503427-338e-4c5e-902d-abe252abfb43')
	.select('details')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\ConditionalAccess\Templates\Item\ConditionalAccessTemplateItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ConditionalAccessTemplateItemRequestBuilderGetRequestConfiguration();
$queryParameters = ConditionalAccessTemplateItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["details"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identity()->conditionalAccess()->templates()->byConditionalAccessTemplateId('conditionalAccessTemplate-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgIdentityConditionalAccessTemplate -ConditionalAccessTemplateId $conditionalAccessTemplateId -Property "details" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.conditional_access.templates.item.conditional_access_template_item_request_builder import ConditionalAccessTemplateItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ConditionalAccessTemplateItemRequestBuilder.ConditionalAccessTemplateItemRequestBuilderGetQueryParameters(
		select = ["details"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity.conditional_access.templates.by_conditional_access_template_id('conditionalAccessTemplate-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/conditionalAccess/templates(details)/$entity",
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
```
