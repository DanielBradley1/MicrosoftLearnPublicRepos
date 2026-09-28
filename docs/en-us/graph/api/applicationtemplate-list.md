<!-- Source: https://learn.microsoft.com/en-us/graph/api/applicationtemplate-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# List applicationTemplates

Namespace: microsoft.graph

Retrieve a list of [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) objects from the Microsoft Entra application gallery. Details about optional risk properties such as **riskScore** and **riskFactors** are available with either the Microsoft Entra Suite or Microsoft Entra Internet Access license.

If a risk property is included in the request without appropriate license, a `@microsoft.graph.licenseRequired` OData annotation is returned in the response.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Additional permissions aren't required to call this API, as long as your application has a valid access token to call Microsoft Graph.

## HTTP request

```http
GET /applicationTemplates
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response.

- You can use `$filter`, `$orderby`, `$top,` and `$skip` query parameters in any GET request.

For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer: odata.maxpagesize={int-value} | Optional. `int-value` is a number up to 2,800 when query parameters are not applied; or up to 200 when query parameters are applied. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: List all application templates

The following example shows how to retrieve all application templates.

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

```msgraph
GET https://graph.microsoft.com/v1.0/applicationTemplates
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates.GetAsync();
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
applicationTemplates, err := graphClient.ApplicationTemplates().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationTemplateCollectionResponse result = graphClient.applicationTemplates().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationTemplates = await client.api('/applicationTemplates')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->applicationTemplates()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplicationTemplate
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.application_templates.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applicationTemplates",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET applicationTemplates?$select=categories,description",
    "value": [
        {
            "id": "00000007-0000-0000-c000-000000000000",
            "displayName": "Dynamics CRM Online",
            "homePageUrl": "http://www.microsoft.com/dynamics/crm",
            "supportedSingleSignOnModes": [
                "oidc",
                "external"
            ],
            "supportedProvisioningTypes": [],
            "logoUrl": "https://az495088.vo.msecnd.net/app-logo/crm_215.png",
            "categories": [
                "crm",
                "productivity",
                "collaboration",
                "businessMgmt"
            ],
            "publisher": "Microsoft Corporation",
            "description": null,
            "deprecationDate": null,
            "endpoints": [
                "crm2.dynamics.com",
                "crm.dynamics.com",
                "crm6.dynamics.com",
                "crm5.dynamics.com",
                "crm4.dynamics.com",
                "svc.dynamics.com",
                "dynamics.microsoft.com",
                "dynamics.com",
                "microsoftdynamics.us",
                "home.dynamics.com",
                "crm11.dynamics.com"
            ],
            "lastModifiedDateTime": "2026-03-27T16:51:49.594913Z",
            "isEntraIntegrated": true
        }
    ]
}
```

### Example 2: List all application templates with optional properties \(with appropriate license\)

The following example shows how to retrieve all application templates with optional properties.

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

```msgraph
GET https://graph.microsoft.com/v1.0/applicationTemplates?$select=id,displayName,riskScore,riskFactors
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","riskScore","riskFactors" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplicationtemplates "github.com/microsoftgraph/msgraph-sdk-go/applicationtemplates"
	  //other-imports
)

requestParameters := &graphapplicationtemplates.ApplicationTemplatesRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","riskScore","riskFactors"},
}
configuration := &graphapplicationtemplates.ApplicationTemplatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applicationTemplates, err := graphClient.ApplicationTemplates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationTemplateCollectionResponse result = graphClient.applicationTemplates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "riskScore", "riskFactors"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationTemplates = await client.api('/applicationTemplates')
	.select('id,displayName,riskScore,riskFactors')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ApplicationTemplates\ApplicationTemplatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ApplicationTemplatesRequestBuilderGetRequestConfiguration();
