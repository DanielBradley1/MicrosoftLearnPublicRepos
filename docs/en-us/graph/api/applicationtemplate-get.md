<!-- Source: https://learn.microsoft.com/en-us/graph/api/applicationtemplate-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Get applicationTemplate

Namespace: microsoft.graph

Retrieve the properties of an [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) object. Details about optional risk properties such as **riskScore** and **riskFactors** are available with either the Microsoft Entra Suite or Microsoft Entra Internet Access license.

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
GET /applicationTemplates/{id}
```

## Optional query parameters

You can use a `$select` query parameter to specify only the properties you need for best performance. The **id** property is always returned. The `riskFactors` and `riskScore` properties aren't returned by default. You must use `$select` to include them. See [Example 2](#example-2-get-application-template-with-optional-properties).

For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and the requested [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get application template

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
GET https://graph.microsoft.com/v1.0/applicationTemplates/00000007-0000-0000-c000-000000000000
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates["{applicationTemplate-id}"].GetAsync();
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
applicationTemplates, err := graphClient.ApplicationTemplates().ByApplicationTemplateId("applicationTemplate-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationTemplate result = graphClient.applicationTemplates().byApplicationTemplateId("{applicationTemplate-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationTemplate = await client.api('/applicationTemplates/00000007-0000-0000-c000-000000000000')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->applicationTemplates()->byApplicationTemplateId('applicationTemplate-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplicationTemplate -ApplicationTemplateId $applicationTemplateId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.application_templates.by_application_template_id('applicationTemplate-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applicationTemplates/$entity",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET applicationTemplates('<guid>')?$select=categories,description",
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
```

### Example 2: Get application template with optional properties

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
GET https://graph.microsoft.com/v1.0/applicationTemplates/006a06ef-9160-42cd-88bf-17a7588fc844?$select=id,displayName,riskScore,riskFactors
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ApplicationTemplates["{applicationTemplate-id}"].GetAsync((requestConfiguration) =>
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

requestParameters := &graphapplicationtemplates.ApplicationTemplateItemRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","riskScore","riskFactors"},
}
configuration := &graphapplicationtemplates.ApplicationTemplateItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applicationTemplates, err := graphClient.ApplicationTemplates().ByApplicationTemplateId("applicationTemplate-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ApplicationTemplate result = graphClient.applicationTemplates().byApplicationTemplateId("{applicationTemplate-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "riskScore", "riskFactors"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let applicationTemplate = await client.api('/applicationTemplates/006a06ef-9160-42cd-88bf-17a7588fc844')
	.select('id,displayName,riskScore,riskFactors')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ApplicationTemplates\Item\ApplicationTemplateItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ApplicationTemplateItemRequestBuilderGetRequestConfiguration();
$queryParameters = ApplicationTemplateItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","riskScore","riskFactors"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->applicationTemplates()->byApplicationTemplateId('applicationTemplate-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

Get-MgApplicationTemplate -ApplicationTemplateId $applicationTemplateId -Property "id,displayName,riskScore,riskFactors" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.application_templates.item.application_template_item_request_builder import ApplicationTemplateItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ApplicationTemplateItemRequestBuilder.ApplicationTemplateItemRequestBuilderGetQueryParameters(
		select = ["id","displayName","riskScore","riskFactors"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.application_templates.by_application_template_id('applicationTemplate-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applicationTemplates(id,displayName,riskScore,riskFactors)/$entity",
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
```
