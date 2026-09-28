<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-access-package-api -->
<!-- Sitemap-Last-Modified: 2025-03-21 -->

# Manage access to resources using the entitlement management APIs

Microsoft Entra entitlement management lets you manage resource access at scale for employees and guests in your organization. This tutorial shows how to use entitlement management APIs to create a resource package that internal users can request. The APIs offer a programmatic alternative to creating custom apps in the Microsoft Entra admin center.

In this tutorial, you learn how to:

- Create an access package that users can request themselves.
- Assign a group resource to the access package.
- Request an access package.

## Prerequisites

To complete this tutorial, you need:

- A Microsoft Entra tenant with either a Microsoft Entra ID P2 or Microsoft Entra ID Governance license.
- A test guest account and a test security group in your tenant. The security group is the resource in this tutorial. Ensure you're either the owner of the group or assigned the Groups Administrator role. In this tutorial:

  - The user has the ID `007d1c7e-7fa8-4e33-b678-5e437acdcddc` and is named `Requestor1`.
  - The group has the ID `f4892fac-e81c-4712-bdf2-a4450008a4b0` with the "Marketing group" description and "Marketing resources" display name.

- An API client such as [Graph Explorer](https://aka.ms/ge) signed in with an account that has at least the Identity Governance Administrator role
- Delegated permissions:

  - `User.ReadWrite.All`
  - `Group.ReadWrite.All`
  - `EntitlementManagement.ReadWrite.All`

- \[Optional\] An anonymous browser window. Sign in later in this tutorial.

Note

Some steps in this tutorial use the `beta` endpoint.

## Step 1: Add resources to a catalog and create an access package

An access package is a bundle of resources that a team or project needs and is governed with policies. Access packages are defined in containers called catalogs. Catalogs can reference resources, such as groups, apps, and sites, that are used in the access package. Entitlement management includes a default `General` catalog.

In this step, you create a **Marketing Campaign** access package in the General catalog.

### Step 1.1: Get the identifier for the General catalog

Get the ID of the **General** catalog.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs?$filter=(displayName eq 'General')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "(displayName eq 'General')";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "(displayName eq 'General')"

requestParameters := &graphidentitygovernance.EntitlementManagementCatalogsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.EntitlementManagementCatalogsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
catalogs, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageCatalogCollectionResponse result = graphClient.identityGovernance().entitlementManagement().catalogs().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "(displayName eq 'General')";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let catalogs = await client.api('/identityGovernance/entitlementManagement/catalogs')
	.filter('(displayName eq \'General\')')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\EntitlementManagement\Catalogs\CatalogsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new CatalogsRequestBuilderGetRequestConfiguration();
$queryParameters = CatalogsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "(displayName eq 'General')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgEntitlementManagementCatalog -Filter "(displayName eq 'General')" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.entitlement_management.catalogs.catalogs_request_builder import CatalogsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = CatalogsRequestBuilder.CatalogsRequestBuilderGetQueryParameters(
		filter = "(displayName eq 'General')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.entitlement_management.catalogs.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/catalogs",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/entitlementManagement/catalogs?$select=catalogType,createdDateTime",
    "value": [
        {
            "id": "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
            "displayName": "General",
            "description": "Built-in catalog.",
            "catalogType": "serviceDefault",
            "state": "published",
            "isExternallyVisible": true,
            "createdDateTime": "2023-04-13T14:43:19.44Z",
            "modifiedDateTime": "2023-04-13T14:43:19.44Z"
        }
    ]
}
```

### Step 1.2: Add the group to the catalog

In this step, you add the "Marketing resources" group to the **General** catalog as a resource.

If you're not the owner of the group that you reference in **originId** or aren't assigned the Groups Administrator role, then this request fails with a `403 Forbidden` error code.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
  "catalogId":"cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
  "requestType": "AdminAdd",
  "justification": "",
  "accessPackageResource": {
    "resourceType": "AadGroup",
    "originId": "e93e24d1-2b65-4a6c-a1dd-654a12225487",
    "originSystem": "AadGroup"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"catalogId" , "cec5d6ab-c75d-47c0-9c1c-92e89f66e384"
		},
		{
			"justification" , ""
		},
		{
			"accessPackageResource" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"resourceType", new UntypedString("AadGroup")
				},
				{
					"originId", new UntypedString("e93e24d1-2b65-4a6c-a1dd-654a12225487")
				},
				{
					"originSystem", new UntypedString("AadGroup")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
additionalData := map[string]interface{}{
	"catalogId" : "cec5d6ab-c75d-47c0-9c1c-92e89f66e384", 
	"justification" : "", 
accessPackageResource := graph.New()
resourceType := "AadGroup"
accessPackageResource.SetResourceType(&resourceType) 
originId := "e93e24d1-2b65-4a6c-a1dd-654a12225487"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AadGroup"
accessPackageResource.SetOriginSystem(&originSystem) 
	requestBody.SetAccessPackageResource(accessPackageResource)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminAdd);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("catalogId", "cec5d6ab-c75d-47c0-9c1c-92e89f66e384");
additionalData.put("justification", "");
 accessPackageResource = new ();
accessPackageResource.setResourceType("AadGroup");
accessPackageResource.setOriginId("e93e24d1-2b65-4a6c-a1dd-654a12225487");
accessPackageResource.setOriginSystem("AadGroup");
additionalData.put("accessPackageResource", accessPackageResource);
accessPackageResourceRequest.setAdditionalData(additionalData);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  catalogId: 'cec5d6ab-c75d-47c0-9c1c-92e89f66e384',
  requestType: 'AdminAdd',
  justification: '',
  accessPackageResource: {
    resourceType: 'AadGroup',
    originId: 'e93e24d1-2b65-4a6c-a1dd-654a12225487',
    originSystem: 'AadGroup'
  }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$additionalData = [
	'catalogId' => 'cec5d6ab-c75d-47c0-9c1c-92e89f66e384',
	'justification' => '',
	'accessPackageResource' => [
		'resourceType' => 'AadGroup',
		'originId' => 'e93e24d1-2b65-4a6c-a1dd-654a12225487',
		'originSystem' => 'AadGroup',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	catalogId = "cec5d6ab-c75d-47c0-9c1c-92e89f66e384"
	requestType = "AdminAdd"
	justification = ""
	accessPackageResource = @{
		resourceType = "AadGroup"
		originId = "e93e24d1-2b65-4a6c-a1dd-654a12225487"
		originSystem = "AadGroup"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	additional_data = {
			"catalog_id" : "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
			"justification" : "",
			"access_package_resource" : {
					"resource_type" : "AadGroup",
					"origin_id" : "e93e24d1-2b65-4a6c-a1dd-654a12225487",
					"origin_system" : "AadGroup",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

In this response, the **id** represents the ID for the group as a resource in the General catalog. This ID isn't the group ID. Record this ID.

> **Note:** The response object shown here might be shortened for readability.

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/resourceRequests/$entity",
    "id": "44e521e0-fb6b-4d5e-a282-e7e68dc59493",
    "requestType": "AdminAdd",
    "requestState": "Delivered",
    "requestStatus": "Fulfilled",
    "catalogId": "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
    "executeImmediately": false,
    "justification": "",
    "expirationDateTime": null
}
```