$queryParameters = ApplicationTemplatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","riskScore","riskFactors"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->applicationTemplates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplicationTemplate -Property "id,displayName,riskScore,riskFactors" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.application_templates.application_templates_request_builder import ApplicationTemplatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ApplicationTemplatesRequestBuilder.ApplicationTemplatesRequestBuilderGetQueryParameters(
		select = ["id","displayName","riskScore","riskFactors"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.application_templates.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applicationTemplates",
    "value": [
        {
            "id": "de92ca39-7b85-4b4c-90d8-2885eff5100b",
            "displayName": "LinkedIn Lookup",
            "riskScore": {
                "total": 9.910557,
                "security": 9.95,
                "provider": 9.611832,
                "compliance": 9.931034,
                "legal": 10.0
            },
                "riskFactors": {
                    "general": {
                        "hasDisasterRecoveryPlan": true
                        // ... omitted for brevity
                    },
                    "security": {
                        "hasMFA": true
                        // ... omitted for brevity
                    },
                    "compliance": {
                        "cobit": true
                        // ... omitted for brevity
                    },
                    "legal": {
                        "hasDmca": null
                        // ... omitted for brevity
                    }
                }
        }
    ]
}
```

### Example 3: List all application templates with optional properties \(without appropriate license\)

The following example shows how to retrieve all application templates with optional properties when the tenant lacks Microsoft Entra Suite or Microsoft Entra Internet Access subscription.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/applicationTemplates?$select=id,displayName,riskScore,riskFactors
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","riskScore","riskFactors" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplicationtemplates "github.com/microsoftgraph/msgraph-sdk-go/applicationtemplates"
	  //other-imports
)

requestParameters := &graphapplicationtemplates.ApplicationTemplatesRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","riskScore","riskFactors"},
}
configuration := &graphapplicationtemplates.ApplicationTemplatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applicationTemplates, err := graphClient.ApplicationTemplates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationTemplateCollectionResponse result = graphClient.applicationTemplates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "riskScore", "riskFactors"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationTemplates = await client.api('/applicationTemplates')
	.select('id,displayName,riskScore,riskFactors')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ApplicationTemplates\ApplicationTemplatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ApplicationTemplatesRequestBuilderGetRequestConfiguration();
$queryParameters = ApplicationTemplatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","riskScore","riskFactors"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->applicationTemplates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplicationTemplate -Property "id,displayName,riskScore,riskFactors" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.application_templates.application_templates_request_builder import ApplicationTemplatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ApplicationTemplatesRequestBuilder.ApplicationTemplatesRequestBuilderGetQueryParameters(
		select = ["id","displayName","riskScore","riskFactors"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.application_templates.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applicationTemplates",
    "@microsoft.graph.licenseRequired": "An Entra Suite or Entra Internet Access license is required to show riskScore or riskFactors properties. For more info see aka.ms/applicationTemplateEndpointLicensing",
    "value": [
        {
            "id": "de92ca39-7b85-4b4c-90d8-2885eff5100b",
            "displayName": "LinkedIn Lookup",
            "riskScore": null,
            "riskFactors": null
        }
    ]
}
```

### Example 4: List application templates with filtering and ordering

The following example shows how to get the top two application templates, sorted by total risk score, that are classified in the `contentSharing` category.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/applicationTemplates?$select=id,displayName,riskScore,categories&$filter=categories/any(c: c eq 'contentSharing')&$top=2&$orderby=riskScore/total desc
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","riskScore","categories" };
	requestConfiguration.QueryParameters.Filter = "categories/any(c: c eq 'contentSharing')";
	requestConfiguration.QueryParameters.Top = 2;
	requestConfiguration.QueryParameters.Orderby = new string []{ "riskScore/total desc" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplicationtemplates "github.com/microsoftgraph/msgraph-sdk-go/applicationtemplates"
	  //other-imports
)


requestFilter := "categories/any(c: c eq 'contentSharing')"
requestTop := int32(2)

requestParameters := &graphapplicationtemplates.ApplicationTemplatesRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","riskScore","categories"},
	Filter: &requestFilter,
	Top: &requestTop,
	Orderby: [] string {"riskScore/total desc"},
}
configuration := &graphapplicationtemplates.ApplicationTemplatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applicationTemplates, err := graphClient.ApplicationTemplates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationTemplateCollectionResponse result = graphClient.applicationTemplates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "riskScore", "categories"};
	requestConfiguration.queryParameters.filter = "categories/any(c: c eq 'contentSharing')";
	requestConfiguration.queryParameters.top = 2;
	requestConfiguration.queryParameters.orderby = new String []{"riskScore/total desc"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationTemplates = await client.api('/applicationTemplates')
	.filter('categories/any(c: c eq \'contentSharing\')')
	.select('id,displayName,riskScore,categories')
	.orderby('riskScore/total desc')
	.top(2)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ApplicationTemplates\ApplicationTemplatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ApplicationTemplatesRequestBuilderGetRequestConfiguration();
$queryParameters = ApplicationTemplatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","riskScore","categories"];
$queryParameters->filter = "categories/any(c: c eq 'contentSharing')";
$queryParameters->top = 2;
$queryParameters->orderby = ["riskScore/total desc"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->applicationTemplates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplicationTemplate -Property "id,displayName,riskScore,categories" -Filter "categories/any(c: c eq 'contentSharing')" -Top 2 -Sort "riskScore/total desc" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.application_templates.application_templates_request_builder import ApplicationTemplatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ApplicationTemplatesRequestBuilder.ApplicationTemplatesRequestBuilderGetQueryParameters(
		select = ["id","displayName","riskScore","categories"],
		filter = "categories/any(c: c eq 'contentSharing')",
		top = 2,
		orderby = ["riskScore/total desc"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.application_templates.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applicationTemplates",
    "value": [
        {
            "id": "2af39c45-8bb3-5369-9341-696181ebfa55",
            "displayName": "Contoso network",
            "categories": [
                "contentSharing"
            ],
            "riskScore": {
                "total": 9.610546,
                "security": 9.833333,
                "provider": 9.475291,
                "compliance": 9.923077,
                "legal": 9.142858
            }
        },
        {
            "id": "e0e5def8-f27e-5445-93f3-02ea8733a811",
            "displayName": "Fourth Coffee",
            "categories": [
                "contentSharing"
            ],
            "riskScore": {
                "total": 8.562663,
                "security": 8.266666,
                "provider": 8.833883,
                "compliance": 8.142858,
                "legal": 9.142858
            }
        }
    ]
}
```
