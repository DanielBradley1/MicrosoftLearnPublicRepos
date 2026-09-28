<!-- Source: https://learn.microsoft.com/en-us/graph/api/appconsentrequest-filterbycurrentuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-02 -->

# appConsentRequest: filterByCurrentUser

Namespace: microsoft.graph

Retrieve a collection of [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) objects for which the current user is the reviewer and the status of the userConsentRequest for accessing the specified app is `InProgress`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ConsentRequest.Read.All | ConsentRequest.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ConsentRequest.Read.All | ConsentRequest.ReadWrite.All |

## HTTP request

```http
GET /identityGovernance/appConsent/appConsentRequests/filterByCurrentUser(on='parameterValue')
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| on | consentRequestFilterByCurrentUserOptions | Filter to query appConsentRequest objects for which the current user is a reviewer. Allowed value is `reviewer`. Required. |

## Query parameters

This function *requires* the `$filter` \(`eq`\) OData query parameter to return a collection of [userConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/userconsentrequest?view=graph-rest-1.0) objects for which the status is `InProgress`. The function also supports the `$select` query parameter. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) objects in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/appConsent/appConsentRequests/filterByCurrentUser(on='reviewer')?$filter=userConsentRequests/any(u:u/status eq 'InProgress')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AppConsent.AppConsentRequests.FilterByCurrentUserWithOn("reviewer").GetAsFilterByCurrentUserWithOnGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "userConsentRequests/any(u:u/status eq 'InProgress')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)


requestFilter := "userConsentRequests/any(u:u/status eq 'InProgress')"

requestParameters := &graphidentitygovernance.AppConsentAppConsentRequestsFilterByCurrentUserWithOnRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.AppConsentAppConsentRequestsFilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
on := "reviewer"
filterByCurrentUser, err := graphClient.IdentityGovernance().AppConsent().AppConsentRequests().FilterByCurrentUserWithOn(&on).GetAsFilterByCurrentUserWithOnGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identityGovernance().appConsent().appConsentRequests().filterByCurrentUserWithOn("reviewer").get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "userConsentRequests/any(u:u/status eq 'InProgress')";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let filterByCurrentUser = await client.api('/identityGovernance/appConsent/appConsentRequests/filterByCurrentUser(on='reviewer')')
	.filter('userConsentRequests/any(u:u/status eq \'InProgress\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\AppConsent\AppConsentRequests\FilterByCurrentUser(on='{on}')\FilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new FilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration();
$queryParameters = FilterByCurrentUserWithOnRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "userConsentRequests/any(u:u/status eq 'InProgress')";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->appConsent()->appConsentRequests()->filterByCurrentUserWithOn('reviewer', )->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Invoke-MgFilterIdentityGovernanceAppConsentRequestByCurrentUser -Filter "userConsentRequests/any(u:u/status eq 'InProgress')"  -On $onId 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.app_consent.app_consent_requests.filter_by_current_user(on='{on}').filter_by_current_user_with_on_request_builder import FilterByCurrentUserWithOnRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = FilterByCurrentUserWithOnRequestBuilder.FilterByCurrentUserWithOnRequestBuilderGetQueryParameters(
		filter = "userConsentRequests/any(u:u/status eq 'InProgress')",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.app_consent.app_consent_requests.filter_by_current_user_with_on("reviewer").get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(appConsentRequest)",
    "@odata.count": 1,
    "value": [
        {
            "@odata.type": "#microsoft.graph.appConsentRequest",
            "id": "7322e5f3-0f15-4eb8-9e82-2029e8622f5d",
            "appId": "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
            "appDisplayName": "Graph Explorer",
            "pendingScopes": [
                {
                    "displayName": "AccessReview.Read.All"
                },
                {
                    "displayName": "openid"
                },
                {
                    "displayName": "profile"
                },
                {
                    "displayName": "offline_access"
                }
            ],
            "userConsentRequests": []
        }
    ]
}
```