### Step 1.3: Get catalog resources

In this step, you retrieve the details of the resources that match the ID of the group resource that you added to the General catalog.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/cec5d6ab-c75d-47c0-9c1c-92e89f66e384/resources?$filter=originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs["{accessPackageCatalog-id}"].Resources.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'"

requestParameters := &graphidentitygovernance.EntitlementManagementCatalogsItemResourcesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.EntitlementManagementCatalogsItemResourcesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resources, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").Resources().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceCollectionResponse result = graphClient.identityGovernance().entitlementManagement().catalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").resources().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let resources = await client.api('/identityGovernance/entitlementManagement/catalogs/cec5d6ab-c75d-47c0-9c1c-92e89f66e384/resources')
	.filter('originId eq \'e93e24d1-2b65-4a6c-a1dd-654a12225487\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\EntitlementManagement\Catalogs\Item\Resources\ResourcesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ResourcesRequestBuilderGetRequestConfiguration();
$queryParameters = ResourcesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->resources()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgEntitlementManagementCatalogResource -AccessPackageCatalogId $accessPackageCatalogId -Filter "originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.entitlement_management.catalogs.item.resources.resources_request_builder import ResourcesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ResourcesRequestBuilder.ResourcesRequestBuilderGetQueryParameters(
		filter = "originId eq 'e93e24d1-2b65-4a6c-a1dd-654a12225487'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.entitlement_management.catalogs.by_access_package_catalog_id('accessPackageCatalog-id').resources.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/catalogs('cec5d6ab-c75d-47c0-9c1c-92e89f66e384')/resources",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/entitlementManagement/catalogs('<guid>')/resources?$select=attributes,createdDateTime",
  "value": [
    {
      "id": "4a1e21c5-8a76-4578-acb1-641160e076e8",
      "displayName": "Marketing resources",
      "description": "Marketing group",
      "originId": "e93e24d1-2b65-4a6c-a1dd-654a12225487",
      "originSystem": "AadGroup",
      "createdDateTime": "2024-03-26T09:44:50.527Z",
      "attributes": []
    }
  ]
}
```

### Step 1.4: Get resource roles

The access package assigns users to the roles of a resource. The typical role of a group is the `Member` role. Other resources, such as SharePoint Online sites and applications, might have many roles. The typical role of a group used in an access package is the `Member` role. You need the member role to add a resource role to the access package later in this tutorial.

In the request, use the **id** of the catalog and the **id** of the group resource in the catalog that you recorded to get the **originId** of the Member resource role. Record the value of the **originId** property to use later in this tutorial.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/ede67938-cda7-4127-a9ca-7c7bf86a19b7/resourceRoles?$filter=(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')&$expand=resource
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs["{accessPackageCatalog-id}"].ResourceRoles.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')";
	requestConfiguration.QueryParameters.Expand = new string []{ "resource" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')"

requestParameters := &graphidentitygovernance.EntitlementManagementCatalogsItemResourceRolesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Expand: [] string {"resource"},
}
configuration := &graphidentitygovernance.EntitlementManagementCatalogsItemResourceRolesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoles, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").ResourceRoles().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleCollectionResponse result = graphClient.identityGovernance().entitlementManagement().catalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").resourceRoles().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')";
	requestConfiguration.queryParameters.expand = new String []{"resource"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let resourceRoles = await client.api('/identityGovernance/entitlementManagement/catalogs/ede67938-cda7-4127-a9ca-7c7bf86a19b7/resourceRoles')
	.filter('(originSystem eq \'AadGroup\' and displayName eq \'Member\' and resource/id eq \'274a1e21c5-8a76-4578-acb1-641160e076e\')')
	.expand('resource/id eq \'274a1e21c5-8a76-4578-acb1-641160e076e\')')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\EntitlementManagement\Catalogs\Item\ResourceRoles\ResourceRolesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new ResourceRolesRequestBuilderGetRequestConfiguration();
$queryParameters = ResourceRolesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')";
$queryParameters->expand = ["resource"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->resourceRoles()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgEntitlementManagementCatalogResourceRole -AccessPackageCatalogId $accessPackageCatalogId -Filter "(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')" -ExpandProperty "resource" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.entitlement_management.catalogs.item.resource_roles.resource_roles_request_builder import ResourceRolesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = ResourceRolesRequestBuilder.ResourceRolesRequestBuilderGetQueryParameters(
		filter = "(originSystem eq 'AadGroup' and displayName eq 'Member' and resource/id eq '274a1e21c5-8a76-4578-acb1-641160e076e')",
		expand = ["resource"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.entitlement_management.catalogs.by_access_package_catalog_id('accessPackageCatalog-id').resource_roles.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

Because you filtered by the originId, display name and resource ID, if successful, a single value is returned, which represents the Member role of that group. If no roles are returned, check the **id** values of the catalog and the access package resource.

> **Note:** The response object shown here might be shortened for readability.

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/catalogs('ede67938-cda7-4127-a9ca-7c7bf86a19b7')/resourceRoles(resource())",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/entitlementManagement/catalogs('<guid>')/resourceRoles?$select=description,displayName",
    "value": [
        {
            "id": "00000000-0000-0000-0000-000000000000",
            "displayName": "Member",
            "description": null,
            "originSystem": "AadGroup",
            "originId": "Member_e93e24d1-2b65-4a6c-a1dd-654a12225487",
            "resource@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/catalogs('ede67938-cda7-4127-a9ca-7c7bf86a19b7')/resourceRoles('00000000-0000-0000-0000-000000000000')/resource/$entity",
            "resource": {
                "id": "ec09e90e-e021-4599-a8c3-bce77c2b2000",
                "displayName": "Marketing resources",
                "description": "Marketing group",
                "originId": "e93e24d1-2b65-4a6c-a1dd-654a12225487",
                "originSystem": "AadGroup",
                "createdDateTime": "2023-04-13T14:43:21.43Z",
                "attributes": []
            }
        }
    ]
}
```

