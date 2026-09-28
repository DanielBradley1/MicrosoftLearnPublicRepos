<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringrule-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# List filteringRules

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) objects and their properties. The following derived types are supported:

- [fqdnFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-fqdnfilteringrule?view=graph-rest-beta)
- [webCategoryFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoryfilteringrule?view=graph-rest-beta)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccessPolicy.Read.All | NetworkAccessPolicy.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkaccess/filteringPolicies/{filteringPolicyId}?$expand=policyRules
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.networkaccess.filteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringrule?view=graph-rest-beta) objects in the response body. The **@odata.type** property in the response object indicates the type of the **filteringRule** object.

## Examples

### Request

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
GET https://graph.microsoft.com/beta/networkaccess/filteringPolicies/d0187e08-04cc-41b4-9a47-dd640e804280?$expand=policyRules
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.FilteringPolicies["{filteringPolicy-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "policyRules" };
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/networkaccess"
	  //other-imports
)

requestParameters := &graphnetworkaccess.FilteringPoliciesItemRequestBuilderGetQueryParameters{
	Expand: [] string {"policyRules"},
}
configuration := &graphnetworkaccess.FilteringPoliciesItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
filteringPolicies, err := graphClient.NetworkAccess().FilteringPolicies().ByFilteringPolicyId("filteringPolicy-id").Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.networkaccess.FilteringPolicy result = graphClient.networkAccess().filteringPolicies().byFilteringPolicyId("{filteringPolicy-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"policyRules"};
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let filteringPolicy = await client.api('/networkaccess/filteringPolicies/d0187e08-04cc-41b4-9a47-dd640e804280')
	.version('beta')
	.expand('policyRules')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\NetworkAccess\FilteringPolicies\Item\FilteringPolicyItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new FilteringPolicyItemRequestBuilderGetRequestConfiguration();
$queryParameters = FilteringPolicyItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["policyRules"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->networkAccess()->filteringPolicies()->byFilteringPolicyId('filteringPolicy-id')->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

Get-MgBetaNetworkAccessFilteringPolicy -FilteringPolicyId $filteringPolicyId -ExpandProperty "policyRules" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.network_access.filtering_policies.item.filtering_policy_item_request_builder import FilteringPolicyItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = FilteringPolicyItemRequestBuilder.FilteringPolicyItemRequestBuilderGetQueryParameters(
		expand = ["policyRules"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.network_access.filtering_policies.by_filtering_policy_id('filteringPolicy-id').get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": [
        {
            "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/filteringPolicies(policyRules())/$entity",
            "id": "d0187e08-04cc-41b4-9a47-dd640e804280",
            "name": "Block Social",
            "description": "Block Social",
            "version": "1.0.0",
            "lastModifiedDateTime": "2023-10-29T11:33:55Z",
            "createdDateTime": "2023-10-29T11:33:55Z",
            "action": "block",
            "policyRules@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/filteringPolicies('d0187e08-04cc-41b4-9a47-dd640e804280')/policyRules",
            "policyRules": [
                {
                    "@odata.type": "#microsoft.graph.networkaccess.webCategoryFilteringRule",
                    "id": "36ce876d-16aa-4059-83db-9deab5adeb68",
                    "name": "Block Social",
                    "ruleType": "webCategory",
                    "destinations": [
                        {
                            "@odata.type": "#microsoft.graph.networkaccess.webCategory",
                            "name": "SocialNetworking",
                            "displayName": "Social Networks in General + Facebook + Facebook: Posting + Facebook: Commenting + Facebook: Friends + Facebook: Photo Upload + Facebook: Events + Facebook: Apps + Facebook: Chat + Facebook: Questions + Facebook: Video Upload + Facebook: Groups + Facebook: Games + Twitter + Twitter: Posting + Twitter: Mail + Twitter: Follow + Youtube + Youtube: Commenting + Youtube: Video Upload + Youtube: Sharing + Instagram + Instagram: Upload + Instagram: Commenting + Instagram: Private Message + Tumblr + Tumblr: Posting + Tumblr: Commenting + Tumblr: Photo or Video Upload + Google+ + Google+: Posting + Google+: Commenting + Google+: Photo Upload + Google+: Video Upload + Google+: Video Chat + Pinterest + Pinterest: Pin + Pinterest: Commenting + Ask.fm + Ask.fm: Ask + Ask.fm: Answer + Wordpress + Wordpress: Posting + Wordpress: Upload + TikTok",
                            "group": "Productivity"
                        }
                    ]
                }
            ]
        }
    ]
}
```