### Step 1.5: Create the access package

You now have a catalog with a group resource, and you want to use the resource role of group member in the access package. The next step is to create the access package. After you have the access package, you can add the resource role to it, and create a policy for how users can request access to that resource role. You use the **id** of the catalog that you recorded earlier to create the access package. Record the **id** of the access package to use later in this tutorial.

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages
Content-type: application/json

{
  "catalogId": "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
  "displayName": "Marketing Campaign",
  "description": "Access to resources for the campaign"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackage
{
	DisplayName = "Marketing Campaign",
	Description = "Access to resources for the campaign",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"catalogId" , "cec5d6ab-c75d-47c0-9c1c-92e89f66e384"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackage()
displayName := "Marketing Campaign"
requestBody.SetDisplayName(&displayName) 
description := "Access to resources for the campaign"
requestBody.SetDescription(&description) 
additionalData := map[string]interface{}{
	"catalogId" : "cec5d6ab-c75d-47c0-9c1c-92e89f66e384", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackages, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackage accessPackage = new AccessPackage();
accessPackage.setDisplayName("Marketing Campaign");
accessPackage.setDescription("Access to resources for the campaign");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("catalogId", "cec5d6ab-c75d-47c0-9c1c-92e89f66e384");
accessPackage.setAdditionalData(additionalData);
AccessPackage result = graphClient.identityGovernance().entitlementManagement().accessPackages().post(accessPackage);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackage = {
  catalogId: 'cec5d6ab-c75d-47c0-9c1c-92e89f66e384',
  displayName: 'Marketing Campaign',
  description: 'Access to resources for the campaign'
};

await client.api('/identityGovernance/entitlementManagement/accessPackages')
	.post(accessPackage);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackage();
$requestBody->setDisplayName('Marketing Campaign');
$requestBody->setDescription('Access to resources for the campaign');
$additionalData = [
	'catalogId' => 'cec5d6ab-c75d-47c0-9c1c-92e89f66e384',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	catalogId = "cec5d6ab-c75d-47c0-9c1c-92e89f66e384"
	displayName = "Marketing Campaign"
	description = "Access to resources for the campaign"
}

New-MgEntitlementManagementAccessPackage -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package import AccessPackage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackage(
	display_name = "Marketing Campaign",
	description = "Access to resources for the campaign",
	additional_data = {
			"catalog_id" : "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
	}
)

result = await graph_client.identity_governance.entitlement_management.access_packages.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackages/$entity",
    "id": "88203d16-0e31-41d4-87b2-dd402f1435e9",
    "catalogId": "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
    "displayName": "Marketing Campaign",
    "description": "Access to resources for the campaign",
    "isHidden": false,
    "isRoleScopesVisible": false,
    "createdBy": "admin@contoso.com",
    "createdDateTime": "2024-03-26T17:36:45.411033Z",
    "modifiedBy": "admin@contoso.com",
    "modifiedDateTime": "2024-03-26T17:36:45.411033Z"
}
```

### Step 1.6: Add a resource role to the access package

#### Request

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/88203d16-0e31-41d4-87b2-dd402f1435e9/accessPackageResourceRoleScopes
Content-type: application/json

{
  "role": {
    "originId":"Member_f4892fac-e81c-4712-bdf2-a4450008a4b0",
    "displayName":"Member",
    "originSystem":"AadGroup",
    "resource": {
      "id":"4a1e21c5-8a76-4578-acb1-641160e076e8",
      "resourceType":"Security Group",
      "originId":"f4892fac-e81c-4712-bdf2-a4450008a4b0",
      "originSystem":"AadGroup"
    }
  },
  "scope": {
    "originId":"f4892fac-e81c-4712-bdf2-a4450008a4b0",
    "originSystem":"AadGroup"
  }
}
```

#### Response

```http
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/entitlementManagement/accessPackages('88203d16-0e31-41d4-87b2-dd402f1435e9')/accessPackageResourceRoleScopes/$entity",
  "id": "e081321b-2802-4834-a6ca-6f598ce3cdf7_6dbd2209-9d14-4c76-b92b-fcb00e835fe1",
  "createdDateTime": "2024-03-26T19:56:00.6320729Z",
}
```

The access package now has one resource role, which is group membership. The role is assigned to any user who has the access package.

### Step 1.7: Create an access package policy

Now that you created the access package and added resources and roles, you can decide who can access it by creating an access package policy. In this tutorial, you enable the **Requestor1** account that you created to request access to the resources in the access package. For this task, you need these values:

- **id** of the access package for the value of the **accessPackageId** property
- **id** of the **Requestor1** user account for the value of the **id** property in **allowedRequestors**

The value of the **durationInDays** property enables the **Requestor1** account to access the resources in the access package for up to 30 days. Record the value of the **id** property that is returned to use later in this tutorial.

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies
Content-type: application/json

{
  "accessPackageId": "88203d16-0e31-41d4-87b2-dd402f1435e9",
  "displayName": "Specific users",
  "description": "Specific users can request assignment",
  "accessReviewSettings": null,
  "durationInDays": 30,
  "requestorSettings": {
    "scopeType": "SpecificDirectorySubjects",
    "acceptRequests": true,
    "allowedRequestors": [
       {
         "@odata.type": "#microsoft.graph.singleUser",
         "isBackup": false,
         "id": "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
         "description": "Requestor1"
       }
    ]
  },
  "requestApprovalSettings": {
    "isApprovalRequired": false,
    "isApprovalRequiredForExtension": false,
    "isRequestorJustificationRequired": false,
    "approvalMode": "NoApproval",
    "approvalStages": []
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentPolicy
{
	AccessPackageId = "88203d16-0e31-41d4-87b2-dd402f1435e9",
	DisplayName = "Specific users",
	Description = "Specific users can request assignment",
	AccessReviewSettings = null,
	DurationInDays = 30,
	RequestorSettings = new RequestorSettings
	{
		ScopeType = "SpecificDirectorySubjects",
		AcceptRequests = true,
		AllowedRequestors = new List<UserSet>
		{
			new SingleUser
			{
				OdataType = "#microsoft.graph.singleUser",
				IsBackup = false,
				Id = "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
				Description = "Requestor1",
			},
		},
	},
	RequestApprovalSettings = new ApprovalSettings
	{
		IsApprovalRequired = false,
		IsApprovalRequiredForExtension = false,
		IsRequestorJustificationRequired = false,
		ApprovalMode = "NoApproval",
		ApprovalStages = new List<ApprovalStage>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentPolicy()
accessPackageId := "88203d16-0e31-41d4-87b2-dd402f1435e9"
requestBody.SetAccessPackageId(&accessPackageId) 
displayName := "Specific users"
requestBody.SetDisplayName(&displayName) 
description := "Specific users can request assignment"
requestBody.SetDescription(&description) 
accessReviewSettings := null
requestBody.SetAccessReviewSettings(&accessReviewSettings) 
durationInDays := int32(30)
requestBody.SetDurationInDays(&durationInDays) 
requestorSettings := graphmodels.NewRequestorSettings()
scopeType := "SpecificDirectorySubjects"
requestorSettings.SetScopeType(&scopeType) 
acceptRequests := true
requestorSettings.SetAcceptRequests(&acceptRequests) 


userSet := graphmodels.NewSingleUser()
isBackup := false
userSet.SetIsBackup(&isBackup) 
id := "007d1c7e-7fa8-4e33-b678-5e437acdcddc"
userSet.SetId(&id) 
description := "Requestor1"
userSet.SetDescription(&description) 

allowedRequestors := []graphmodels.UserSetable {
	userSet,
}
requestorSettings.SetAllowedRequestors(allowedRequestors)
requestBody.SetRequestorSettings(requestorSettings)
requestApprovalSettings := graphmodels.NewApprovalSettings()
isApprovalRequired := false
requestApprovalSettings.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
requestApprovalSettings.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := false
requestApprovalSettings.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "NoApproval"
requestApprovalSettings.SetApprovalMode(&approvalMode) 
approvalStages := []graphmodels.ApprovalStageable {

}
requestApprovalSettings.SetApprovalStages(approvalStages)
requestBody.SetRequestApprovalSettings(requestApprovalSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentPolicies, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentPolicy accessPackageAssignmentPolicy = new AccessPackageAssignmentPolicy();
accessPackageAssignmentPolicy.setAccessPackageId("88203d16-0e31-41d4-87b2-dd402f1435e9");
accessPackageAssignmentPolicy.setDisplayName("Specific users");
accessPackageAssignmentPolicy.setDescription("Specific users can request assignment");
accessPackageAssignmentPolicy.setAccessReviewSettings(null);
accessPackageAssignmentPolicy.setDurationInDays(30);
RequestorSettings requestorSettings = new RequestorSettings();
requestorSettings.setScopeType("SpecificDirectorySubjects");
requestorSettings.setAcceptRequests(true);
LinkedList<UserSet> allowedRequestors = new LinkedList<UserSet>();
SingleUser userSet = new SingleUser();
userSet.setOdataType("#microsoft.graph.singleUser");
userSet.setIsBackup(false);
userSet.setId("007d1c7e-7fa8-4e33-b678-5e437acdcddc");
userSet.setDescription("Requestor1");
allowedRequestors.add(userSet);
requestorSettings.setAllowedRequestors(allowedRequestors);
accessPackageAssignmentPolicy.setRequestorSettings(requestorSettings);
ApprovalSettings requestApprovalSettings = new ApprovalSettings();
requestApprovalSettings.setIsApprovalRequired(false);
requestApprovalSettings.setIsApprovalRequiredForExtension(false);
requestApprovalSettings.setIsRequestorJustificationRequired(false);
requestApprovalSettings.setApprovalMode("NoApproval");
LinkedList<ApprovalStage> approvalStages = new LinkedList<ApprovalStage>();
requestApprovalSettings.setApprovalStages(approvalStages);
accessPackageAssignmentPolicy.setRequestApprovalSettings(requestApprovalSettings);
AccessPackageAssignmentPolicy result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().post(accessPackageAssignmentPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentPolicy = {
  accessPackageId: '88203d16-0e31-41d4-87b2-dd402f1435e9',
  displayName: 'Specific users',
  description: 'Specific users can request assignment',
  accessReviewSettings: null,
  durationInDays: 30,
  requestorSettings: {
    scopeType: 'SpecificDirectorySubjects',
    acceptRequests: true,
    allowedRequestors: [
       {
         '@odata.type': '#microsoft.graph.singleUser',
         isBackup: false,
         id: '007d1c7e-7fa8-4e33-b678-5e437acdcddc',
         description: 'Requestor1'
       }
    ]
  },
  requestApprovalSettings: {
    isApprovalRequired: false,
    isApprovalRequiredForExtension: false,
    isRequestorJustificationRequired: false,
    approvalMode: 'NoApproval',
    approvalStages: []
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies')
	.version('beta')
	.post(accessPackageAssignmentPolicy);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentPolicy;
use Microsoft\Graph\Beta\Generated\Models\RequestorSettings;
use Microsoft\Graph\Beta\Generated\Models\UserSet;
use Microsoft\Graph\Beta\Generated\Models\SingleUser;
use Microsoft\Graph\Beta\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Beta\Generated\Models\ApprovalStage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentPolicy();
$requestBody->setAccessPackageId('88203d16-0e31-41d4-87b2-dd402f1435e9');
$requestBody->setDisplayName('Specific users');
$requestBody->setDescription('Specific users can request assignment');
$requestBody->setAccessReviewSettings(null);
$requestBody->setDurationInDays(30);
$requestorSettings = new RequestorSettings();
$requestorSettings->setScopeType('SpecificDirectorySubjects');
$requestorSettings->setAcceptRequests(true);
$allowedRequestorsUserSet1 = new SingleUser();
$allowedRequestorsUserSet1->setOdataType('#microsoft.graph.singleUser');
$allowedRequestorsUserSet1->setIsBackup(false);
$allowedRequestorsUserSet1->setId('007d1c7e-7fa8-4e33-b678-5e437acdcddc');
$allowedRequestorsUserSet1->setDescription('Requestor1');
$allowedRequestorsArray []= $allowedRequestorsUserSet1;
$requestorSettings->setAllowedRequestors($allowedRequestorsArray);

$requestBody->setRequestorSettings($requestorSettings);
$requestApprovalSettings = new ApprovalSettings();
$requestApprovalSettings->setIsApprovalRequired(false);
$requestApprovalSettings->setIsApprovalRequiredForExtension(false);
$requestApprovalSettings->setIsRequestorJustificationRequired(false);
$requestApprovalSettings->setApprovalMode('NoApproval');
$requestApprovalSettings->setApprovalStages([]);
$requestBody->setRequestApprovalSettings($requestApprovalSettings);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageId = "88203d16-0e31-41d4-87b2-dd402f1435e9"
	displayName = "Specific users"
	description = "Specific users can request assignment"
	accessReviewSettings = $null
	durationInDays = 30
	requestorSettings = @{
		scopeType = "SpecificDirectorySubjects"
		acceptRequests = $true
		allowedRequestors = @(
			@{
				"@odata.type" = "#microsoft.graph.singleUser"
				isBackup = $false
				id = "007d1c7e-7fa8-4e33-b678-5e437acdcddc"
				description = "Requestor1"
			}
		)
	}
	requestApprovalSettings = @{
		isApprovalRequired = $false
		isApprovalRequiredForExtension = $false
		isRequestorJustificationRequired = $false
		approvalMode = "NoApproval"
		approvalStages = @(
		)
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_policy import AccessPackageAssignmentPolicy
from msgraph_beta.generated.models.requestor_settings import RequestorSettings
from msgraph_beta.generated.models.user_set import UserSet
from msgraph_beta.generated.models.single_user import SingleUser
from msgraph_beta.generated.models.approval_settings import ApprovalSettings
from msgraph_beta.generated.models.approval_stage import ApprovalStage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentPolicy(
	access_package_id = "88203d16-0e31-41d4-87b2-dd402f1435e9",
	display_name = "Specific users",
	description = "Specific users can request assignment",
	access_review_settings = None,
	duration_in_days = 30,
	requestor_settings = RequestorSettings(
		scope_type = "SpecificDirectorySubjects",
		accept_requests = True,
		allowed_requestors = [
			SingleUser(
				odata_type = "#microsoft.graph.singleUser",
				is_backup = False,
				id = "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
				description = "Requestor1",
			),
		],
	),
	request_approval_settings = ApprovalSettings(
		is_approval_required = False,
		is_approval_required_for_extension = False,
		is_requestor_justification_required = False,
		approval_mode = "NoApproval",
		approval_stages = [
		],
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignmentPolicies/$entity",
  "id": "db440482-1210-4a60-9b55-3ac7a72f63ba",
  "accessPackageId": "88203d16-0e31-41d4-87b2-dd402f1435e9",
  "displayName": "Specific users",
  "description": "Specific users can request assignment",
  "canExtend": false,
  "durationInDays": 30,
  "expirationDateTime": null,
  "createdBy": "admin@contoso.com",
  "createdDateTime": "2020-06-29T19:47:44.7399675Z",
  "modifiedBy": "admin@contoso.com",
  "modifiedDateTime": "2020-06-29T19:47:44.7555489Z",
  "accessReviewSettings": null,
  "requestorSettings": {
    "scopeType": "SpecificDirectorySubjects",
    "acceptRequests": true,
    "allowedRequestors": [
      {
        "@odata.type": "#microsoft.graph.singleUser",
        "isBackup": false,
        "id": "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
        "description": "Requestor1"
      }
    ]
  },
  "requestApprovalSettings": {
    "isApprovalRequired": false,
    "isApprovalRequiredForExtension": false,
    "isRequestorJustificationRequired": false,
    "approvalMode": "NoApproval",
    "approvalStages": []
  }
}
```

## Step 2: Request access

In this step, the **Requestor1** user account requests access to resources in the access package.

To request access to the access package, you need to provide these values:

- **id** of the **Requestor1** user account that you created for the value of the **targetId** property
- **id** of the assignment policy for the value of the **assignmentPolicyId** property
- **id** of the access package for the value of **accessPackageId** property

In the response, the status is `Accepted` and the state is `Submitted`. Record the value of the **id** property that is returned to check the status of the request later.

Open a new anonymous browser session and sign in as **Requestor1** so you don't interrupt your current administrator session. Alternatively, log out of Graph Explorer and sign in as **Requestor1**.

#### Request

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
  "requestType": "UserAdd",
  "accessPackageAssignment":{
     "targetId":"007d1c7e-7fa8-4e33-b678-5e437acdcddc",
     "assignmentPolicyId":"db440482-1210-4a60-9b55-3ac7a72f63ba",
     "accessPackageId":"88203d16-0e31-41d4-87b2-dd402f1435e9"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "UserAdd",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		TargetId = "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
		AssignmentPolicyId = "db440482-1210-4a60-9b55-3ac7a72f63ba",
		AccessPackageId = "88203d16-0e31-41d4-87b2-dd402f1435e9",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "UserAdd"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
targetId := "007d1c7e-7fa8-4e33-b678-5e437acdcddc"
accessPackageAssignment.SetTargetId(&targetId) 
assignmentPolicyId := "db440482-1210-4a60-9b55-3ac7a72f63ba"
accessPackageAssignment.SetAssignmentPolicyId(&assignmentPolicyId) 
accessPackageId := "88203d16-0e31-41d4-87b2-dd402f1435e9"
accessPackageAssignment.SetAccessPackageId(&accessPackageId) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("UserAdd");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
accessPackageAssignment.setTargetId("007d1c7e-7fa8-4e33-b678-5e437acdcddc");
accessPackageAssignment.setAssignmentPolicyId("db440482-1210-4a60-9b55-3ac7a72f63ba");
accessPackageAssignment.setAccessPackageId("88203d16-0e31-41d4-87b2-dd402f1435e9");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
  requestType: 'UserAdd',
  accessPackageAssignment: {
     targetId: '007d1c7e-7fa8-4e33-b678-5e437acdcddc',
     assignmentPolicyId: 'db440482-1210-4a60-9b55-3ac7a72f63ba',
     accessPackageId: '88203d16-0e31-41d4-87b2-dd402f1435e9'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('UserAdd');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignment->setTargetId('007d1c7e-7fa8-4e33-b678-5e437acdcddc');
$accessPackageAssignment->setAssignmentPolicyId('db440482-1210-4a60-9b55-3ac7a72f63ba');
$accessPackageAssignment->setAccessPackageId('88203d16-0e31-41d4-87b2-dd402f1435e9');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "UserAdd"
	accessPackageAssignment = @{
		targetId = "007d1c7e-7fa8-4e33-b678-5e437acdcddc"
		assignmentPolicyId = "db440482-1210-4a60-9b55-3ac7a72f63ba"
		accessPackageId = "88203d16-0e31-41d4-87b2-dd402f1435e9"
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "UserAdd",
	access_package_assignment = AccessPackageAssignment(
		target_id = "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
		assignment_policy_id = "db440482-1210-4a60-9b55-3ac7a72f63ba",
		access_package_id = "88203d16-0e31-41d4-87b2-dd402f1435e9",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignmentRequests/$entity",
    "createdDateTime": null,
    "completedDate": null,
    "id": "a6bb6942-3ae1-4259-9908-0133aaee9377",
    "requestType": "UserAdd",
    "requestState": "Submitted",
    "requestStatus": "Accepted",
    "isValidationOnly": false,
    "expirationDateTime": null,
    "justification": null
}
```

Sign out and close the anonymous session.

## Step 3: Validate that access is assigned

In this step, confirm that the **Requestor1** user account is assigned the access package and is a member of the **Marketing resources** group. Return to the administrator session in Graph Explorer.

### Step 3.1: Get the status of the request

Use the value of the **id** property of the request to get its current status. In the response, you see the status changed to **Fulfilled** and the state changed to **Delivered**.

#### Request

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests/a6bb6942-3ae1-4259-9908-0133aaee9377
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests["{accessPackageAssignmentRequest-id}"].GetAsync();
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
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().ByAccessPackageAssignmentRequestId("accessPackageAssignmentRequest-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().byAccessPackageAssignmentRequestId("{accessPackageAssignmentRequest-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let accessPackageAssignmentRequest = await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests/a6bb6942-3ae1-4259-9908-0133aaee9377')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->byAccessPackageAssignmentRequestId('accessPackageAssignmentRequest-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaEntitlementManagementAccessPackageAssignmentRequest -AccessPackageAssignmentRequestId $accessPackageAssignmentRequestId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.by_access_package_assignment_request_id('accessPackageAssignmentRequest-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignmentRequests/$entity",
  "createdDateTime": "2020-06-29T20:24:24.683Z",
  "completedDate": "2020-06-29T20:24:47.937Z",
  "id": "a6bb6942-3ae1-4259-9908-0133aaee9377",
  "requestType": "UserAdd",
  "requestState": "Delivered",
  "requestStatus": "FulfilledNotificationTriggered",
  "isValidationOnly": false,
  "expirationDateTime": null,
  "justification": null
}
```

### Step 3.2: Get access package assignments

Use the **id** of the access package policy you created to see that resources are assigned to the **Requestor1** user account.

#### Request

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignments?$filter=accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'&$expand=target,accessPackageAssignmentResourceRoles
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'";
	requestConfiguration.QueryParameters.Expand = new string []{ "target","accessPackageAssignmentResourceRoles" };
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-beta-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'"

requestParameters := &graphidentitygovernance.EntitlementManagementAccessPackageAssignmentsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Expand: [] string {"target","accessPackageAssignmentResourceRoles"},
}
configuration := &graphidentitygovernance.EntitlementManagementAccessPackageAssignmentsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignments, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignments().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentCollectionResponse result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'";
	requestConfiguration.queryParameters.expand = new String []{"target", "accessPackageAssignmentResourceRoles"};
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let accessPackageAssignments = await client.api('/identityGovernance/entitlementManagement/accessPackageAssignments')
	.version('beta')
	.filter('accessPackageAssignmentPolicy/Id eq \'db440482-1210-4a60-9b55-3ac7a72f63ba\'')
	.expand('target,accessPackageAssignmentResourceRoles')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\IdentityGovernance\EntitlementManagement\AccessPackageAssignments\AccessPackageAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new AccessPackageAssignmentsRequestBuilderGetRequestConfiguration();
$queryParameters = AccessPackageAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'";
$queryParameters->expand = ["target","accessPackageAssignmentResourceRoles"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignments()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Get-MgBetaEntitlementManagementAccessPackageAssignment -Filter "accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'" -ExpandProperty "target,accessPackageAssignmentResourceRoles" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identity_governance.entitlement_management.access_package_assignments.access_package_assignments_request_builder import AccessPackageAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = AccessPackageAssignmentsRequestBuilder.AccessPackageAssignmentsRequestBuilderGetQueryParameters(
		filter = "accessPackageAssignmentPolicy/Id eq 'db440482-1210-4a60-9b55-3ac7a72f63ba'",
		expand = ["target","accessPackageAssignmentResourceRoles"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignments.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignments",
  "value": [
    {
      "id": "a6bb6942-3ae1-4259-9908-0133aaee9377",
      "catalogId": "cec5d6ab-c75d-47c0-9c1c-92e89f66e384",
      "accessPackageId": "88203d16-0e31-41d4-87b2-dd402f1435e9",
      "assignmentPolicyId": "db440482-1210-4a60-9b55-3ac7a72f63ba",
      "targetId": "2bc42425-6dc5-4f2a-9ebb-7a7464481eb0",
      "assignmentStatus": "Delivered",
      "assignmentState": "Delivered",
      "isExtended": false,
      "expiredDateTime": null,
      "target": {
         "id": "8586ddc8-0ff7-4c24-9c79-f192bc3566e3",
         "objectId": "2bc42425-6dc5-4f2a-9ebb-7a7464481eb0"
      },
      "accessPackageAssignmentResourceRoles": [
         {
            "id": "bdb7e0a0-a927-42ab-bf30-c5b5533dc54a",
            "originSystem": "AadGroup",
            "status": "Fulfilled"
         }
      ]
    }
  ]
}
```

### Step 3.3: Get the members of the group

After the request is granted, use the **id** you recorded for the **Marketing resources** group to see that the **Requestor1** user account is added to it.

#### Request

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```msgraph
GET https://graph.microsoft.com/v1.0/groups/f4892fac-e81c-4712-bdf2-a4450008a4b0/members
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Members.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
members, err := graphClient.Groups().ByGroupId("group-id").Members().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DirectoryObjectCollectionResponse result = graphClient.groups().byGroupId("{group-id}").members().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let members = await client.api('/groups/f4892fac-e81c-4712-bdf2-a4450008a4b0/members')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->groups()->byGroupId('group-id')->members()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroupMember -GroupId $groupId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.groups.by_group_id('group-id').members.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response:

```http
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directoryObjects",
  "value": [
    {
      "@odata.type": "#microsoft.graph.user",
      "id": "007d1c7e-7fa8-4e33-b678-5e437acdcddc",
      "deletedDateTime": null,
      "accountEnabled": true,
      "ageGroup": null,
      "businessPhones": [],
      "city": null,
      "createdDateTime": "2020-06-23T18:43:24Z",
      "creationType": null,
      "companyName": null,
      "consentProvidedForMinor": null,
      "country": null,
      "department": null,
      "displayName": "Requestor1",
      "employeeId": null,
      "faxNumber": null,
      "givenName": null,
      "imAddresses": [],
      "infoCatalogs": [],
      "isResourceAccount": null,
      "jobTitle": null,
      "legalAgeGroupClassification": null,
      "mail": null,
      "mailNickname": "Requestor1"
    }
  ]
}
```

## Step 4: Clean up resources

### Remove an access package assignment

You must remove any assignments to the access package before you can delete it. Use the **id** of the assignment request that you previously recorded to delete it.

Remove any assignments to the access package before deleting it. Use the **id** of the assignment request that you previously recorded to delete it.

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentRequests
Content-type: application/json

{
  "requestType": "AdminRemove",
  "accessPackageAssignment":{
     "id": "a6bb6942-3ae1-4259-9908-0133aaee9377"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageAssignmentRequest
{
	RequestType = "AdminRemove",
	AccessPackageAssignment = new AccessPackageAssignment
	{
		Id = "a6bb6942-3ae1-4259-9908-0133aaee9377",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageAssignmentRequest()
requestType := "AdminRemove"
requestBody.SetRequestType(&requestType) 
accessPackageAssignment := graphmodels.NewAccessPackageAssignment()
id := "a6bb6942-3ae1-4259-9908-0133aaee9377"
accessPackageAssignment.SetId(&id) 
requestBody.SetAccessPackageAssignment(accessPackageAssignment)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageAssignmentRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentRequests().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequest accessPackageAssignmentRequest = new AccessPackageAssignmentRequest();
accessPackageAssignmentRequest.setRequestType("AdminRemove");
AccessPackageAssignment accessPackageAssignment = new AccessPackageAssignment();
accessPackageAssignment.setId("a6bb6942-3ae1-4259-9908-0133aaee9377");
accessPackageAssignmentRequest.setAccessPackageAssignment(accessPackageAssignment);
AccessPackageAssignmentRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentRequests().post(accessPackageAssignmentRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageAssignmentRequest = {
  requestType: 'AdminRemove',
  accessPackageAssignment: {
     id: 'a6bb6942-3ae1-4259-9908-0133aaee9377'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentRequests')
	.version('beta')
	.post(accessPackageAssignmentRequest);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignmentRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequest();
$requestBody->setRequestType('AdminRemove');
$accessPackageAssignment = new AccessPackageAssignment();
$accessPackageAssignment->setId('a6bb6942-3ae1-4259-9908-0133aaee9377');
$requestBody->setAccessPackageAssignment($accessPackageAssignment);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentRequests()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	requestType = "AdminRemove"
	accessPackageAssignment = @{
		id = "a6bb6942-3ae1-4259-9908-0133aaee9377"
	}
}

New-MgBetaEntitlementManagementAccessPackageAssignmentRequest -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_assignment_request import AccessPackageAssignmentRequest
from msgraph_beta.generated.models.access_package_assignment import AccessPackageAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequest(
	request_type = "AdminRemove",
	access_package_assignment = AccessPackageAssignment(
		id = "a6bb6942-3ae1-4259-9908-0133aaee9377",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_assignment_requests.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageAssignmentRequests/$entity",
    "createdDateTime": null,
    "completedDate": null,
    "id": "78eaee8c-e6cf-48c9-8f99-aae44c35e379",
    "requestType": "AdminRemove",
    "requestState": "Submitted",
    "requestStatus": "Accepted",
    "isValidationOnly": false,
    "expirationDateTime": null,
    "justification": null
}
```

### Delete the access package assignment policy

Use the **id** of the assignment policy that you previously recorded to delete it. Make sure all assignments are removed first. The request returns a `204 No Content` response code.

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```http
DELETE https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/6c1f65ec-8c25-4a45-83c2-a1de2a6d0e9f
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageAssignmentPolicies["{accessPackageAssignmentPolicy-id}"].DeleteAsync();
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
graphClient.IdentityGovernance().EntitlementManagement().AccessPackageAssignmentPolicies().ByAccessPackageAssignmentPolicyId("accessPackageAssignmentPolicy-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identityGovernance().entitlementManagement().accessPackageAssignmentPolicies().byAccessPackageAssignmentPolicyId("{accessPackageAssignmentPolicy-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identityGovernance/entitlementManagement/accessPackageAssignmentPolicies/6c1f65ec-8c25-4a45-83c2-a1de2a6d0e9f')
	.version('beta')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageAssignmentPolicies()->byAccessPackageAssignmentPolicyId('accessPackageAssignmentPolicy-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Remove-MgBetaEntitlementManagementAccessPackageAssignmentPolicy -AccessPackageAssignmentPolicyId $accessPackageAssignmentPolicyId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity_governance.entitlement_management.access_package_assignment_policies.by_access_package_assignment_policy_id('accessPackageAssignmentPolicy-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Delete the access package

Use the **id** of the access package that you previously recorded to delete it. The request returns a `204 No Content` response code.

#### Request

- [HTTP](#tabpanel_13_http)
- [C#](#tabpanel_13_csharp)
- [Go](#tabpanel_13_go)
- [Java](#tabpanel_13_java)
- [JavaScript](#tabpanel_13_javascript)
- [PHP](#tabpanel_13_php)
- [PowerShell](#tabpanel_13_powershell)
- [Python](#tabpanel_13_python)

```http
DELETE https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/cf54c6ca-d717-49bc-babe-d140d035dfdd
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].DeleteAsync();
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
graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identityGovernance/entitlementManagement/accessPackages/cf54c6ca-d717-49bc-babe-d140d035dfdd')
	.version('beta')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

Remove-MgBetaEntitlementManagementAccessPackage -AccessPackageId $accessPackageId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Conclusion

In this tutorial, a marketing campaign resource is defined as membership in a single group that can access other resources. It can also be a collection of groups, applications, or SharePoint Online sites.

## Related content

- [Working with the Microsoft Entra entitlement management APIs](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview)
